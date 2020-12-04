---
description: U kunt opmaak voor Closed Caption opgeven.
seo-description: U kunt opmaak voor Closed Caption opgeven.
seo-title: Voorbeelden van bijschriftopmaak
title: Voorbeelden van bijschriftopmaak
uuid: d55a506a-6662-4252-95f6-4073b2997f3b
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '41'
ht-degree: 0%

---


# Voorbeelden: Bijschriftopmaak{#examples-caption-formatting}

U kunt opmaak voor Closed Caption opgeven.

## Voorbeeld 1: Geef opmaakwaarden expliciet op {#section_BD7B48F3B66D4E9290E1CB2F464E08E4}

```js
// Set CC style. 
var tf = new AdobePSDK.TextFormat( 
      AdobePSDK.TextFormat.FONT_DEFAULT, 
      AdobePSDK.TextFormat.COLOR_DEFAULT, 
      AdobePSDK.TextFormat.COLOR_DEFAULT, 
      AdobePSDK.TextFormat.FONT_EDGE_DEFAULT, 
      AdobePSDK.TextFormat.COLOR_DEFAULT, 
      AdobePSDK.TextFormat.COLOR_DEFAULT, 
      AdobePSDK.TextFormat.SIZE_DEFAULT, 
      AdobePSDK.TextFormat.DEFAULT_OPACITY, 
      AdobePSDK.TextFormat.DEFAULT_OPACITY, 
      AdobePSDK.TextFormat.DEFAULT_OPACITY; 
 mediaPlayer.CCStyle(tf);
```

>[!IMPORTANT]
>
>Browser-TVSDK ondersteunt geen fontrand, vulkleur of vuldekking.

