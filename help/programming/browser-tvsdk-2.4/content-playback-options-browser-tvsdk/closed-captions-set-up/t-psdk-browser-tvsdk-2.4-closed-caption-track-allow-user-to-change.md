---
description: Hier ziet u hoe een gebruiker een track met een gesloten bijschrift kan selecteren.
title: De gebruiker toestaan de track te wijzigen
exl-id: 103ca0ad-2707-4e4f-87ee-f55041e4527a
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '77'
ht-degree: 0%

---

# De gebruiker toestaan de track te wijzigen{#allow-the-user-to-change-the-track}

Hier ziet u hoe een gebruiker een track met een gesloten bijschrift kan selecteren.

1. Als u de beschikbare Closed Caption-tracks wilt weergeven, gebruikt u de opdracht `MediaPlayerItem.closedCaptionsTracks` eigenschap.

   ```js
   var tracks = item.closedCaptionsTracks;
   ```

1. Als u wilt instellen welke Closed Caption-track actief is, gebruikt u de optie `MediaPlayerItem.selectClosedCaptionsTrack` methode.
1. Nadat het item van de mediaspeler is voorbereid, haalt u het op uit de mediaspeler met de ` MediaPlayer.  currentItem ` methode.

   ```js
   // Select the cc track with index k. 
   var item = mediaPlayer.currentItem;     
   var tracks = item.closedCaptionsTracks; 
   
   if (k >= 0 && k < tracks.length) { 
       item.selectClosedCaptionsTrack(tracks[k]); 
   }
   ```
