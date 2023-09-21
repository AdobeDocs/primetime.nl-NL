---
title: Softwarevereisten
description: Softwarevereisten
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---

# Softwarevereisten {#software-requirements}

* Tomcat 6
* JDK 1.8

## Inhoud van levering/pakket voor code{#code-delivery-package-contents}

Het Adobe Primetime DRM On Premises Individualization Server-pakket bevat het volgende:

* [!DNL flashaccess.war] - De Individualization Server
* [!DNL flashaccess-kgs.war] - De optionele Key Generation Server
* [!DNL /shared] - Bevat:

   * [!DNL adobe-flashaccess-certs.jar]
   * [!DNL AdobeInitial.properties] - Voorbeeldeigenschappenbestand

* [!DNL thirdparty/] - Bevat ondersteuning voor Crypto-J als native bibliotheken:

   * [!DNL libjsafe.so] (Linux)
   * [!DNL jsafe.dll] (Windows)

* [!DNL adobe-flashaccess-i15n-setup.jar] - Een hulpprogramma voor het coderen van serverreferenties voor wachtwoorden
* [!DNL ROOT] - bevat een [!DNL crossdomain.xml] file

* ECI-cachebestanden - vooraf gedownload
* [!DNL addIndivCert.py] - Een script voor het bijwerken van de vertrouwensbasis van een licentieserver voor ondersteuning van individualisaties op locatie
* [!DNL CreateMetadata.jar] - Een hulpprogramma voor het maken van DRM-metagegevens op locatie
* [!DNL client_sample/] - Een map met een clientcodefragment
* Opmerkingen bij de release - Voor alle laatste minuten die u aan de documentatie toevoegt

## Individualisatieservercertificaten verkrijgen{#obtain-individualization-server-certificates}

Om de Server van de Individualisering te gebruiken Op locatie, moet u twee digitale geloofsbrieven (certificaten) eerst verkrijgen:

* *Individuele transportreferentie* - afgegeven door Adobe
* *Individuele CA-referentie* - afgegeven door Symantec (VeriSign)

Om deze certificaten te verkrijgen, dient u een aanvraag in via het Zendesk-ticket naar: [https://adobeprimetime.zendesk.com](https://adobeprimetime.zendesk.com)

Deze gegevens komen bovenop de gegevens die vereist zijn voor het gebruik van een Primetime DRM-licentieserver.
