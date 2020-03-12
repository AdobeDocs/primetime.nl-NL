---
description: Video Player Ad-Serving Interface Definition (VPAID) 2.0 biedt een algemene interface voor het afspelen van videoadvertenties. Het biedt gebruikers een rijke mediabeleving en biedt uitgevers de mogelijkheid om advertenties beter te richten, indrukken bij te houden en te monetiseren, en video-inhoud te monetiseren.
seo-description: Video Player Ad-Serving Interface Definition (VPAID) 2.0 biedt een algemene interface voor het afspelen van videoadvertenties. Het biedt gebruikers een rijke mediabeleving en biedt uitgevers de mogelijkheid om advertenties beter te richten, indrukken bij te houden en te monetiseren, en video-inhoud te monetiseren.
seo-title: VPAID 2.0-ondersteuning
title: VPAID 2.0-ondersteuning
uuid: 7168a6e4-9c5e-4d3a-8710-867cf98e4445
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# VPAID 2.0-ondersteuning {#vpaid-ad-support}

Video Player Ad-Serving Interface Definition (VPAID) 2.0 biedt een algemene interface voor het afspelen van videoadvertenties. Het biedt gebruikers een rijke mediabeleving en biedt uitgevers de mogelijkheid om advertenties beter te richten, indrukken bij te houden en te monetiseren, en video-inhoud te monetiseren.

De volgende functies worden ondersteund:

* Versie 2.0 van de VPAID-specificatie

   Raadpleeg [IAB VPAID 2.0](https://www.iab.com/wp-content/uploads/2015/06/VPAID_2_0_Final_04-10-2012.pdf)voor meer informatie.
* Lineaire VPAID-advertenties op video-on-demand (VOD)-inhoud
* JavaScript VPAID-advertenties

   VPAID-advertenties moeten zijn gebaseerd op JavaScript en in de reactie op de advertentie moet het mediatype van de VPAID-advertentie worden geïdentificeerd als `application/javascript`.

De volgende functies worden niet ondersteund:

* Versie 1.0 van de VPAID-specificatie
* Overschakelbare advertenties
* Niet-onlineadvertenties zoals overlayadvertenties, dynamische metgezeadvertenties, minimizable advertenties, inklapbare advertenties en uitbreidbare advertenties
* VPAID-advertenties vooraf laden
* VPAID-advertenties in live-inhoud
* Flash VPAID-advertenties

## API-wijzigingen {#section_D62F3E059C6C493592D34534B0BFC150}

De API is als volgt gewijzigd:

* Er is een `getCustomAdView` functie toegevoegd in `MediaPlayer` en retourneert de webweergave die de VPAID-advertentie rendert.

   Zie `CustomAdView` API-verwijzingen voor meer informatie over het [object dat door deze functie wordt geretourneerd](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/index.html).

* Er wordt een `CUSTOM_AD` gebeurtenis verzonden vanuit de instantie van de mediaspeler.

   De toepassing kan een gebeurteniscallback registreren door uit te voeren `CustomAdEventListener`.

* `MediaPlayer.setCustomAdTimeout(int milliseconds)` Hiermee kunt u de standaardtime-out bij het laden van de VPAID wijzigen.

   De standaardwaarde voor een time-out is 10 seconden.

<!--<a id="section_495700E1C5404A7B85307A4137C740C5"></a>-->

Tijdens het afspelen van de VPAID-advertentie:

* De VPAID-advertentie wordt weergegeven in een weergavecontainer boven de spelerweergave, zodat de code die afhankelijk is van tikken door gebruikers in de spelerweergave, niet werkt.
* De hoofdinhoudspeler wordt gepauzeerd, en de vraag aan `pause` en `play` op de spelerinstantie wordt gebruikt om de VPAID-advertentie te pauzeren en te hervatten.

* VPAID-advertenties hebben geen vooraf gedefinieerde duur, omdat de advertentie interactief kan zijn.

   De duur van de advertentie en de totale duur van de advertentie die door de reactie van de advertentieserver worden bepaald, zijn mogelijk niet nauwkeurig.

## VPAID 2.0-integratie implementeren {#implement-vpaid-integration}

Als u ondersteuning voor VPAID 2.0 wilt toevoegen, voegt u een aangepaste advertentieweergave en de juiste listeners toe.

U voegt als volgt VPAID 2.0-ondersteuning toe:

1. Voeg de aangepaste advertentieweergave toe aan de Player-interface.

   ```java
   _playerFrame.addView(mediaPlayer.createCustomAdView());
   ```

1. Voeg een listener toe voor aangepaste advertentiegebeurtenissen.

   ```java
   mediaplayer.addEventListener(MediaPlayer.Event.CUSTOM_AD,  
     _customAdEventListener);
   ```
