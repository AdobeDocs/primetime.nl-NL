---
description: VPAID 2.0 (Video Player ad-serving interface definition) biedt een algemene interface voor het afspelen van videoadvertenties. Het biedt gebruikers een rijke mediabeleving en biedt uitgevers de mogelijkheid om advertenties beter te richten, indrukken bij te houden en te monetiseren, en video-inhoud te monetiseren.
title: VPAID 2.0-ondersteuning
exl-id: 8cc08999-6047-4bd0-a09f-8a2e28e09766
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Overzicht {#vpaid-ad-support-overview}

VPAID 2.0 (Video Player ad-serving interface definition) biedt een algemene interface voor het afspelen van videoadvertenties. Het biedt gebruikers een rijke mediabeleving en biedt uitgevers de mogelijkheid om advertenties beter te richten, indrukken bij te houden en te monetiseren, en video-inhoud te monetiseren.

De volgende functies worden ondersteund:

* Versie 2.0 van de VPAID-specificatie

   Raadpleeg voor meer informatie [IAB VPAID 2.0](https://www.iab.com/wp-content/uploads/2015/06/VPAID_2_0_Final_04-10-2012.pdf).
* Lineaire VPAID-advertenties met video-on-demand (VOD)-inhoud
* JavaScript VPAID-advertenties

   VPAID-advertenties moeten zijn gebaseerd op JavaScript en in de reactie op de advertentie moet het mediatype van de VPAID-advertentie worden geïdentificeerd als `application/javascript`.

De volgende functies worden niet ondersteund:

* Versie 1.0 van de VPAID-specificatie
* Overschakelbare advertenties
* Niet-online ooradvertenties, zoals overlayadvertenties, dynamische metgezel, minimizable advertenties, inklapbare advertenties en uitbreidbare advertenties
* VPAID-advertenties vooraf laden
* VPAID-advertenties in live-inhoud
* Flash VPAID-advertenties

## API

De volgende API-elementen ondersteunen VPAID 2.0-advertenties:

* De `getCustomAdView` methode `MediaPlayer` retourneert een `CustomAdView` object, dat de webweergave vertegenwoordigt die de VPAID-advertentie rendert (zie [API-verwijzingen](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/index.html)).

* `MediaPlayer.setCustomAdTimeout(int milliseconds)` Hiermee stelt u de time-out in voor het laadproces van VPAID. De standaardwaarde voor een time-out is 10 seconden.

Tijdens het afspelen van de VPAID-advertentie:

* De VPAID-advertentie wordt weergegeven in een weergavecontainer boven de spelerweergave, zodat code die afhankelijk is van tikken door gebruikers in de spelerweergave, niet werkt.
* verzoekt `pause` en `play` pauzeren en hervatten in de spelerinstantie de VPAID-advertentie.

* VPAID-advertenties hebben geen vooraf gedefinieerde duur, omdat de advertentie interactief kan zijn.

   De duur van de advertentie en de totale duur van de advertentie die zijn opgegeven in de reactie van de advertentieserver, zijn mogelijk niet nauwkeurig.
