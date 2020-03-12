---
description: Met gebeurtenishandlers kan Browser-TVSDK reageren op gebeurtenissen.
seo-description: Met gebeurtenishandlers kan Browser-TVSDK reageren op gebeurtenissen.
seo-title: Gebeurtenislisteners en callbacks implementeren
title: Gebeurtenislisteners en callbacks implementeren
uuid: 63f62c60-505e-4f83-bc0d-58895d85a75a
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Gebeurtenislisteners en callbacks implementeren{#implement-event-listeners-and-callbacks}

Met gebeurtenishandlers kan Browser-TVSDK reageren op gebeurtenissen.

Wanneer een gebeurtenis voorkomt, roept het de gebeurtenismechanisme van Browser TVSDK uw geregistreerde gebeurtenismanager aan en gaat de gebeurtenisinformatie tot de manager over.

Uw toepassing moet gebeurtenislisteners implementeren voor Browser-TVSDK-gebeurtenissen die van invloed zijn op uw toepassing.

1. Bepaal voor welke gebeurtenissen uw toepassing moet luisteren.

   * **Vereiste gebeurtenissen**: Luister naar alle afspeelgebeurtenissen.

      >[!IMPORTANT]
      >
      >De afspeelgebeurtenis `STATUS_CHANGED` geeft de spelerstatus aan, inclusief fouten. Een van de staten kan de volgende stap van de speler beïnvloeden.

   * **Andere gebeurtenissen**: Optioneel, afhankelijk van uw toepassing.

      Als u bijvoorbeeld reclame in het afspelen opneemt, luistert u naar alle gebeurtenissen `AdBreakPlaybackEvent` `AdPlaybackEvent` en gebeurtenissen.

1. Implementeer gebeurtenislisteners voor elke gebeurtenis.

   Browser TVSDK keert parameterwaarden aan uw gebeurtenis-luisteraarcallbacks terug. Deze waarden bieden relevante informatie over de gebeurtenis die u in de listeners kunt gebruiken om de juiste handelingen uit te voeren.

   Bijvoorbeeld:

   * Type gebeurtenis: `AdobePSDK.PSDKEventType.STATUS_CHANGED`
   * Event, eigenschap: Op deze manier `MediaPlayerStatus.<event>` gebruikt:

```js
player.addEventListener( 
            AdobePSDK.PSDKEventType.STATUS_CHANGED,  
            onStatusChange); 
 
onStatusChange = function (event) { 
 
    switch (event.status) { 
        case AdobePSDK.MediaPlayerStatus.IDLE: 
            console.log("Player Status: IDLE"); 
            break;
```

1. Registreer de callback-listeners met het `MediaPlayer` object `MediaPlayer.addEventListener`.

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED,  
                                    onStatusChange);
   ```
