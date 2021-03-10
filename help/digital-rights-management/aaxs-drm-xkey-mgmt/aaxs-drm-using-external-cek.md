---
description: Met de functie External CEK kunt u licenties doorvoeren en verpakken met behulp van uw bestaande CKMS.
title: De externe CEK gebruiken om licenties te zoeken en te verpakken
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---


# Het gebruiken van Externe CEK aan Vend en de Vergunningen van het Pakket{#using-external-cek-to-vend-and-package-licenses}

Met de functie External CEK kunt u licenties doorvoeren en verpakken met behulp van uw bestaande CKMS.

## EncryptContentWithExternalKey.java

Dit is een opdrachtregelprogramma waarmee een video wordt gecodeerd en metagegevens worden gemaakt die *niet* de CEK bevatten (beveiligd met een openbare cert van een AXS-licentieserver). In plaats daarvan sluit het gereedschap een CEK-id in de metagegevens van de video in.

Tijdens het aanschaffen van licenties merkt de AAXS-licentieserver een markering in de metagegevens op die aangeeft dat deze inhoud is beveiligd met een externe CEK. De licentieserver haalt de CEK-id uit de metagegevens en vraagt vervolgens een beveiligde gegevensopslagruimte/CKMS op om de juiste CEK op te halen.

## Verpakkingswerkstroom

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

1. Controleer of er een [!DNL CEKDepot.properties]-bestand naast uw [!DNL flashaccess-refimpl.properties] staat

1. Een licentieaanvraag starten vanuit een Adobe Primetime Player
1. Bekijk de Ref Impl-logboeken voor iets gelijkaardigs:

   ```
   DEBUG [com.adobe.flashaccess.refimpl.web.RefImplLicenseReqHandler.REQUESTS] 
     Used CEK ID:{abc} to retrieve CEK: {abcdef0123456789} from depot
   ```

   1. Mogelijk moet u de [!DNL log4j.xml]-instellingen wijzigen om u aan te melden op een niveau `DEBUG` ( `INFO` is standaard ingesteld)

## Bekende problemen

Geen
