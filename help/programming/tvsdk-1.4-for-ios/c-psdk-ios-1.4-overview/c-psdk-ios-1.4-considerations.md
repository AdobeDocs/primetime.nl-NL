---
description: Als u TVSDK het doeltreffendst wilt gebruiken, moet u bepaalde details van de werking van de SDK in overweging nemen en bepaalde best practices volgen.
seo-description: Als u TVSDK het doeltreffendst wilt gebruiken, moet u bepaalde details van de werking van de SDK in overweging nemen en bepaalde best practices volgen.
seo-title: Overwegingen en beste praktijken
title: Overwegingen en beste praktijken
uuid: b37a5710-e811-4c3e-be8c-7c34ee5944e5
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Overwegingen en beste praktijken{#considerations-and-best-practices}

Als u TVSDK het doeltreffendst wilt gebruiken, moet u bepaalde details van de werking van de SDK in overweging nemen en bepaalde best practices volgen.

## Overwegingen {#section_tvsdk_considerations}

Houd rekening met de volgende informatie wanneer u TVSDK gebruikt:

* Adobe Primetime werkt niet op iOS-simulators.

   U moet echte apparaten gebruiken voor het testen.
* Afspelen wordt alleen ondersteund voor HLS-inhoud (HTTP Live Streaming).
* Hoofdvideo-inhoud kan worden vermenigvuldigd, waarbij video- en audiostreams zich in dezelfde uitvoering bevinden, of niet-gemultiplext, waarbij video- en audiostreams zich in afzonderlijke uitvoeringen bevinden.
* De TVSDK-API wordt geïmplementeerd in doelstelling C.
* Voor het afspelen van video&#39;s is het native Apple AV Foundation-framework vereist. Dit beïnvloedt hoe en wanneer de media middelen, met inbegrip van gesloten titels en chronologie, kunnen worden betreden:

   * Aanpassingen aan de tijdlijn kunnen niet worden herzien na de eerste setup.

      Een advertentie kan bijvoorbeeld niet uit de tijdlijn worden verwijderd nadat deze is afgespeeld. Als de gebruiker terug in de presentatie zoekt, wordt dezelfde advertentie opnieuw afgespeeld, zelfs als het beleid zou zijn geweest om de advertentie te verwijderen.
   * Afhankelijk van de precisie van de codeermodule kan de werkelijk gecodeerde mediaduur afwijken van de tijdsduur die in het manifest van de streambron wordt vastgelegd.

      Er is geen betrouwbare manier om opnieuw te synchroniseren tussen de ideale virtuele tijdlijn en de werkelijke afspeeltijdlijn. Bij het bijhouden van de voortgang van het afspelen van de stream voor advertentiebeheer en Video-analyse moet de werkelijke afspeeltijd worden gebruikt. Het is dus mogelijk dat de media en advertentie-inhoud niet exact worden bijgehouden door de rapportage en het gedrag van de gebruikersinterface.
   * De inkomende gebruikersagent voor alle HTTP-aanvragen van TVSDK op dit platform wordt bepaald door het apparaat en de iOS-versie die op het apparaat wordt uitgevoerd.

      De waarde van de userAgent-tekenreeks staat standaard voor wat het besturingssysteem toewijst.

## Aanbevolen procedures {#section_tvsdk_best_practices}

Hier volgen de aanbevolen procedures voor TVSDK:

* Gebruik HLS versie 3.0 of hoger voor programma-inhoud.
* Gebruik het hulpprogramma MediaStreamValidator van Apple om VOD-streams te valideren.
* De `PTSDKConfig` klasse biedt methoden om SSL af te dwingen voor aanvragen die zijn gedaan naar Primetime en beslissings-, DRM- en Video Analytics-servers.

   Zie de methoden `forceHTTPS` `isForcingHTTPS` en methoden in deze klasse voor meer informatie.

   >[!IMPORTANT]
   >
   >Aanvragen voor domeinen van derden, zoals het bijhouden van pixels, URL&#39;s voor inhoud en advertentie, en vergelijkbare aanvragen worden niet gewijzigd. Het is de verantwoordelijkheid van de inhoudsproviders en -servers om URL&#39;s te leveren die via HTTPS worden ondersteund.

