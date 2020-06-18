---
description: U kunt bijschriften weergeven tijdens het afspelen van video-inhoud.
seo-description: U kunt bijschriften weergeven tijdens het afspelen van video-inhoud.
seo-title: Bijschriften
title: Bijschriften
uuid: 4dedcedc-50e5-4983-bb09-3f316337117e
translation-type: tm+mt
source-git-commit: 9c6a6f0b5ecff78796e37daf9d7bdb9fa686ee0c
workflow-type: tm+mt
source-wordcount: '64'
ht-degree: 3%

---


# Bijschriften{#captions}

U kunt bijschriften weergeven tijdens het afspelen van video-inhoud.

Als u ondertitels wilt afhandelen, moet u de `AdobePSDK.PSDKEventType.CAPTIONS_UPDATED` gebeurtenislistener toevoegen:

```js
... 
player.addEventListener(AdobePSDK.PSDKEventType.CAPTIONS_UPDATED,  
                        onCaptionsUpdateEvent); 
... 
function onCaptionsUpdateEvent (event) { 
  // code to show the captions icon and any settings button. 
<ph>
   For example: 
  var btnCC = document.getElementById("btn_captions"); 
   btnCC.classList.remove("invisible"); 
   
  var btnSettings = document.getElementById("btn_settings"); 
   btnSettings.classList.remove("invisible"); 
 } 
</ph>
```

Het UI-framework biedt een standaardimplementatie voor ondertitels, die kan worden gewijzigd. Gedrag van gesloten bijschriften kan ook worden gewijzigd door het standaardgedrag voor gesloten bijschriften uit te breiden. Bijvoorbeeld:

```js
// Using UI Framework 
var playerWrapper = ptp.videoPlayer(‘.videoDiv', { 
player:{ 
    mediaResource: 'Specify Resource URL', 
    ccStyle: { 
    font:AdobePSDK.TextFormat.CURSIVE, 
    fontColor:AdobePSDK.TextFormat.BRIGHT_WHITE, 
    edgeColor:AdobePSDK.TextFormat.BLUE, 
    backgroundColor:AdobePSDK.TextFormat.BLACK, 
    fillColor:AdobePSDK.TextFormat.BLUE, 
    size:AdobePSDK.TextFormat.MEDIUM, 
    fontOpacity:100, 
    backgroundOpacity:1, 
    fillOpacity:1 
   } 
 } 
 
}); 
```
