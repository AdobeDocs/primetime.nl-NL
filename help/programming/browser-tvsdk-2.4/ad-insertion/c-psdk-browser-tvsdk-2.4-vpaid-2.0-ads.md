---
description: VPAID 2.0 (Video Player ad-serving interface definition) biedt een algemene interface voor het afspelen van videoadvertenties. Het biedt gebruikers een rijke mediabeleving en biedt uitgevers de mogelijkheid om advertenties beter te richten, indrukken bij te houden en te monetiseren, en video-inhoud te monetiseren.
title: VPAID 2.0-ondersteuning
exl-id: ea3dcd1d-c4e2-46c6-b613-e86c3e161ca8
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---

# VPAID 2.0-ondersteuning {#vpaid-ad-support}

VPAID 2.0 (Video Player ad-serving interface definition) biedt een algemene interface voor het afspelen van videoadvertenties. Het biedt gebruikers een rijke mediabeleving en biedt uitgevers de mogelijkheid om advertenties beter te richten, indrukken bij te houden en te monetiseren, en video-inhoud te monetiseren.

De volgende functies worden ondersteund:

* Versie 2.0 van de VPAID-specificatie

   Zie voor meer informatie [IAB VPAID 2.0](https://www.iab.com/guidelines/digital-video-player-ad-interface-definition-vpaid-2-0/).
* Lineaire VPAID-advertenties met video-on-demand (VOD)-inhoud
* In Live-inhoud ondersteunt Browser-TVSDK pre-roll JavaScript VPAID-advertenties.
* In de Flash fallback-modus ondersteunt Browser-TVSDK alleen op Flash gebaseerde VPAID-advertenties.
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

* De `getCustomAdView` methode `MediaPlayer` retourneert een `CustomAdView` object, dat staat voor de webweergave die de VPAID-advertentie rendert.

   Voor meer informatie over de `getCustomAdView` methode, zie [Documentatie voor de MediaPlayer-API](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/AdobePSDK.MediaPlayer.html).

* `MediaPlayer.setCustomAdTimeout(int milliseconds)` Hiermee stelt u de time-out in voor het laadproces van VPAID.

   De standaardwaarde voor een time-out is 10 seconden.

* De API, `auditudeSettings.ignoreVPAIDAds`, kunt u VPAID-advertenties negeren die zijn ontvangen van de Auditude-server. De API werkt niet voor Flash Fallback.

Tijdens het afspelen van de VPAID-advertentie:

* De VPAID-advertentie wordt weergegeven in een weergavecontainer boven de spelerweergave, zodat code die afhankelijk is van tikken door gebruikers in de spelerweergave, niet werkt.
* Aanroepen om de VPAID-advertentie te pauzeren en af te spelen op de spelerinstantie.
* VPAID-advertenties hebben geen vooraf gedefinieerde duur, omdat de advertentie interactief kan zijn.

   De duur van de advertentie en de totale duur van de advertentie die zijn opgegeven in de reactie van de advertentieserver, zijn mogelijk niet nauwkeurig.
