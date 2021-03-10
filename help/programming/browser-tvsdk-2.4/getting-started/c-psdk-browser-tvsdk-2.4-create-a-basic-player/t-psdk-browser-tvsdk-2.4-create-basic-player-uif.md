---
title: Een basisspeler maken met behulp van het UI-framework
description: Een basisspeler maken met behulp van het UI-framework
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 1%

---


# Creeer een basisspeler gebruikend het Kader UI{#create-a-basic-player-using-the-ui-framework}

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

Het object dat wordt geretourneerd door het aanroepen van `ptp.videoPlayer()`, biedt een gedrag dat de TVSDK-mediaspeler-API omsluit en programmatische controle over het afspelen mogelijk maakt. Wanneer u de instantie van de mediaspeler aanroept, wordt de gebruikersinterface automatisch bijgewerkt op basis van gebeurtenissen die door de mediaspeler zijn geactiveerd:

```js
<script> 
    (function(){ 
        var player = ptp.videoPlayer('#video1'); 
        player.loadResource( 'sample.mp4' ); 
    })(); 
</script>
```
