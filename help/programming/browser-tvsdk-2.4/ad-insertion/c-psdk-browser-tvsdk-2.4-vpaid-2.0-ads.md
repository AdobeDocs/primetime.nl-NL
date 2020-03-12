---
description: VPAID 2.0 (Video Player ad-serving interface definition) biedt een algemene interface voor het afspelen van videoadvertenties. Het biedt gebruikers een rijke mediabeleving en biedt uitgevers de mogelijkheid om advertenties beter te richten, indrukken bij te houden en te monetiseren, en video-inhoud te monetiseren.
seo-description: VPAID 2.0 (Video Player ad-serving interface definition) biedt een algemene interface voor het afspelen van videoadvertenties. Het biedt gebruikers een rijke mediabeleving en biedt uitgevers de mogelijkheid om advertenties beter te richten, indrukken bij te houden en te monetiseren, en video-inhoud te monetiseren.
seo-title: VPAID 2.0-ondersteuning
title: VPAID 2.0-ondersteuning
uuid: 462692b5-c4b3-4488-adb3-f309809d64ad
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# VPAID 2.0-ondersteuning {#vpaid-ad-support}

VPAID 2.0 (Video Player ad-serving interface definition) biedt een algemene interface voor het afspelen van videoadvertenties. Het biedt gebruikers een rijke mediabeleving en biedt uitgevers de mogelijkheid om advertenties beter te richten, indrukken bij te houden en te monetiseren, en video-inhoud te monetiseren.

De volgende functies worden ondersteund:

* Versie 2.0 van de VPAID-specificatie

   Zie [IAB VPAID 2.0](https://www.iab.com/guidelines/digital-video-player-ad-interface-definition-vpaid-2-0/)voor meer informatie.
* Lineaire VPAID-advertenties met video-on-demand (VOD)-inhoud
* In Live-inhoud ondersteunt Browser-TVSDK pre-roll JavaScript VPAID-advertenties.
* In de fallback-modus van Flash ondersteunt Browser-TVSDK alleen op Flash gebaseerde VPAID-advertenties.
* Lineaire VPAID-advertenties van JavaScript

   VPAID-advertenties moeten zijn gebaseerd op JavaScript en in de reactie op de advertentie moet het mediatype van de VPAID-advertentie worden geïdentificeerd als `application/javascript`.

De volgende functies worden niet ondersteund:

* Versie 1.0 van de VPAID-specificatie
* Overschakelbare advertenties
* Niet-lineaire advertenties, zoals overlayadvertenties, dynamische metgezel, minimizable advertenties, inklapbare advertenties en uitbreidbare advertenties.
* VPAID-advertenties vooraf laden
* VPAID-advertenties in live-inhoud
* Flash VPAID-advertenties

## API {#section_0DB1D383CA5047B281BC808BC082C69B}

De volgende API-elementen ondersteunen VPAID 2.0-advertenties:

* De `getCustomAdView` methode om een `MediaPlayer` object te `CustomAdView` retourneren, die de webweergave vertegenwoordigt die de VPAID-advertentie rendert.

   Raadpleeg de documentatie bij de `getCustomAdView` MediaPlayer-API voor meer informatie over de [methode](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/AdobePSDK.MediaPlayer.html).

* `MediaPlayer.setCustomAdTimeout(int milliseconds)` Hiermee stelt u de time-out in voor het laadproces van VPAID.

   De standaardwaarde voor een time-out is 10 seconden.

* Met de API kunt `auditudeSettings.ignoreVPAIDAds`u VPAID-advertenties negeren die zijn ontvangen van de Auditude-server. De API werkt niet voor Flash Fallback.

Tijdens het afspelen van de VPAID-advertentie:

* De VPAID-advertentie wordt weergegeven in een weergavecontainer boven de spelerweergave, zodat code die afhankelijk is van tikken door gebruikers in de spelerweergave, niet werkt.
* Aanroepen om de VPAID-advertentie te pauzeren en af te spelen op de spelerinstantie.
* VPAID-advertenties hebben geen vooraf gedefinieerde duur, omdat de advertentie interactief kan zijn.

   De duur van de advertentie en de totale duur van de advertentie die zijn opgegeven in de reactie van de advertentieserver, zijn mogelijk niet nauwkeurig.