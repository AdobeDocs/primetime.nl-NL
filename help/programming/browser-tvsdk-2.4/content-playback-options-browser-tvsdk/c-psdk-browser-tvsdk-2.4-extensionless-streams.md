---
description: Browser-TVSDK ondersteunt momenteel het afspelen van streams waarbij manifesten en fragmenten geen extensies bevatten.
seo-description: Browser-TVSDK ondersteunt momenteel het afspelen van streams waarbij manifesten en fragmenten geen extensies bevatten.
seo-title: Uitbreidbare stromen
title: Uitbreidbare stromen
uuid: c69ba62b-a940-4211-920d-2e559849fd6d
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---


# Extra stromen{#extensionless-streams}

Browser-TVSDK ondersteunt momenteel het afspelen van streams waarbij manifesten en fragmenten geen extensies bevatten.

## Fragmentniveau {#section_0E035129501D4A77BBC14192D8A53A86}

Browser TVSDK ontleedt de eerste bytes van de reactie om het inhoudstype van fragmenten zonder extensie te ontdekken. Als geen geldig inhoudstype wordt ontdekt, zal Browser TVSDK een fout werpen.

## Manifestniveau {#section_AAD9EBAC883D4CC3A0133A45B555EECF}

Browser TVSDK gebruikt de `mediaResource.resourceType` parameter die in `replaceCurrentResource` methode wordt overgegaan om het inhoudstype van manifestURL te ontdekken. Zie de klasse `AdobePSDK.MediaPlayer` voor meer informatie.

In de speler van het Kader UI, kunt u het middeltype in media middel als volgt specificeren:

```js
var playerWrapper = ptp.videoPlayer('.videoDiv', { 
  player: { 
    mediaResource: { 
      resourceUrl:'Specify Resource Url', 
      resourceType: ‘Specify Resource Type. Refer AdobePSDK.MediaResourceType' 
    } 
  } 
}); 
```

Als `resourceType` niet wordt verstrekt, bepaalt het Kader UI het middeltype van middel URL uitbreiding, die dan tot `replaceCurrentResource` methode wordt overgegaan.

>[!TIP]
>
>Voor uitbreiding-minder manifest, zorg ervoor dat `resourceType` altijd wordt overgegaan terwijl het laden van een middel in het Kader UI.

