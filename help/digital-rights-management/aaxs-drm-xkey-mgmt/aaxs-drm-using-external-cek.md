---
description: Met de functie External CEK kunt u licenties doorvoeren en verpakken met behulp van uw bestaande CKMS.
title: De externe CEK gebruiken om licenties te zoeken en te verpakken
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# De externe CEK gebruiken om licenties te zoeken en te verpakken{#using-external-cek-to-vend-and-package-licenses}

Met de functie External CEK kunt u licenties doorvoeren en verpakken met behulp van uw bestaande CKMS.

## EncryptContentWithExternalKey.java

Dit is een opdrachtregelprogramma waarmee u een video kunt coderen en metagegevens kunt maken die *niet* bevat de CEK (die is beveiligd met een openbare cert van de AXS-licentieserver). In plaats daarvan sluit het gereedschap een CEK-id in de metagegevens van de video in.

Tijdens het aanschaffen van licenties merkt de AAXS-licentieserver een markering in de metagegevens op die aangeeft dat deze inhoud is beveiligd met een externe CEK. De licentieserver haalt de CEK-id uit de metagegevens en vraagt vervolgens een beveiligde gegevensopslagruimte/CKMS op om de juiste CEK op te halen.

## Verpakkingsworkflow

1. Zorg ervoor dat u Java 1.6.0_24 of hoger gebruikt.
1. U kunt als volgt het gereedschapsgebruik zien: `java -jar AdobePackager_ExternalCEK.jar`
1. Inhoud verpakken:

   ```
   java -jar AdobePackager_ExternalCEK.jar sample.flv encrypted.flv abc abcdef0123456789 
       policy.pol https://path-to-your-server:8090 <license-server-public-cert.pem> 
       <license-server-private-key.pfx> <private-key-password>
   ```

>[!NOTE]
>
>* De Java-broncode kan worden gemaakt met de opgenomen ANT `build-samples.xml`
>* De Flash Access-SDK ( `adobe-flashaccess-sdk.jar`) moet zich op het klassepad bevinden
>

## Serverworkflow

1. Stel de referentie-implementatie in.
1. Indien aanwezig, opschort vorige implementaties van Reference Implementation:

   1. `delete <tomcat>\work\Catalina\*.*`
   1. `delete <tomcat>\conf\Catalina\*.*`
   1. `delete <tomcat>\logs\*.*`

1. Controleren of er een [!DNL CEKDepot.properties] naast uw [!DNL flashaccess-refimpl.properties]

1. Een licentieaanvraag starten vanuit een Adobe Primetime Player
1. Bekijk de Ref Impl-logboeken voor iets gelijkaardigs:

   ```
   DEBUG [com.adobe.flashaccess.refimpl.web.RefImplLicenseReqHandler.REQUESTS] 
     Used CEK ID:{abc} to retrieve CEK: {abcdef0123456789} from depot
   ```

   1. Mogelijk moet u uw [!DNL log4j.xml] instellingen voor aanmelden bij een `DEBUG` niveau ( `INFO` is standaard ingesteld)

## Bekende problemen

Geen
