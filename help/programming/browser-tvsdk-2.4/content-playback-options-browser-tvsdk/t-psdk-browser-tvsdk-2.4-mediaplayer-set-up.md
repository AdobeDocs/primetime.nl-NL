---
description: Een MediaPlayer-object kapselt het gedrag en de functionaliteit van een mediaspeler in.
title: De MediaPlayer instellen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
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

1. Een `MediaPlayerView` -instantie:

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

   Bellen:

   ```js
   var view = new  
   <codeph>
   AdobePSDK.MediaPlayerView 
   </codeph>( 
         document.getElementById("videoDiv"));  
   ```

1. Voeg uw `MediaPlayerView` -instantie `MediaPlayer` -instantie:

   ```js
   player.view = view;
   ```

1. Aangepaste besturingselementen bijvoegen `div` -element naar uw MediaPlayer-instantie.

   Bijvoorbeeld in HTML:

   ```
   <div id="videoDiv"> 
      <div id="video-controls"> 
         ..... custom video controls 
      </div> 
   </div>
   ```

   Bellen:

   ```js
   if (typeof player.getView() !== 'undefined') { 
       var view = player.view; 
       view.attachVideoControls(document.getElementById("video-controls")); 
   }
   ```

De `MediaPlayer` -instantie is nu beschikbaar en correct geconfigureerd voor het weergeven van video-inhoud op het apparaatscherm.
