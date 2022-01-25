# Certificati di esenzione

## Indice

- [Scopo del documento](#scopo-del-documento)
- [Struttura nuova classe Exemption](#struttura-nuova-classe-exemption)
- [Estrapolazione dell’esenzione](#estrapolazione-dellesenzione)
- [Controlli in fase di scansione](#controlli-in-fase-di-scansione)
  
## Scopo del documento

Lo scopo del documento è quello di dare una panormica agli sviluppatori di come
funzionano i certificati di esenzione e come vengono attualmente gestiti dal
SDK Android.

## Struttura nuova classe Exemption

La classe `Exemption` all'interno del SDK Android si presenta nel seguente modo:

```kotlin
data class Exemption(

    @SerializedName("tg")
    val disease: String,

    @SerializedName("co")
    val countryOfVaccination: String,

    @SerializedName("is")
    val certificateIssuer: String,

    @SerializedName("ci")
    val certificateIdentifier: String,

    @SerializedName("df")
    val certificateValidFrom: String,

    @SerializedName("du")
    val certificateValidUntil: String?

) : Serializable
```

L’oggetto che arriva dalla libreria Decoder contiene i dati riportati sopra, nello 
specifico noi andremo a lavorare però soltanto con i campi:

  - certificateIdentifier (UCVI)
  - certificateValidFrom (Data inizio validità)
  - certificateValidUntil (Data fine validità)

## Estrapolazione dell’esenzione

Per estrapolare il dato dell’esenzione dalla Decoder però non è stato possibile 
prendere l’esenzione direttamente dall’oggetto GreenCertificate definito nella 
libreria, poiché deserializza il certificato ignorando l’esenzione e avrebbe 
necessitato un update. Perciò andiamo a cercare il Json “Raw” e tentiamo di 
prendere il campo “e” dove presente, che contiene l’eventuale esenzione.

Codice di esempio:

```kotlin
/**
 * This method takes care of retrieving the [Exemption] from the json received
 * by the Decoder library, and then returns it if present, otherwise it returns null.
 */
private fun extractExemption(
    decodeData: GreenCertificateData?
): Array<Exemption>? {
    val jsonObject = JSONObject(decodeData!!.hcertJson)
    val exemptionJson = if (jsonObject.has("e")) jsonObject.getString("e") else null
    exemptionJson?.let {
        Log.i("exemption found", it)
        return Gson().fromJson(exemptionJson, Array<Exemption>::class.java)
    }
    return null
}
```


## Controlli in fase di scansione

Nel caso in cui l’esenzione venisse popolata, andremo a vedere se la 
`dateUntil` è stata superata oppure se `startDate` non è ancora stata raggiunta.

Infine, una volta passati questi controlli il certificato richiederà un tampone se 
in modalità “Booster” altrimenti risulterà valido.

Codice di esempio:

```kotlin
/**
 * This method checks the [Exemption] and returns a proper [CertificateStatus]
 * after checking the validity start and end dates.
 */
private fun checkExemptions(
    it: List<Exemption>,
    scanMode: String
): CertificateStatus {
    try {
        val startDate: LocalDate = LocalDate.parse(clearExtraTime(it.last().certificateValidFrom))
        val endDate: LocalDate? = it.last().certificateValidUntil?.let {
            LocalDate.parse(clearExtraTime(it))
        }
        Log.d("dates", "start:$startDate end: $endDate")

        if (startDate.isAfter(LocalDate.now())) {
            return CertificateStatus.NOT_VALID_YET
        }
        endDate?.let {
            if (LocalDate.now().isAfter(endDate)) {
                return CertificateStatus.NOT_VALID
            }
        }
        return if (scanMode == ScanMode.BOOSTER) {
            CertificateStatus.TEST_NEEDED
        } else CertificateStatus.VALID
    } catch (e: Exception) {
        return CertificateStatus.NOT_EU_DCC
    }
}
```
