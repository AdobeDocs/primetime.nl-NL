---
description: Video Player Ad-Serving Interface Definition (VPAID) 2.0 biedt een algemene interface voor het afspelen van videoadvertenties. Het biedt gebruikers een rijke mediabeleving en biedt uitgevers de mogelijkheid om advertenties beter te richten, indrukken bij te houden en te monetiseren, en video-inhoud te monetiseren.
seo-description: Video Player Ad-Serving Interface Definition (VPAID) 2.0 biedt een algemene interface voor het afspelen van videoadvertenties. Het biedt gebruikers een rijke mediabeleving en biedt uitgevers de mogelijkheid om advertenties beter te richten, indrukken bij te houden en te monetiseren, en video-inhoud te monetiseren.
seo-title: VPAID 2.0-ondersteuning
title: VPAID 2.0-ondersteuning
uuid: d9a06f3c-0ac2-48aa-b6d2-915184027a38
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---


# VPAID 2.0 en ondersteuning {#vpaid-ad-support}

Video Player Ad-Serving Interface Definition (VPAID) 2.0 biedt een algemene interface voor het afspelen van videoadvertenties. Het biedt gebruikers een rijke mediabeleving en biedt uitgevers de mogelijkheid om advertenties beter te richten, indrukken bij te houden en te monetiseren, en video-inhoud te monetiseren.

De volgende functies worden ondersteund:

* Versie 2.0 van de VPAID-specificatie

   Raadpleeg [IAB VPAID 2.0](https://www.iab.com/wp-content/uploads/2015/06/VPAID_2_0_Final_04-10-2012.pdf) voor meer informatie.
* Lineaire VPAID-advertenties op video-on-demand (VOD)-inhoud
* JavaScript VPAID-advertenties

   VPAID-advertenties moeten zijn gebaseerd op JavaScript en in de reactie op de advertentie moet het mediatype van de VPAID-advertentie worden aangeduid als `application/javascript`.

De volgende functies worden niet ondersteund:

* Versie 1.0 van de VPAID-specificatie
* Overschakelbare advertenties
* Niet-onlineadvertenties zoals overlayadvertenties, dynamische metgezeadvertenties, minimizable advertenties, inklapbare advertenties en uitbreidbare advertenties
* VPAID-advertenties vooraf laden
* VPAID-advertenties in live-inhoud
* Flash VPAID-advertenties
* VPAID-advertentie na de rol

## API-wijzigingen {#section_D62F3E059C6C493592D34534B0BFC150}

De API is als volgt gewijzigd:

* `PTAuditudeMetadata` heeft een  `customAdLoadTimeout` eigenschap om de standaardtime-out van het VPAID-laadproces te wijzigen.

   De standaardwaarde voor een time-out is 10 seconden.

* `PTMediaPlayerCustomAdNotification` wordt verzonden vanuit de  `PTMediaPlayer` instantie

<!--<a id="section_495700E1C5404A7B85307A4137C740C5"></a>-->

Tijdens het afspelen van de VPAID-advertentie:

* De VPAID-advertentie wordt weergegeven in een weergavecontainer boven de spelerweergave, zodat de code die afhankelijk is van tikken door gebruikers in de spelerweergave, niet werkt.
* De hoofdinhoudspeler wordt gepauzeerd, en de vraag aan `pause` en `play` op de spelerinstantie wordt gebruikt om de VPAID te pauzeren en te hervatten.

* VPAID-advertenties hebben geen vooraf gedefinieerde duur, omdat de advertentie interactief kan zijn.

   De duur van de advertentie en de totale duur van de advertentie die door de reactie van de advertentieserver worden bepaald, zijn mogelijk niet nauwkeurig.

## Implementeer VPAID 2.0-integratie {#section_63C9C737367C4A0AB4D62E0DC2084141}

U voegt als volgt VPAID 2.0-ondersteuning toe aan uw iOS-toepassing:

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

