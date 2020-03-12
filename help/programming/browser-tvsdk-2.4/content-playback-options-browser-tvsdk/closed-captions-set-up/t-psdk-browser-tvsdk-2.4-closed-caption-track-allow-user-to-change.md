---
description: Hier ziet u hoe een gebruiker een track met een gesloten bijschrift kan selecteren.
seo-description: Hier ziet u hoe een gebruiker een track met een gesloten bijschrift kan selecteren.
seo-title: De gebruiker toestaan de track te wijzigen
title: De gebruiker toestaan de track te wijzigen
uuid: bd3d4d20-9b52-4365-b656-83ec2a405a1c
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# De gebruiker toestaan de track te wijzigen{#allow-the-user-to-change-the-track}

Hier ziet u hoe een gebruiker een track met een gesloten bijschrift kan selecteren.

1. Gebruik de `MediaPlayerItem.closedCaptionsTracks` eigenschap om de beschikbare Closed Caption-tracks weer te geven.

   ```js
   var tracks = item.closedCaptionsTracks;
   ```

1. Gebruik de `MediaPlayerItem.selectClosedCaptionsTrack` methode om in te stellen welke Closed Caption-track actief is.
1. Nadat het item van de mediaspeler is voorbereid, haalt u het op via de ` MediaPlayer.  currentItem ` methode.

   ```js
   // Select the cc track with index k. 
   var item = mediaPlayer.currentItem;     
   var tracks = item.closedCaptionsTracks; 
   
   if (k >= 0 && k < tracks.length) { 
       item.selectClosedCaptionsTrack(tracks[k]); 
   }
   ```

