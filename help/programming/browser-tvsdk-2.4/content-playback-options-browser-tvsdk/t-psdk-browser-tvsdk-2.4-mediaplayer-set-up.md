---
description: Een MediaPlayer-object kapselt het gedrag en de functionaliteit van een mediaspeler in.
title: De MediaPlayer instellen
exl-id: f492b2bb-3280-4306-ac4b-8b8d0fd68409
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 0%

---

# De MediaPlayer instellen{#set-up-the-mediaplayer}

Een MediaPlayer-object kapselt het gedrag en de functionaliteit van een mediaspeler in.

1. Instantiëren van een `MediaPlayer` met behulp van het volgende:

   ```js
   var player = new AdobePSDK.MediaPlayer();
   ```

1. Een `MediaPlayerView` instantie:

   ```js
   var view = new AdobePSDK.MediaPlayerView(container);
   ```

   waar `container` is het doel `div` element dat uw `HTMLMediaElement`.

   Bijvoorbeeld op een HTML-pagina:

   ```
   <div id="videoDiv"> 
   <codeph>
     <div id="video-controls"> 
          ... custom video controls 
     </div> 
   </codeph> 
   </div>
   ```

   Bel:

   ```js
   var view = new  
   <codeph>
   AdobePSDK.MediaPlayerView 
   </codeph>( 
         document.getElementById("videoDiv"));  
   ```

1. Voeg uw `MediaPlayerView` -instantie `MediaPlayer` instantie:

   ```js
   player.view = view;
   ```

1. Aangepaste besturingselementen koppelen `div` -element naar uw MediaPlayer-instantie.

   Bijvoorbeeld in HTML:

   ```
   <div id="videoDiv"> 
      <div id="video-controls"> 
         ..... custom video controls 
      </div> 
   </div>
   ```

   Bel:

   ```js
   if (typeof player.getView() !== 'undefined') { 
       var view = player.view; 
       view.attachVideoControls(document.getElementById("video-controls")); 
   }
   ```

De `MediaPlayer` -instantie is nu beschikbaar en correct geconfigureerd voor het weergeven van video-inhoud op het apparaatscherm.
