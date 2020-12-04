---
description: Met de PTMediaPlayer-interface worden de functionaliteit en het gedrag van een mediaspelerobject ingekapseld.
seo-description: Met de PTMediaPlayer-interface worden de functionaliteit en het gedrag van een mediaspelerobject ingekapseld.
seo-title: PTMediaPlayer instellen
title: PTMediaPlayer instellen
uuid: 78549406-7e33-4bca-a25e-1e433f6a75d7
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---


# PTMediaPlayer {#set-up-the-ptmediaplayer} instellen

TVSDK beschikt over gereedschappen voor het maken van een geavanceerde videospelertoepassing (uw Primetime-speler), die u kunt integreren met andere Primetime-componenten.

Gebruik de gereedschappen van uw platform om een speler te maken en deze aan te sluiten op de weergave van de mediaspeler in TVSDK, die beschikt over methoden om video&#39;s af te spelen en te beheren. TVSDK beschikt bijvoorbeeld over afspeel- en pauzemethoden. U kunt gebruikersinterfaceknoppen op uw platform tot stand brengen en de knopen plaatsen om die methodes te roepen TVSDK.

Met de PTMediaPlayer-interface worden de functionaliteit en het gedrag van een mediaspelerobject ingekapseld.

Uw `PTMediaPlayer` instellen:

1. Haal de URL van het medium op vanuit de gebruikersinterface, bijvoorbeeld in een tekstveld.

   ```
   NSURL *url = [NSURL URLWithString:textFieldURL.text];
   ```

1. `PTMetadata` maken.

   Stel dat uw methode `createMetada` metagegevens voorbereidt (zie [Reclame](../ad-insertion/r-psdk-ios-1.4-advertising-requirements.md)).

   ```
   PTMetadata *metadata = [self createMetadata]
   ```

1. Maak `PTMediaPlayerItem` door uw `PTMetadata`-instantie te gebruiken.

   ```
   PTMediaPlayerItem *item = [[[PTMediaPlayerItem alloc] 
          initWithUrl:url mediaId:yourMediaID metadata:metadata] autorelease];
   ```

1. Voeg waarnemers toe aan meldingen die door TVSDK worden verzonden.

   ```
   [self addObservers]
   ```

1. Maak `PTMediaPlayer` met de nieuwe `PTMediaPlayerItem`.

   ```
   PTMediaPlayer *player = [PTMediaPlayer playerWithMediaPlayerItem:item];
   ```

1. Stel eigenschappen in voor de speler.

   Hier volgen een aantal van de beschikbare `PTMediaPlayer` eigenschappen:

   ```
   player.autoPlay                    = YES;  
   player.closedCaptionDisplayEnabled = YES; 
   player.videoGravity                = PTMediaPlayerVideoGravityResizeAspect;  
   player.allowsAirPlayVideo          = YES;
   ```

1. Stel de weergave-eigenschap van de speler in.

   ```
   CGRect playerRect = self.adPlayerView.frame;  
   playerRect.origin = CGPointMake(0, 0); 
   playerRect.size = CGSizeMake(self.adPlayerView.frame.size.width,  
                                self.adPlayerView.frame.size.height); 
   
   [player.view setFrame:playerRect]; 
   [player.view setAutoresizingMask:  
         ( UIViewAutoresizingFlexibleWidth | UIViewAutoresizingFlexibleHeight )];
   ```

1. Voeg de weergave van de speler toe in de subweergave van de huidige weergave.

   ```
   [self.adPlayerView  setAutoresizesSubviews:YES];  
   [self.adPlayerView addSubview:(UIView *)player.view];
   ```

1. Roep `play` aan om het afspelen van media te starten.

   ```
   [player play];
   ```

