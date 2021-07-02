<h1 align="center">Digital Green Certificate High-Level Description</h1>

<div align="center">
<img width="256" height="256" src="img/logo-dcg.png">
</div>

<br />
<div align="center">
    <!-- CoC -->
    <a href="CODE_OF_CONDUCT.md">
      <img src="https://img.shields.io/badge/Contributor%20Covenant-v2.0%20adopted-ff69b4.svg" />
    </a>
    <a href="CODE_OF_CONDUCT.md">
      <img src="https://img.shields.io/badge/badge-green.svg" />
    </a>
    <a href="/">
      <img alt="java11"
      src="https://img.shields.io/badge/badge-red.svg">
    </a>
    <a href="/">
      <img alt="security: bandit"
      src="https://img.shields.io/badge/badge-yellow.svg">
    </a>
</div>


# Table of contents

- [Introduction](#introduction)
- [Vision and goals](#vision-and-goals)
- [Principles](#principles)
- [Product](#product)
  - [How it works](#product--how-it-works)
  - [DCC generation process](#product--dcc-generation-process)
  - [DCC use case](#product--dcc-use-case)


# Introduction
On the 14th of June 2021 the presidents of the European Commission, European Parliament and European Council approved the EU Digital Covid Certificate (EU DCC), to be used starting from the 1st of July, 2021. Such a certificate is conceived as a flexible tool to facilitate the free movement between Member States. This system involves a constant reassessment of the level of risk by evaluating the immunization effects resulting from the vaccination campaign and citizens that recovered from Covid-19, as well as the results of the widespread Covid-19 testing (molecular and / or antigen).

The following documentation refers to the national solution for the generation, distribution and verification of certificates in compliance with the provisions of the European regulation and the subsequent activation of the interoperability framework with the other Member States.


# Vision and goals
For the implementation of the aforementioned European Regulations, the Ministry of Health, in agreement with the Italian Regions and Autonomous Provinces, with the support of the Ministry for Technological Innovation and Digital Transition and the Ministry of Economy and Finance (MEF), created the National Platform (PN-DGC) for the issue, the distribution and the validation of the EU DCC. Moreover, the platform will guarantee the expected European interoperability.


# Principles
The National Platform (PN-DGC) is represented by a novel standalone system owned by the Ministry of Health and managed by Sogei SPA on behalf of the MEF.
There can be three different types of DCC generated from different data sources. As such,
the PN-DGC database is fed by data collected from the following databases:
* the National Vaccine Registry (ANV, Anagrafe Nazionale Vaccini), managed by the Ministry of Health. Data are transferred to the Tessera Sanitaria System (DL 41/2021 -support Decree- art. 20 paragraph 12);
* data of molecular and antigenic Covid-19 swabs, partly already transmitted to the TS System in relation to previous regulations related to the pandemic and partly transmitted thanks to new regulatory intervention.

The collection of certificates for Covid-19 recovery will be a new feature that can be easily derived from similar features already offered to physicians by the TS System.

Distribution of the DCC to citizens will be carried out through a multi-channel approach. The PN-DGC will generate the DCC that will be inserted in the patient's Fascicolo Sanitario Elettronico (FSE, the online health inbox for official documentation), and will also be accessible through a novel web front-end accessible through the [main website](https://www.dgc.gov.it). Furthermore, the DCC can also be downloaded through the Immuni App as well as through the Tessera Sanitaria portal.

For the verification of the DCC a specific Verifier mobile App (named VerificaC19, [Android](https://github.com/ministero-salute/it-dgc-verificaC19-android), [iOS](https://github.com/ministero-salute/it-dgc-verificaC19-ios)) has been developed. Such an application allows the Verifier to scan the QR code on the DCC, extract the relevant data and verify it subsequently. In case of a positive outcome, the App will show a few details of the DCC, such as the name, surname and the date of birth, of the citizen so that the Verifier can check the correspondence with the citizen’s ID.

Art.9 of the DL 52/2021 (Decree reopening) introduced the "COVID-19 green certifications" valid at national level for the mobility among Italian regions at high risk of infection effectively anticipating the introduction of the European DCC. Such a National certificate uses the current paper certifications already produced by the territorial health facilities following vaccination, recovery, molecular or antigen Covid-19 test.

The PN-DCC national platform can therefore be activated at a National level, even before the official entry of the relevant European regulation, in order to generate Covid-19 green certifications in digital format, with a QR Code and with a unique national identifier. The certification will be checked through the planned verification App that can ensure the validity, authenticity and assure the protection of personal data contained in the certification itself.


# Product
The key features of the Digital Green Certificate (DCC) are:
1. There are three different types of certificates, namely:
certificate of vaccination;
certificate of testing (NAAT / RT-PCR test or rapid antigen test)
certificate of recovery from COVID-19. 
The goal is to grant the right to free movement both to subjects immunized naturally or through vaccination, but also to non-immune subjects who could not or would not be vaccinated.
2. The Certificate must be accessible and secure for all EU citizens. Certificates must be issued in digital or paper format. Both should have a QR code that contains the necessary key information and a digital signature in order to assure the authenticity of the certificate.
The European Commission set up a gateway and supported each Member State in the development of mobile applications useful for verifying the Certificates.
The Certificate will be made available free of charge, also on request, and in the official language(s) of the issuing Member State and in English.
3. The Certificate contains only the minimum identifying information about the citizen and information essential to verify the validity of the certificate. Certificates include a limited set of information such as name, date of birth, date of issue, relevant vaccine/test/recovery information, and a unique certificate identifier.
This data can only be checked to confirm and verify the authenticity and validity of the certificates also in relation to the rules adopted by each Member State regarding e.g., the duration of the immunizing effect of vaccines or infection or the type of vaccine used. 
4. The Certificate is not an identification document of the citizen. 
5. Finally the Certificate is not discriminatory.

## How it works
Here the [openapi.yaml](./openapi.yaml) file, which describes all services exposed in the backend.

## DCC generation process
The DCC generation process follows the health rules, defined in relation to the different use cases specified by the Ministry of Health, based on what has been agreed at the European level. The generation process of a DCC is summarized in the following figure.

![image](https://user-images.githubusercontent.com/11008116/124256302-6d5fbe80-db2b-11eb-89c0-121079483466.png)

## DCC use case
![Screenshot from 2021-07-02 12-07-22](https://user-images.githubusercontent.com/11008116/124258807-1ad3d180-db2e-11eb-8ec9-d7978bac3798.png)

The image above represents a typical use case of the Digital Green Certificate Gateway (DGCG):
1. During the onboarding phase, the Member State communicates to the DGCG some information regarding the cryptographic material that uniquely distinguishes it and that will be used to sign the DCCs (CSCA, DSC and certificates to guarantee the security of the communication channel).
2. Member State A can then start generating DCCs and sign them digitally.
3. Member State B, in turn, carries out the same operations as A. Furthermore, Member State B downloads the information sent by A to the DGCG within its PN-DGC.
4. On a daily basis, all installations of the Verifier App of Member State B receive information from the other Member States, such as cryptographic material related to Member State A.
5. When a citizen of Member State A decides to visit Member State B, he exposes his DCC together with his ID (passport, identity card or other) to the border staff. At this point the Verifier App operated by the border staff of Member State B reads the QR code, extracts the information and proceeds to the validation phase. Since the Verifier App knows the information relating to the signature certificate used by Member State A (downloaded in point 4) it is therefore able to recognize the validity of the DCC and process the information.
6. In case the information contained in the DCC is correct, valid and belonging to the traveler, the citizen of Member State A will be able to enter Member State B.
