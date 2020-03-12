---
description: 'null'
seo-description: 'null'
seo-title: Een basisspeler maken met behulp van het UI-framework
title: Een basisspeler maken met behulp van het UI-framework
uuid: d1a82dbb-1c05-4d0c-b6bc-e07cbede93cb
translation-type: tm+mt
source-git-commit: 4102780d0c7d0b96d120c1c2b3d14c47bc1b0e6f

---


# Een basisspeler maken met behulp van het UI-framework{#create-a-basic-player-using-the-ui-framework}

Een basisspeler maken met het UI-framework:

1. Maak een `<div>` voor de spelerinstantie.

   Bijvoorbeeld:

   ```
   <div id="video1" > 
    </div>
   ```

1. Laad de speler.

   ```js
   <script> 
       (function(){ 
           var player = ptp.videoPlayer('#video1'); 
       })(); 
   </script>
   ```

   Wanneer de speler wordt gecreeerd, wordt het gespecificeerde `<div>` element gegeven een CSS klasse van `ptp-main-video-div-style`. Het resulterende DOM ziet er ongeveer als volgt uit:

   ```
   <div id="video1" class="ptp-main-video-div-style"> 
       <video class="vp-video-element"></video> 
   </div>
   ```

1. Voeg een controle UI toe.

   Voeg bijvoorbeeld een besturingsbalk toe die wordt weergegeven wanneer de muisaanwijzer op de speler wordt geplaatst:

   ```js
   <script> 
       (function(){ 
           function myControlBarBehavior(element, configuration, player) { 
               return ptp.controlBarBehavior(element, configuration, player); 
           } 
           var player = ptp.videoPlayer('#video1', { 
               controlBar: { 
                   behavior: myControlBarBehavior, 
                   classNames: 'ptp-control-bar my_control_bar' 
               } 
           }); 
       })(); 
   </script>
   ```

   Het resulterende DOM ziet er als volgt uit:

   ```
   <div id="video1" class="ptp-main-video-div-style"> 
       <div class="ptp-control-bar my_control_bar"></div> 
       <video class="vp-video-element"></video> 
   </div>
   ```

Het object dat door het aanroepen wordt geretourneerd, `ptp.videoPlayer()` biedt een gedrag dat de API voor de TVSDK-mediaspeler omsluit en programmatische controle over het afspelen mogelijk maakt. Wanneer u de instantie van de mediaspeler aanroept, wordt de gebruikersinterface automatisch bijgewerkt op basis van gebeurtenissen die door de mediaspeler zijn geactiveerd:

```js
<script> 
    (function(){ 
        var player = ptp.videoPlayer('#video1'); 
        player.loadResource( 'sample.mp4' ); 
    })(); 
</script>
```
