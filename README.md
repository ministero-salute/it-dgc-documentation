<h1 align="center">EU Digital COVID Certificate's High-Level Description</h1>

<div align="center">
<img width="256" height="256" src="img/logo-dcg.png">
</div>

<br />

# Table of contents

- [Introduction](#introduction)
- [Vision and goals](#vision-and-goals)
- [Principles](#principles)
- [Product](#product)
  - [How it works](#product--how-it-works)
- [Privacy](#privacy)


# Introduction
TheEU Digital COVID Certificate (DCC) is introduced by a proposal for a European Regulation of March 17, 2021, whose approval is expected in June 2021, as a flexible tool to facilitate the free movement between Member States, through a constant reassessment of the level of risk of spread of infection in relation essentially to the effects of immunization resulting from vaccination and a proven recovery, as well as the results of a reliable test (molecular and / or antigenic) with respect to the ability to transmit the SARS-CoV-2 virus.

The following documentation refers to the national solution for the generation, distribution and verification of certificates in compliance with the provisions of the European regulation and the subsequent activation of interoperability with other states of the union.

# Vision and goals
For the implementation of the aforementioned proposal for European Regulations, the Ministry of Health, in agreement also with the regions and autonomous provinces, with the support of the Ministry for Technological Innovation and Digital Transition and the Ministry of Economy and Finance, has deemed it appropriate to initiate the creation of a National Platform (PN-DGC) for the issue, distribution and validation of the DGC, which will guarantee the expected European interoperability.

# Principles
This national platform will constitute a new system, created as part of the systems managed by Sogei SPA on behalf of the MEF, of which the Ministry of Health will be the owner, and will be fed by data collected from the National Vaccine Registry (ANV), managed by the Ministry of Health and transferred to the TS System pursuant to DL 41/2021 (support decree) art. 20 paragraph 12, and from the data of molecular and antigenic swabs, partly already transmitted to the TS System in relation to previous regulations related to emergency management and partly to be transmitted according to a new regulatory intervention. The collection of healing certificates will be a new feature that can be easily derived from similar features already offered to physicians by the TS System.
Distribution of the DGC to the citizen is expected to be through a multi-channel approach. The PN-DGC will produce the DGC that will be inserted in the patient's FSE, also, a dedicated web front-end will  be created. The DGC can also be downloaded through government APPs (APP IO and APP IMMUNI) as well as through the Tessera Sanitaria portal.
For the verification of the DGC will be developed a special Verifier App (VerificaC19) to allow the Verifier to read the QR code on the DGC and, in case of positive outcome, the App shows the details of the DGC and the personal data of the citizen so that the Verifier can verify the identity of the citizen with an identification document and verify the correspondence with the personal data shown by the App.

The DL 52/2021 (decree reopening) has provided by art.9 the introduction of the "COVID-19 green certifications" valid at national level for the mobility in regions at high risk of infection anticipating the introduction of the DGC as a principle, but using the current paper certifications already produced by the territorial health facilities following vaccination, recovery, molecular or antigenic Covid-19 test.

The PN-DGC national platform can therefore be used at the national level, even before the entry into effect of the relevant European regulation, to ensure the production of Covid-19 green certifications in digital format, with QR Code and unique national identifier, interoperable and verifiable through the planned verification App that can ensure the validity, authenticity and ensure greater protection of personal data contained in the certification itself.

# Product
The key elements of the Digital Green Certificate (DGC)
1. contain the following information: certificate of vaccination, certificate of testing (NAAT / RT-PCR test or rapid antigen test) or certificate of recovery from COVID-19 as it gives the opportunity to apply the right to free movement both to subjects immunized naturally or through vaccination, but also to non-immune subjects who could not or would not be vaccinated.
2. Be accessible and secure for all EU citizens:
Certificates must be issued in digital or paper format. Both should have a QR code that contains the necessary key information and a digital signature so that we can be sure that the certificate is authentic.
The Commission will set up a gateway and support Member States in developing mobile applications that national authorities can use to verify all certificate signatures in the EU.
Be available free of charge, also on request, and in the official language(s) of the issuing Member State and in English.
3. Contain only the minimum identifying information about the citizen and information essential to verify the validity of the certificate: Certificates will include a limited set of information such as name, date of birth, date of issue, relevant vaccine/test/recovery information, and a unique certificate identifier.
These data can only be checked to confirm and verify the authenticity and validity of the certificates also in relation to the rules adopted by each country regarding e.g. the duration of the immunizing effect of vaccines or contagion or the type of vaccine administered. 
4. It is not an identification document of the citizen 
5. Is not discriminatory: Is not binding for travel between Member States, which must be guaranteed regardless of the possession of the certificate itself
Guarantees in all the countries of the Union the exemption from further restrictive measures to travel such as testing or quarantine.

## How it works
Here the [openapi.yaml](./openapi.yaml) file, which describe all services exposed by backend.

# Privacy
