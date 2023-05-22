---
description: Bij Closed Captioning wordt het audiogedeelte van een video als tekst op het scherm weergegeven wanneer het geluid onhoorbaar is of de kijker niet goed kan worden gehoord.
title: Selecteer een ondertitelingstrack uit de beschikbare tracks
exl-id: 75970604-c318-4621-bad3-caab292c8a04
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---

# Selecteer een ondertitelingstrack uit de beschikbare tracks{#select-a-current-caption-track-from-among-available-tracks}

U kunt een track selecteren in een lijst met momenteel beschikbare Closed Caption-tracks. Dit wordt de huidige track die wordt weergegeven wanneer de zichtbaarheid is ingeschakeld. Sommige sporen zouden niet aanvankelijk beschikbaar kunnen zijn, zodat luistert naar de gebeurtenis die erop wijst dat meer beschikbaar is geworden.

>[!TIP]
>
>Gesloten bijschriften zijn altijd ingeschakeld. Alle standaard Closed Caption-tracks worden als aanwezig beschouwd. Standaardtracks (zoals CC1-CC4, CS1-CS6) worden opgesomd in `ClosedCaptionsTrack.DefaultCCTypes`. Wanneer het afspelen begint, zoekt TVSDK naar activiteit op elk van deze kanalen. Als het activiteit vindt, stelt het `isActive` methode voor die track en verzendt de `MediaPlayer.PlaybackEventListener.onUpdated` gebeurtenis.

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
           mediaPlayer.getCurrentItem().selectClosedCaptionsTrack(track); 
           selectedClosedCaptionsIndex = i; 
       } 
   }
   ```

1. Voer een luisteraar voor de gebeurtenis uit die erop wijst dat meer sporen beschikbaar zijn. Wanneer TVSDK de gebeurtenis verzendt, haalt u de huidige lijst met beschikbare tracks op.

   Haal de lijst telkens op wanneer de gebeurtenis plaatsvindt om ervoor te zorgen dat u altijd de meest actuele lijst hebt.
