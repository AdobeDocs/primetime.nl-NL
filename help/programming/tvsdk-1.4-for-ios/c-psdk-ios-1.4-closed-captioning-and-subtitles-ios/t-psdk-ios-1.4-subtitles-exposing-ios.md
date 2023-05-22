---
description: De TVSDK informeert uw spelerclient over de beschikbaarheid van de interne AVAsset's availableMediaCharacteristicsWithMediaSelectionOptions via de PTMediaPlayerMediaSelectionOptionsAvailableNotification-melding.
title: Ondertiteling weergeven
exl-id: dc726a5b-2eab-4ebd-8773-7396bf818205
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 0%

---

# Ondertiteling weergeven {#expose-subtitles}

De TVSDK informeert uw spelerclient over de beschikbaarheid van de interne AVAsset&#39;s availableMediaCharacteristicsWithMediaSelectionOptions via de PTMediaPlayerMediaSelectionOptionsAvailableNotification-melding.

U hebt toegang tot de beschikbare ondertitels via de `PTMediaPlayerItem` eigendom `subtitlesOptions`.

Ondertiteling toegankelijk maken:

1. De client registreren als een listener voor de `PTMediaPlayerMediaSelectionOptionsAvailableNotification` kennisgeving.

   ```
   [[NSNotificationCenter defaultCenter]  
     addObserver:self selector:@selector(onMediaPlayerItemMediaSelectionOptionsAvailable:)  
     name:PTMediaPlayerMediaSelectionOptionsAvailableNotification object:self.player];
   ```

   Wanneer uw klant deze melding ontvangt, zijn de ondertitels gereed in het dialoogvenster `PTMediaPlayerItem`.
1. Implementeer de `onMediaPlayerItemMediaSelectionOptionsAvailable` methode vergelijkbaar met het volgende voorbeeld:

   ```
   - (void) onMediaPlayerItemMediaSelectionOptionsAvailable:(NSNotification *) notification { 
       NSArray* subtitlesOptions = self.player.currentItem.subtitlesOptions; 
       NSArray* audioOptions = self.player.currentItem.audioOptions; 
   }
   ```

   Voor informatie over alternatieve audiotracks raadpleegt u  [Alternatieve audio](../alternate-audio/c-psdk-ios-1.4-alternate-audio.md).
