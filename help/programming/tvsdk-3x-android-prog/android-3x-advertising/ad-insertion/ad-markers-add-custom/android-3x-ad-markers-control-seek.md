---
description: U kunt het standaardgedrag voor de manier waarop TVSDK-handgrepen zoeken op advertenties negeren wanneer u aangepaste advertentiemarkeringen gebruikt.
title: Afspeelgedrag bepalen voor zoeken op aangepaste advertentiemarkeringen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---


# Afspeelgedrag bepalen voor zoeken op aangepaste advertentiemarkeringen {#control-playback-behavior-for-seeking-over-custom-ad-markers}

U kunt het standaardgedrag voor de manier waarop TVSDK-handgrepen zoeken op advertenties negeren wanneer u aangepaste advertentiemarkeringen gebruikt.

Wanneer een gebruiker gedeelten zoekt die afkomstig zijn van de plaatsing van aangepaste advertentiemarkeringen, slaat TVSDK de advertenties standaard over. Dit kan verschillen van het huidige afspeelgedrag voor standaard en eindpunten. U kunt TVSDK zo instellen dat de afspeelkop wordt verplaatst naar het begin van de laatst overgeslagen aangepaste advertentie wanneer de gebruiker voorbij een of meer aangepaste advertenties zoekt.

1. Roep `CustomRangeMetadata.setAdjustSeekPosition` met `true`.

   ```java
   customRangeMetadata.setAdjustSeekPosition (true);
   ```

1. Gebruik `customRangeMetadata` in `MediaPlayerItemConfig`.

   ```java
   // Set customRangeMetadata 
   config.setCustomRangeMetadata(customRangeMetadata); 
   
   // prepare the content for playback by calling replaceCurrentResource 
   mediaPlayer.replaceCurrentResource(mediaResource, config); 
   ```
