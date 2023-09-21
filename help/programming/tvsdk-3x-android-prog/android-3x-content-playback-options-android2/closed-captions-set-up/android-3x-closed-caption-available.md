---
description: U kunt een track selecteren in een lijst met momenteel beschikbare Closed Caption-tracks. Dit wordt de huidige track die wordt weergegeven wanneer de zichtbaarheid is ingeschakeld. Sommige sporen zouden niet aanvankelijk beschikbaar kunnen zijn, zodat luistert naar de gebeurtenis die erop wijst dat meer beschikbaar is geworden.
title: Selecteer een ondertitelingstrack uit de beschikbare tracks
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# Selecteer een ondertitelingstrack uit de beschikbare tracks {#select-a-current-caption-track-from-among-available-tracks}

U kunt een track selecteren in een lijst met momenteel beschikbare Closed Caption-tracks. Dit wordt de huidige track die wordt weergegeven wanneer de zichtbaarheid is ingeschakeld. Sommige sporen zouden niet aanvankelijk beschikbaar kunnen zijn, zodat luistert naar de gebeurtenis die erop wijst dat meer beschikbaar is geworden.

1. Wacht tot de mediaspeler zich in ten minste `PREPARED` status.
1. Luister naar deze gebeurtenissen:

   * `MediaPlayerEvent.STATUS_CHANGED` met status `MediaPlayerStatus.INITIALIZED`: De eerste lijst met Closed Caption-tracks is beschikbaar.

1. Hiermee wordt een lijst opgehaald met alle momenteel beschikbare Closed Caption-tracks.

   Bijvoorbeeld:

   ```java
   List<ClosedCaptionsTrack> ccTracks = 
     mediaPlayer.getCurrentItem().getClosedCaptionsTracks();
   ```

1. Selecteer een beschikbare track als huidige track.

   Bijvoorbeeld:

   ```java
   // Select the initial CC track. 
   for (int i = 0; i < ccTracks.size(); i++) { 
       ClosedCaptionsTrack track = ccTracks.get(i); 
       if (track.getName().equals(INITIAL_CC_TRACK)) {
        <b>mediaPlayer.getCurrentItem().selectClosedCaptionsTrack(track);</b> 
             selectedClosedCaptionsIndex = i; 
       } 
   }
   ```

1. Voer een luisteraar voor de gebeurtenis uit die erop wijst dat meer sporen beschikbaar zijn. Wanneer TVSDK de gebeurtenis verzendt, haalt u de huidige lijst met beschikbare tracks op.

   Haal de lijst telkens op wanneer de gebeurtenis plaatsvindt om ervoor te zorgen dat u altijd de meest actuele lijst hebt.
