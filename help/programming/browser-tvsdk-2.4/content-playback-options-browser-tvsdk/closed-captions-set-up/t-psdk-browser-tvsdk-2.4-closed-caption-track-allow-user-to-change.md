---
description: Hier ziet u hoe een gebruiker een track met een gesloten bijschrift kan selecteren.
title: De gebruiker toestaan de track te wijzigen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '77'
ht-degree: 0%

---


# Laat de gebruiker het spoor wijzigen{#allow-the-user-to-change-the-track}

Hier ziet u hoe een gebruiker een track met een gesloten bijschrift kan selecteren.

1. Gebruik de eigenschap `MediaPlayerItem.closedCaptionsTracks` om de beschikbare Closed Caption-tracks weer te geven.

   ```js
   var tracks = item.closedCaptionsTracks;
   ```

1. Gebruik de methode `MediaPlayerItem.selectClosedCaptionsTrack` om in te stellen welke Closed Caption-track actief is.
1. Nadat het item van de mediaspeler is voorbereid, haalt u dit op uit de mediaspeler met de methode ` MediaPlayer.  currentItem `.

   ```js
   // Select the cc track with index k. 
   var item = mediaPlayer.currentItem;     
   var tracks = item.closedCaptionsTracks; 
   
   if (k >= 0 && k < tracks.length) { 
       item.selectClosedCaptionsTrack(tracks[k]); 
   }
   ```

