---
description: Browser-TVSDK ondersteunt momenteel het afspelen van streams waarbij manifesten en fragmenten geen extensies bevatten.
title: Uitbreidbare stromen
exl-id: ef81bfd2-2bfa-4ff7-b826-fd80802b3c07
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# Uitbreidbare stromen{#extensionless-streams}

Browser-TVSDK ondersteunt momenteel het afspelen van streams waarbij manifesten en fragmenten geen extensies bevatten.

## Fragmentniveau {#section_0E035129501D4A77BBC14192D8A53A86}

Browser TVSDK ontleedt de eerste bytes van de reactie om het inhoudstype van fragmenten zonder extensie te ontdekken. Als geen geldig inhoudstype wordt ontdekt, zal Browser TVSDK een fout werpen.

## Manifestniveau {#section_AAD9EBAC883D4CC3A0133A45B555EECF}

Browser TVSDK gebruikt de `mediaResource.resourceType` parameter die wordt doorgegeven in het dialoogvenster `replaceCurrentResource` methode om het inhoudstype van manifest-URL te detecteren. Zie voor meer informatie de `AdobePSDK.MediaPlayer` klasse.

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

Indien `resourceType` wordt niet verstrekt, bepaalt het Kader UI het middeltype van middel URL uitbreiding, die dan wordt overgegaan tot `replaceCurrentResource` methode.

>[!TIP]
>
>Voor manifest zonder uitbreiding, zorg ervoor dat `resourceType` wordt altijd overgegaan terwijl het laden van een middel in het Kader UI.
