---
description: VPAID 2.0 (Video Player ad-serving interface definition) biedt een algemene interface voor het afspelen van videoadvertenties. Het biedt gebruikers een rijke mediabeleving en biedt uitgevers de mogelijkheid om advertenties beter te richten, indrukken bij te houden en te monetiseren, en video-inhoud te monetiseren.
seo-description: VPAID 2.0 (Video Player ad-serving interface definition) biedt een algemene interface voor het afspelen van videoadvertenties. Het biedt gebruikers een rijke mediabeleving en biedt uitgevers de mogelijkheid om advertenties beter te richten, indrukken bij te houden en te monetiseren, en video-inhoud te monetiseren.
seo-title: VPAID 2.0-ondersteuning
title: VPAID 2.0-ondersteuning
uuid: e45e91d2-2aef-4d69-ac80-228d23e8fd7b
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---


# Overzicht {#vpaid-ad-support-overview}

VPAID 2.0 (Video Player ad-serving interface definition) biedt een algemene interface voor het afspelen van videoadvertenties. Het biedt gebruikers een rijke mediabeleving en biedt uitgevers de mogelijkheid om advertenties beter te richten, indrukken bij te houden en te monetiseren, en video-inhoud te monetiseren.

De volgende functies worden ondersteund:

* Versie 2.0 van de VPAID-specificatie

   Raadpleeg [IAB VPAID 2.0](https://www.iab.com/wp-content/uploads/2015/06/VPAID_2_0_Final_04-10-2012.pdf) voor meer informatie.
* Lineaire VPAID-advertenties met video-on-demand (VOD)-inhoud
* JavaScript VPAID-advertenties

   VPAID-advertenties moeten zijn gebaseerd op JavaScript en in de reactie op de advertentie moet het mediatype van de VPAID-advertentie worden aangeduid als `application/javascript`.

De volgende functies worden niet ondersteund:

* Versie 1.0 van de VPAID-specificatie
* Overschakelbare advertenties
* Niet-online ooradvertenties, zoals overlayadvertenties, dynamische metgezel, minimizable advertenties, inklapbare advertenties en uitbreidbare advertenties
* VPAID-advertenties vooraf laden
* VPAID-advertenties in live-inhoud
* Flash VPAID-advertenties

## API

De volgende API-elementen ondersteunen VPAID 2.0-advertenties:

* De `getCustomAdView` methode van `MediaPlayer` keert een `CustomAdView` voorwerp terug, die de Webmening vertegenwoordigt die de VPAID en (zie [API Verwijzingen](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/index.html)) teruggeeft.

* `MediaPlayer.setCustomAdTimeout(int milliseconds)` Hiermee stelt u de time-out in voor het laadproces van VPAID. De standaardwaarde voor een time-out is 10 seconden.

Tijdens het afspelen van de VPAID-advertentie:

* De VPAID-advertentie wordt weergegeven in een weergavecontainer boven de spelerweergave, zodat code die afhankelijk is van tikken door gebruikers in de spelerweergave, niet werkt.
* Aanroepen naar `pause` en `play` op de spelerinstantie pauzeren en hervatten de VPAID-advertentie.

* VPAID-advertenties hebben geen vooraf gedefinieerde duur, omdat de advertentie interactief kan zijn.

   De duur van de advertentie en de totale duur van de advertentie die zijn opgegeven in de reactie van de advertentieserver, zijn mogelijk niet nauwkeurig.