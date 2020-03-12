---
description: Met de PTMediaPlayer-interface worden de functionaliteit en het gedrag van een mediaspelerobject ingekapseld.
seo-description: Met de PTMediaPlayer-interface worden de functionaliteit en het gedrag van een mediaspelerobject ingekapseld.
seo-title: PTMediaPlayer instellen
title: PTMediaPlayer instellen
uuid: 698034d3-1260-416f-83b0-6b7d058750a0
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# PTMediaPlayer instellen {#set-up-the-ptmediaplayer}

TVSDK beschikt over gereedschappen voor het maken van een geavanceerde videospelertoepassing (uw Primetime-speler), die u kunt integreren met andere Primetime-componenten.

Gebruik de gereedschappen van uw platform om een speler te maken en deze aan te sluiten op de weergave van de mediaspeler in TVSDK, die beschikt over methoden om video&#39;s af te spelen en te beheren. TVSDK beschikt bijvoorbeeld over afspeel- en pauzemethoden. U kunt gebruikersinterfaceknoppen op uw platform tot stand brengen en de knopen plaatsen om die methodes te roepen TVSDK.

Met de PTMediaPlayer-interface worden de functionaliteit en het gedrag van een mediaspelerobject ingekapseld.

Stel uw `PTMediaPlayer`:

1. Haal de URL van het medium op vanuit de gebruikersinterface, bijvoorbeeld in een tekstveld.

   ```
   NSURL *url = [NSURL URLWithString:textFieldURL.text];
   ```

1. Maken `PTMetadata`.

   Stel dat uw methode metagegevens `createMetada` voorbereidt (zie [Advertising](../../ios-3x-advertising/ios-3x-advertising-requirements.md)).

   ```
   PTMetadata *metadata = [self createMetadata]
   ```

1. Maak `PTMediaPlayerItem` met uw `PTMetadata` instantie.

   ```
   PTMediaPlayerItem *item = [[[PTMediaPlayerItem alloc] 
          initWithUrl:url mediaId:yourMediaID metadata:metadata] autorelease];
   ```

1. Voeg waarnemers toe aan meldingen die door TVSDK worden verzonden.

   ```
   [self addObservers]
   ```

1. Maak uw nieuwe `PTMediaPlayer` versie `PTMediaPlayerItem`.

   ```
   PTMediaPlayer *player = [PTMediaPlayer playerWithMediaPlayerItem:item];
   ```

1. Stel eigenschappen in voor de speler.

   Hier volgen enkele beschikbare `PTMediaPlayer` eigenschappen:

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

1. Vraag `play` om media playback te beginnen.

   ```
   [player play];
   ```
