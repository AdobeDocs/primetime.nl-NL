---
description: Een MediaPlayer-object kapselt het gedrag en de functionaliteit van een mediaspeler in.
seo-description: Een MediaPlayer-object kapselt het gedrag en de functionaliteit van een mediaspeler in.
seo-title: De MediaPlayer instellen
title: De MediaPlayer instellen
uuid: 2279e388-6fbc-49a2-8560-218d3d31e1d6
translation-type: tm+mt
source-git-commit: af9b865bc1627a97bf8957b5460ff9b46052a7dc
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 0%

---


# De MediaPlayer{#set-up-the-mediaplayer} instellen

Een MediaPlayer-object kapselt het gedrag en de functionaliteit van een mediaspeler in.

1. Instantieer een `MediaPlayer` gebruikend het volgende:

   ```js
   var player = new AdobePSDK.MediaPlayer();
   ```

1. Een `MediaPlayerView`-instantie maken:

   ```js
   var view = new AdobePSDK.MediaPlayerView(container);
   ```

   waarbij `container` het doel `div` element is dat uw `HTMLMediaElement` bevat.

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

1. Koppel uw `MediaPlayerView`-instantie aan uw `MediaPlayer`-instantie:

   ```js
   player.view = view;
   ```

1. Koppel de aangepaste besturingselementen `div`-element aan uw MediaPlayer-instantie.

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

De instantie `MediaPlayer` is nu beschikbaar en correct geconfigureerd om video-inhoud weer te geven op het apparaatscherm.
