---
description: Bij Closed Captioning wordt het audiogedeelte van een video als tekst op het scherm weergegeven wanneer het geluid onhoorbaar is of de kijker niet goed kan worden gehoord.
seo-description: Bij Closed Captioning wordt het audiogedeelte van een video als tekst op het scherm weergegeven wanneer het geluid onhoorbaar is of de kijker niet goed kan worden gehoord.
seo-title: Selecteer een ondertitelingstrack uit de beschikbare tracks
title: Selecteer een ondertitelingstrack uit de beschikbare tracks
uuid: 637a70c9-9bef-4b13-8b1f-62f22f983e80
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Selecteer een ondertitelingstrack uit de beschikbare tracks{#select-a-current-caption-track-from-among-available-tracks}

U kunt een track selecteren in een lijst met momenteel beschikbare Closed Caption-tracks. Dit wordt de huidige track die wordt weergegeven wanneer de zichtbaarheid is ingeschakeld. Sommige sporen zouden niet aanvankelijk beschikbaar kunnen zijn, zodat luistert naar de gebeurtenis die erop wijst dat meer beschikbaar is geworden.

>[!TIP]
>
>Gesloten bijschriften zijn altijd ingeschakeld. Alle standaard Closed Caption-tracks worden als aanwezig beschouwd. Standaardtracks (zoals CC1-CC4, CS1-CS6) worden opgesomd in `ClosedCaptionsTrack.DefaultCCTypes`. Wanneer het afspelen begint, zoekt TVSDK naar activiteit op elk van deze kanalen. Als het activiteit vindt, plaatst het de `isActive` methode voor dat spoor en verzendt de `MediaPlayer.PlaybackEventListener.onUpdated` gebeurtenis.

1. Wacht tot de mediaspeler zich ten minste in de staat PREPARED bevindt.
1. Luister naar deze gebeurtenissen:

   * `MediaPlayer.PlaybackEventListener.onStateChanged with state MediaPlayer.PlayerState.INITIALIZED`: De initiële lijst met Closed Caption-tracks is beschikbaar

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
}}

```
1. Implement a listener for the event that indicates that more tracks are available. When TVSDK dispatches the event, retrieve the current list of available tracks.

Retrieve the list each time that the event occurs to ensure that you always have the most current list.

