---
description: U kunt visuele instellingen configureren om de gebruiker te laten weten dat de inhoud wordt gebufferd.
seo-description: U kunt visuele instellingen configureren om de gebruiker te laten weten dat de inhoud wordt gebufferd.
seo-title: Bufferen
title: Bufferen
uuid: da9498ee-c736-4093-97a2-250d3ad56d49
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 2%

---


# Buffering{#buffering}

U kunt visuele instellingen configureren om de gebruiker te laten weten dat de inhoud wordt gebufferd.

Luister naar `AdobePSDK.PSDKEventType.BUFFERING_BEGIN`- en `AdobePSDK.PSDKEventType.BUFFERING_END`-gebeurtenissen. Bijvoorbeeld:

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

