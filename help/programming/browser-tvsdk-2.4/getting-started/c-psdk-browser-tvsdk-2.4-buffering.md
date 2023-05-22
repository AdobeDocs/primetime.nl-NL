---
description: U kunt visuele instellingen configureren om de gebruiker te laten weten dat de inhoud wordt gebufferd.
title: Bufferen
exl-id: 1b2f32b4-1839-4256-82d6-b262569aa751
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '56'
ht-degree: 0%

---

# Bufferen{#buffering}

U kunt visuele instellingen configureren om de gebruiker te laten weten dat de inhoud wordt gebufferd.

Luisteren naar `AdobePSDK.PSDKEventType.BUFFERING_BEGIN` en `AdobePSDK.PSDKEventType.BUFFERING_END` gebeurtenissen. Bijvoorbeeld:

```js
player.addEventListener(AdobePSDK.PSDKEventType.BUFFERING_BEGIN,  
                        function (event) { 
                            buffering = true; 
                            // add buffering layer 
                        }); 
  
player.addEventListener(AdobePSDK.PSDKEventType.BUFFERING_END,  
                        function (event) { 
                           buffering = false; 
                           // remove buffering layer 
                        });
```

Het UI-framework biedt een standaardimplementatie voor het bufferen van overlaygedrag, die kan worden uitgebreid zoals hieronder wordt weergegeven:

```js
// Using UI Framework 
function myBufferingOverlayBehavior (element, configuration, player, localize, baseLog) { 
    return ptp.bufferingOverlayBehavior(element, configuration, player, localize, baseLog); 
} 
var playerWrapper = ptp.videoPlayer('.videoDiv', { 
    player: { 
        mediaResource:'Specify Resource URL', 
        bufferingOverlay: { 
            behavior: myBufferingOverlayBehavior, 
            classNames: 'ptp-buffering-overlay my_buffering_overlay_bar' 
        } 
    } 
 
}); 
```

Zo ziet het DOM-resultaat eruit:

```
<div id=" videoDiv" class="ptp-root-element"> 
<div name="videoPlayer" value="videoPlayer" class="ptp-main-video-div-style"> 
<div name="bufferingOverlay" value="bufferingOverlay" class="ptp-buffering-overlay my_buffering_overlay_bar'"></div> 
</div> 
</div> 
```
