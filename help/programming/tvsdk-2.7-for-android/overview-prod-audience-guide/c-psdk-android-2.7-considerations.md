---
description: Als u TVSDK het doeltreffendst wilt gebruiken, moet u bepaalde details van de werking van de SDK in overweging nemen en bepaalde best practices volgen.
seo-description: Als u TVSDK het doeltreffendst wilt gebruiken, moet u bepaalde details van de werking van de SDK in overweging nemen en bepaalde best practices volgen.
seo-title: Overwegingen en beste praktijken
title: Overwegingen en beste praktijken
uuid: 049da1f4-028b-49d2-9ebd-e5d9edcbaf8a
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---


# Overwegingen en aanbevolen procedures{#considerations-and-best-practices}

Als u TVSDK het doeltreffendst wilt gebruiken, moet u bepaalde details van de werking van de SDK in overweging nemen en bepaalde best practices volgen.

## Overwegingen {#section_tvsdk_considerations}

Houd rekening met de volgende informatie wanneer u TVSDK gebruikt:

* De TVSDK-API is geïmplementeerd in Java.
* Adobe Primetime werkt momenteel niet op Android-emulators.

   U moet echte apparaten gebruiken voor het testen.
* Afspelen wordt alleen ondersteund voor HLS-inhoud (HTTP Live Streaming).
* De hoofdvideo-inhoud kan worden vermenigvuldigd (video- en audiostreams in dezelfde uitvoering) of niet-gemultiplext (video- en audiostreams in afzonderlijke uitvoeringen).
* Momenteel moet u de meeste API-bewerkingen voor TVSDK uitvoeren op de gebruikersinterfacethread. Dit is de belangrijkste Android-thread.

   De verrichtingen die correct op de belangrijkste draad lopen kunnen een fout en uitgang werpen wanneer looppas op een achtergronddraad.
* Voor het afspelen van video is de Adobe Video Engine (AVE) vereist. Dit beïnvloedt hoe en wanneer de media middelen kunnen worden betreden:

   * Ondertiteling met gesloten ondertiteling wordt gesteund in de mate die door AVE wordt verstrekt.
   * Afhankelijk van de precisie van de codeermodule kan de werkelijk gecodeerde mediaduur afwijken van de tijdsduur die in het manifest van de streambron wordt vastgelegd.

      Er is geen betrouwbare manier om opnieuw te synchroniseren tussen de ideale virtuele tijdlijn en de werkelijke afspeeltijdlijn. Bij het bijhouden van de voortgang van het afspelen van de stream voor advertentiebeheer en Video-analyse moet de werkelijke afspeeltijd worden gebruikt. Het is dus mogelijk dat de media en advertentie-inhoud niet exact worden bijgehouden door de rapportage en het gedrag van de gebruikersinterface.
   * Aan de naam van de inkomende gebruikersagent voor alle mediaverzoeken van de TVSDK op dit platform wordt het volgende tekenreekspatroon toegewezen:

   ```
   "Adobe Primetime/" + 
   <varname>
   originalUserAgent
   </varname> 
   ```

   Voor alle aan advertenties gerelateerde aanroepen wordt de standaardgebruikersagent van Android of de aangepaste gebruikersagent gebruikt als u deze instelt tijdens het instellen van metagegevens voor invoegtoepassingen.

## Aanbevolen werkwijzen {#section_tvsdk_best_practices}

Hier volgen de aanbevolen procedures voor TVSDK:

* Gebruik HLS versie 3.0 of hoger voor programma-inhoud.
* Voer de meeste bewerkingen van TVSDK uit op de hoofd-thread (UI), niet op de achtergrondthreads.
* Voor TVSDK 2.5 voor Android is het standaard lazy en resolving ingeschakeld.

   Voor inhoud zonder pre-rol of middenrol, kunt u `AdvertisingMetadata.setPreroll(false)` gebruiken om inhoud te versnellen ladend.
