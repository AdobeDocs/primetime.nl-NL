---
description: Video Player Ad-Serving Interface Definition (VPAID) 2.0 biedt een algemene interface voor het afspelen van videoadvertenties. Het biedt gebruikers een rijke mediabeleving en biedt uitgevers de mogelijkheid om advertenties beter te richten, afbeeldingen bij te houden en te drukken en video-inhoud te monetiseren.
title: VPAID 2.0-ondersteuning
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---

# VPAID 2.0-ondersteuning {#vpaid-ad-support}

Video Player Ad-Serving Interface Definition (VPAID) 2.0 biedt een algemene interface voor het afspelen van videoadvertenties. Het biedt gebruikers een rijke mediabeleving en biedt uitgevers de mogelijkheid om advertenties beter te richten, afbeeldingen bij te houden en te drukken en video-inhoud te monetiseren.

De volgende functies worden ondersteund:

* Versie 2.0 van de VPAID-specificatie

  Raadpleeg voor meer informatie [IAB VPAID 2.0](https://www.iab.com/wp-content/uploads/2015/06/VPAID_2_0_Final_04-10-2012.pdf).
* Lineaire VPAID-advertenties op video-on-demand (VOD)-inhoud
* JavaScript VPAID-advertenties

  VPAID-advertenties moeten zijn gebaseerd op JavaScript en in de reactie op de advertentie moet het mediatype van de VPAID-advertentie worden geïdentificeerd als `application/javascript`.

De volgende functies worden niet ondersteund:

* Versie 1.0 van de VPAID-specificatie
* Skiable ads
* Niet-onlineadvertenties zoals overlayadvertenties, dynamische metgezeadvertenties, minimizable advertenties, inklapbare advertenties en uitbreidbare advertenties
* VPAID-advertenties vooraf laden
* VPAID-advertenties in live-inhoud
* VPAID-advertenties Flash
* VPAID-advertentie na de rol

## API-wijzigingen {#section_D62F3E059C6C493592D34534B0BFC150}

De API is als volgt gewijzigd:

* `PTAuditudeMetadata` heeft een `customAdLoadTimeout` eigenschap om de standaardtime-out bij het laden van de VPAID te wijzigen.

  De standaardwaarde voor een time-out is 10 seconden.

* `PTMediaPlayerCustomAdNotification` wordt verzonden vanuit de `PTMediaPlayer` instance

<!--<a id="section_495700E1C5404A7B85307A4137C740C5"></a>-->

Tijdens het afspelen van de VPAID-advertentie:

* De VPAID-advertentie wordt weergegeven in een weergavecontainer boven de spelerweergave, zodat de code die afhankelijk is van tikken door gebruikers in de spelerweergave, niet werkt.
* De hoofdspeler voor inhoud wordt gepauzeerd en aanroepen naar `pause` en `play` op de spelerinstantie worden gebruikt om de VPAID-advertentie te pauzeren en te hervatten.

* VPAID-advertenties hebben geen vooraf gedefinieerde duur, omdat de advertentie interactief kan zijn.

  De duur van de advertentie en de totale duur van de advertentie die door de reactie van de advertentieserver worden bepaald, zijn mogelijk niet nauwkeurig.

## VPAID 2.0-integratie implementeren {#section_63C9C737367C4A0AB4D62E0DC2084141}

U kunt als volgt VPAID 2.0-ondersteuning toevoegen aan uw iOS-toepassing:

1. (Optioneel) Voeg een listener toe voor aangepaste advertentiegebeurtenissen.

   ```
   [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerCustomAdNotification:) name:PTMediaPlayerCustomAdNotification object:self.player];
   ```

1. (Optioneel) Geef de melding weer.

   ```
   -(void)onMediaPlayerCustomAdNotification:(NSNotification *)notification{    PTCustomAdNotificationObject *notificationObject = [notification.userInfo objectForKey:PTCustomAdNotificationObjectKey];    if (notificationObject)    
   {        NSLog(@"ViewController:: Custom Ad Notification Received: %ld", notificationObject.type);    } 
   
   }
   ```
