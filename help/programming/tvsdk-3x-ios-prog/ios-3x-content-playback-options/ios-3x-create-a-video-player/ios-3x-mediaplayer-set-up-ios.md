---
description: Met de PTMediaPlayer-interface worden de functionaliteit en het gedrag van een mediaspelerobject ingekapseld.
title: PTMediaPlayer instellen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '181'
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

   Stel dat uw methode `createMetada` metagegevens voorbereidt (zie [Reclame](../../ios-3x-advertising/ios-3x-advertising-requirements.md)).

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
