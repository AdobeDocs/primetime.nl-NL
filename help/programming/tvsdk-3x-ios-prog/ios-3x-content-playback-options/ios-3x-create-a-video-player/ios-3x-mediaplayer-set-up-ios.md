---
description: Met de PTMediaPlayer-interface worden de functionaliteit en het gedrag van een mediaspelerobject ingekapseld.
title: PTMediaPlayer instellen
exl-id: 6d16bfd2-8d1d-4261-b343-c2e999c4d28b
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# PTMediaPlayer instellen {#set-up-the-ptmediaplayer}

TVSDK beschikt over gereedschappen voor het maken van een geavanceerde videospelertoepassing (uw Primetime-speler), die u kunt integreren met andere Primetime-componenten.

Gebruik de gereedschappen van uw platform om een speler te maken en deze aan te sluiten op de weergave van de mediaspeler in TVSDK, die beschikt over methoden om video&#39;s af te spelen en te beheren. TVSDK beschikt bijvoorbeeld over afspeel- en pauzemethoden. U kunt gebruikersinterfaceknoppen op uw platform tot stand brengen en de knopen plaatsen om die methodes te roepen TVSDK.

Met de PTMediaPlayer-interface worden de functionaliteit en het gedrag van een mediaspelerobject ingekapseld.

Als u uw `PTMediaPlayer`:

1. Haal de URL van het medium op vanuit de gebruikersinterface, bijvoorbeeld in een tekstveld.

   ```
   NSURL *url = [NSURL URLWithString:textFieldURL.text];
   ```

1. Maken `PTMetadata`.

   Stel dat uw methode `createMetada` bereidt meta-gegevens voor (zie [Reclame](../../ios-3x-advertising/ios-3x-advertising-requirements.md)).

   ```
   PTMetadata *metadata = [self createMetadata]
   ```

1. Maken `PTMediaPlayerItem` door uw `PTMetadata` -instantie.

   ```
   PTMediaPlayerItem *item = [[[PTMediaPlayerItem alloc] 
          initWithUrl:url mediaId:yourMediaID metadata:metadata] autorelease];
   ```

1. Voeg waarnemers toe aan meldingen die door TVSDK worden verzonden.

   ```
   [self addObservers]
   ```

1. Maken `PTMediaPlayer` met uw nieuwe `PTMediaPlayerItem`.

   ```
   PTMediaPlayer *player = [PTMediaPlayer playerWithMediaPlayerItem:item];
   ```

1. Stel eigenschappen in voor de speler.

   Hier zijn enkele van de beschikbare `PTMediaPlayer` eigenschappen:

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

1. Bellen `play` om het afspelen van media te starten.

   ```
   [player play];
   ```
