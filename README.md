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


# Introduction
On 17 March 2021, the European Commission issued a proposal for a Regulation on a 'Digital Covid Certificate' (DCC) to be in use from 1 July 2021, The certificate is conceived as a flexible tool to facilitate the free movement between Member States, through a constant reassessment of the level of risk of infection by evaluating the effects of immunization resulting from vaccination, proven recovery, as well as the results of reliable testing (molecular and / or antigen).

The following documentation refers to the national solution for the generation, distribution and verification of certificates in compliance with the provisions of the European regulation and the subsequent activation of interoperability with other Member States.

# Vision and goals
For the implementation of the aforementioned proposal for European Regulations, the Ministry of Health, in agreement with the Italian Regions and Autonomous Provinces, with the support of the Ministry for Technological Innovation and Digital Transition and the Ministry of Economy and Finance (MEF), began the creation of a National Platform (PN-DCC) for the issue, distribution and validation of the DCC, which will guarantee the expected European interoperability.

# Principles
This national platform will constitute a new system, managed by Sogei SPA on behalf of the MEF, of which the Ministry of Health will be the owner, and will be fed by data collected from the National Vaccine Registry (ANV), managed by the Ministry of Health and transferred to the TS System (DL 41/2021 -support Decree- art. 20 paragraph 12), and by data of molecular and antigenic swabs, partly already transmitted to the TS System in relation to previous regulations related to the pandemic and partly transmitted thanks to new regulatory intervention. The collection of certificates for Covid-19 recovery will be a new feature that can be easily derived from similar features already offered to physicians by the TS System.
Distribution of the DCC to citizens is expected to be through a multi-channel approach. The PN-DCC will generate the DCC that will be inserted in the patient's FSE, and will also be accessible through a new web front-end that will be created. The DCC can also be downloaded through government APPs (APP IO and APP IMMUNI) as well as through the Tessera Sanitaria portal.
For the verification of the DCC a specific  Verifier App (VerificaC19) will be developed. It will allow the Verifier to read the QR code on the DCC.  In case of a positive outcome, the App shows the details of the DCC and the personal data of the citizen so that the Verifier can verify the identity of the citizen with an identification document and check the correspondence with the personal data shown by the App.

Art.9  of the DL 52/2021 (Decree reopening) introduced  the "COVID-19 green certifications" valid at national level for the mobility among Italian regions at high risk of infection anticipating the introduction of the European DCC The national certificate uses the current paper certifications already produced by the territorial health facilities following vaccination, recovery, molecular or antigen Covid-19 test.

The PN-DCC national platform can therefore be activated at national level, even before the entry into force of the relevant European regulation, to generate  Covid-19 green certifications in digital format, with QR Code and unique national identifier, interoperable and verifiable through the planned verification App that can ensure the validity, authenticity and assure greater protection of personal data contained in the certification itself.

# Product
The key features of the Digital Green Certificate (DCC) are:
1. The Certificate must contain the following information: certificate of vaccination, certificate of testing (NAAT / RT-PCR test or rapid antigen test) or certificate of recovery from COVID-19. The goal is to grant the right of free movement both to subjects immunized naturally or through vaccination, but also to non-immune subjects who could not or would not be vaccinated.
2. The Certificate must be accessible and secure for all EU citizens:
Certificates must be issued in digital or paper format. Both should have a QR code that contains the necessary key information and a digital signature in order to assure the authenticity of the certificate.
The Commission will set up a gateway and support Member States in developing mobile applications that national authorities can use to verify all certificate signatures in the EU.
The Certificate should also be made available free of charge, also on request, and in the official language(s) of the issuing Member State and in English.
3. The Certificate should contain only the minimum identifying information about the citizen and essential information to verify the validity of the certificate. Certificates will include a limited set of information such as name, date of birth, date of issue, relevant vaccine/test/recovery information, and a unique certificate identifier.
This data can only be checked to confirm and verify the authenticity and validity of the certificates also in relation to the rules adopted by each Member State regarding e.g. the duration of the immunizing effect of vaccines or infection or the type of vaccine used. 
4. The Certificate must not be an identification document of the citizen 
5. Finally the Certificate must not be discriminatory. Is not binding for travel between Member States, which must be guaranteed regardless of the possession of the certificate itself.
It should also guarantee in all the countries of the Union that no further restrictive measures to travel such as testing or quarantine are implemented.

## How it works
Here the [openapi.yaml](./openapi.yaml) file, which describes all services exposed by backend.
