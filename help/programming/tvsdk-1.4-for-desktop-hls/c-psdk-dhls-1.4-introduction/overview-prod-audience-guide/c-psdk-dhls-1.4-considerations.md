---
description: Als u TVSDK het doeltreffendst wilt gebruiken, moet u bepaalde details van de werking van de SDK in overweging nemen en bepaalde best practices volgen.
title: Overwegingen en beste praktijken
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Overwegingen en beste praktijken{#considerations-and-best-practices}

Als u TVSDK het doeltreffendst wilt gebruiken, moet u bepaalde details van de werking van de SDK in overweging nemen en bepaalde best practices volgen.

## Overwegingen {#section_tvsdk_considerations}

Houd rekening met de volgende informatie wanneer u TVSDK gebruikt:

* Adobe Primetime werkt niet op emulators of simulatoren.

  U moet echte apparaten gebruiken voor het testen.
* Afspelen wordt alleen ondersteund voor HLS-inhoud (HTTP Live Streaming).
* Hoofdvideo-inhoud kan worden vermenigvuldigd, waarbij video- en audiostreams zich in dezelfde uitvoering bevinden, of niet-gemultiplext, waarbij video- en audiostreams zich in afzonderlijke uitvoeringen bevinden.
* De TVSDK-API wordt geïmplementeerd in ActionScript.
* Voor het afspelen van video is de Adobe Video Engine (AVE) vereist. Dit beïnvloedt hoe en wanneer de media middelen kunnen worden betreden:

   * Ondertiteling met gesloten ondertiteling wordt gesteund in de mate die door AVE wordt verstrekt.
   * Afhankelijk van de precisie van de codeermodule kan de werkelijk gecodeerde mediaduur afwijken van de tijdsduur die in het manifest van de streambron wordt vastgelegd.

     Er is geen betrouwbare manier om opnieuw te synchroniseren tussen de ideale virtuele tijdlijn en de werkelijke afspeeltijdlijn. Bij het bijhouden van de voortgang van het afspelen van de stream voor advertentiebeheer en Video-analyse moet de werkelijke afspeeltijd worden gebruikt. Het is dus mogelijk dat de media en advertentie-inhoud niet exact worden bijgehouden door de rapportage en het gedrag van de gebruikersinterface.
   * Aan de naam van de binnenkomende gebruikersagent voor alle HTTP-aanvragen van TVSDK op dit platform wordt het volgende tekenreekspatroon toegewezen:

     ```
     "Adobe Flash Player"
     ```

## Aanbevolen procedures {#section_tvsdk_best_practices}

Hier volgen de aanbevolen procedures voor TVSDK:

* Gebruik HLS versie 3.0 of hoger voor programma-inhoud.
* Voor TVSDK 1.4 voor DHLS, wordt het luie en het laden toegelaten door gebrek.

  Voor inhoud zonder pre- of mid-roll kunt u `AdvertisingMetadata.delayAdLoading` om het laden van inhoud nog verder te versnellen.
