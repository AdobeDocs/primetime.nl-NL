---
description: Wanneer het afspelen start, begint VOD-media standaard op 0 en start live media op het live punt op de client (MediaPlayer.LIVE_POINT). U kunt het standaardgedrag overschrijven.
title: Een stream invoeren op een bepaald tijdstip
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---

# Een stream invoeren op een bepaald tijdstip{#enter-a-stream-at-a-specific-time}

Wanneer het afspelen start, begint VOD-media standaard op 0 en start live media op het live punt op de client (MediaPlayer.LIVE_POINT). U kunt het standaardgedrag overschrijven.

1. Een positie doorgeven aan `MediaPlayer.prepareToPlay`.
1. Deze positie wordt door de browser TVSDK gebruikt als beginpunt voor het element.

   >[!NOTE]
   >
   >Er is geen zoekbewerking vereist.

1. Als de positie zich niet binnen het doorzoekbare bereik bevindt, worden de standaardposities gebruikt.

   Bijvoorbeeld:

   ```js
   var desiredPostion = //choose a value; 
   onStatusChange = function (event) { 
       case AdobePSDK.MediaPlayerStatus.INITIALIZED: 
           console.log("Player Status: INITIALIZED"); 
           player.prepareToPlay(desiredPostion); 
           break; 
   } 
   ```
