---
description: Voer de volgende stappen uit om een basisspeler te maken met de Browser-TVSDK.
title: Een basisspeler maken met TVSDK
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---


# Een basisspeler maken met TVSDK{#create-a-basic-player-using-tvsdk}

Voer de volgende stappen uit om een basisspeler te maken met de Browser-TVSDK.

1. Maak een nieuwe map waarin u de gecomprimeerde bestanden voor Browser-TVSDK kunt downloaden.
1. Download Browser TVSDK van Zendesk, decomprimeer de bestanden en plaats de map frameworks in de nieuwe directory.
1. Maak een eenvoudige HTML-bouwsteen voor de code met daarin een `div`.
1. Plaats deze bouwsteenplaat in een HTML- dossier in de folder u in stap 1 creeerde.

   ```
   <!DOCTYPE html> 
   
   <html lang="en"> 
   <head> 
   </head> 
   <body> 
         <div id="videoDiv" width="200" height="200"> 
        <div id="video-controls"></div> 
         </div> 
   </body> 
   </html>
   ```

1. Voeg de Browser TVSDK bibliotheken in de hoofdsectie toe.

   ```js
   <script src= "frameworks/player/dash.min.js"></script> 
   <script src= "frameworks/player/primetimemain.min.js"></script> 
   <script src= "frameworks/player/swfobject.js"></script> 
   <script src= "frameworks/player/primetimeei.min.js"></script>
   ```

1. Voeg de sectie `onLoad` toe voor de body-tag.

   ```
   <body onload="startVideo()">
   ```

1. Start met de implementatie van de functie `startVideo`.
1. Voeg een scripttag toe en maak de functie `startVideo` in de tag.

   Dit hoort in de kopsectie van de pagina te staan.

   ```js
   <script> 
    function startVideo(){ 
    } 
   </script>
   ```

1. Maak de `Adobe.MediaPlayer`.

   ```js
   var player = new AdobePSDK.MediaPlayer();
   ```

1. Maak de `MediaPlayerView`.

   >[!TIP]
   >
   >Dit is waar `div` wordt gebruikt die u vroeger creeerde.

   ```js
   var view = new AdobePSDK.MediaPlayerView( 
   document.getElementById("videoDiv")); 
   player.view = view;
   ```

1. Voeg de gebeurtenislistener voor de speler toe.

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED, onStatusChange);
   ```

1. Implementeer de gebeurtenishandler en plaats deze vóór de gebeurtenislistener toevoegen.

   ```js
   var onStatusChange = function (event) { 
    console.log(event.status); 
   
    switch (event.status) { 
     case AdobePSDK.MediaPlayerStatus.IDLE: 
      console.log("Player Status: IDLE"); 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.INITIALIZING: 
      console.log("Player Status: INITIALIZING"); 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.INITIALIZED: 
      console.log("Player Status: INITIALIZED"); 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.PREPARING: 
      console.log("Player Status: PREPARING"); 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.PREPARED: 
      console.log("Player Status: PREPARED"); 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.PLAYING: 
      console.log("Player Status: PLAYING"); 
      //update UI play/pause to show pause icon 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.PAUSED: 
      console.log("Player Status: PAUSED"); 
      //update UI play/pause to show play icon & 
      //display pause icon over video 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.SEEKING: 
      console.log("Player Status: SEEKING"); 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.COMPLETE: 
      console.log("Player Status: COMPLETE"); 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.RELEASED: 
      console.log("Player Status: RELEASED"); 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.RELEASED: 
      console.log("Player Status: ERROR"); 
      break; 
    } 
   }; 
   ```

1. Maak de `MediaResource`, die de M3U8-koppeling (of mpd) doorgeeft.

   ```js
   var resourceUrl = "https://example.com/a/yourUrl.m3u8"; 
   var resourceType = AdobePSDK.MediaResourceType.HLS; 
   var mediaResource = new AdobePSDK.MediaResource(resourceUrl, resourceType, null, false);
   ```

1. Creeer leeg config en vervang het middel.

   ```js
   var config = new AdobePSDK.MediaPlayerItemConfig(); 
   
   player.replaceCurrentResource(mediaResource, config);
   ```

1. Roep `prepareToPlay` aan wanneer de speler in de geINITIALISEERDE status is.

   ```js
   case INITIALIZED: 
    player.prepareToPlay(); // <- add this line 
    break;
   ```

1. Nadat de speler in de VOORBEREIDENDE staat is, roep `play`.

   ```js
   case PREPARED: 
    player.play(); 
    break;
   ```

