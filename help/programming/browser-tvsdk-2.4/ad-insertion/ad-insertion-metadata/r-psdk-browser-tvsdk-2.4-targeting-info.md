---
description: In Adobe Primetime en bij de besluitvorming kunt u advertenties op sleutelwaardeparen als doel instellen.
title: Doelgegevens
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '37'
ht-degree: 0%

---

# Doelgegevens{#targeting-information}

In Adobe Primetime en bij de besluitvorming kunt u advertenties op sleutelwaardeparen als doel instellen.

Deze sleutelwaardeparen doorgeven aan Browser TVSDK:

```js
var auditudeSettings = new AdobePSDK.AuditudeSettings(); 
var targetingInfo = new AdobePSDK.Metadata(); 
 
// Add key value pairs to targetingInfo 
targetingInfo.setValue(key1, value1); 
targetingInfo.setValue(key2, value2); 
 
auditudeSettings.targetingInfo = targetingInfo;
```
