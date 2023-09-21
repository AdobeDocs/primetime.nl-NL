---
description: Wanneer uw afspelen reclame bevat, verzendt Browser-TVSDK gebeurtenissen/meldingen in de over het algemeen verwachte reeksen. De speler kan handelingen implementeren op basis van gebeurtenissen in de verwachte volgorde.
title: Volgorde van reclameevenementen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---

# Volgorde van reclameevenementen{#order-of-advertising-events}

Wanneer uw afspelen reclame bevat, verzendt Browser-TVSDK gebeurtenissen/meldingen in de over het algemeen verwachte reeksen. De speler kan handelingen implementeren op basis van gebeurtenissen in de verwachte volgorde.

<!--<a id="section_69E3CCBC57BB48399799876E83908348"></a>-->

Bij het afspelen van advertenties is de volgorde van gebeurtenissen:

* `AdobePSDK.PSDKEventType.AD_BREAK_STARTED`
* Het volgende wordt verzonden voor elke advertentie in het ad-einde:

   * `AdobePSDK.PSDKEventType.AD_STARTED`
   * `AdobePSDK.PSDKEventType.AD_PROGRESS` (meerdere keren tijdens het afspelen van een advertentie)
   * `AdobePSDK.PSDKEventType.AD_COMPLETED`

* `AdobePSDK.PSDKEventType.AD_BREAK_COMPLETED`

In het volgende voorbeeld ziet u een doorsnee progressie van gebeurtenissen voor het afspelen van advertenties:

```js
player.addEventListener(AdobePSDK.PSDKEventType.AD_BREAK_STARTED, onAdbreakStarted); 
player.addEventListener(AdobePSDK.PSDKEventType.AD_STARTED, onAdStarted); 
player.addEventListener(AdobePSDK.PSDKEventType.AD_PROGRESS, onAdProgress); 
player.addEventListener(AdobePSDK.PSDKEventType.AD_COMPLETED, onAdCompleted); 
player.addEventListener(AdobePSDK.PSDKEventType.AD_BREAK_COMPLETED, onAdbreakCompleted);
```
