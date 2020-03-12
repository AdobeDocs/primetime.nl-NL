---
description: Als u TVSDK het doeltreffendst wilt gebruiken, moet u bepaalde details van de werking van de SDK in overweging nemen en bepaalde best practices volgen.
seo-description: Als u TVSDK het doeltreffendst wilt gebruiken, moet u bepaalde details van de werking van de SDK in overweging nemen en bepaalde best practices volgen.
seo-title: Overwegingen en beste praktijken
title: Overwegingen en beste praktijken
uuid: 62a5d641-6f37-4e4d-bbc2-414bf3681d9c
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Overwegingen en beste praktijken{#considerations-and-best-practices}

Als u TVSDK het doeltreffendst wilt gebruiken, moet u bepaalde details van de werking van de SDK in overweging nemen en bepaalde best practices volgen.

## Overwegingen {#section_tvsdk_considerations}

Houd rekening met de volgende informatie wanneer u TVSDK gebruikt:

* Adobe Primetime werkt niet op emulators of simulators.

   U moet echte apparaten gebruiken voor het testen.
* Afspelen wordt alleen ondersteund voor HLS-inhoud (HTTP Live Streaming).
* Hoofdvideo-inhoud kan worden vermenigvuldigd, waarbij video- en audiostreams zich in dezelfde uitvoering bevinden, of niet-gemultiplext, waarbij video- en audiostreams zich in afzonderlijke uitvoeringen bevinden.
* De TVSDK-API wordt geïmplementeerd in ActionScript.
* Voor het afspelen van video&#39;s is de Adobe Video Engine (AVE) vereist. Dit beïnvloedt hoe en wanneer de media middelen kunnen worden betreden:

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

   Voor inhoud zonder pre-rol of middenrol, kunt u gebruiken `AdvertisingMetadata.delayAdLoading` om inhoud te versnellen ladend nog meer.

