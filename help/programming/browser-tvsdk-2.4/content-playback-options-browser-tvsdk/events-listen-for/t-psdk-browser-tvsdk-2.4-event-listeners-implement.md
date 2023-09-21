---
description: Met gebeurtenishandlers kan Browser-TVSDK reageren op gebeurtenissen.
title: Gebeurtenislisteners en callbacks implementeren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 0%

---

# Gebeurtenislisteners en callbacks implementeren{#implement-event-listeners-and-callbacks}

Met gebeurtenishandlers kan Browser-TVSDK reageren op gebeurtenissen.

Wanneer een gebeurtenis voorkomt, roept het de gebeurtenismechanisme van Browser TVSDK uw geregistreerde gebeurtenismanager aan en gaat de gebeurtenisinformatie tot de manager over.

Uw toepassing moet gebeurtenislisteners implementeren voor Browser-TVSDK-gebeurtenissen die van invloed zijn op uw toepassing.

1. Bepaal voor welke gebeurtenissen uw toepassing moet luisteren.

   * **Vereiste gebeurtenissen**: Luister naar alle afspeelgebeurtenissen.

     >[!IMPORTANT]
     >
     >De afspeelgebeurtenis `STATUS_CHANGED` bevat de status van de speler, inclusief fouten. Een van de staten kan de volgende stap van de speler beïnvloeden.

   * **Andere gebeurtenissen**: Optioneel, afhankelijk van uw toepassing.

     Als u bijvoorbeeld reclame in het afspelen opneemt, luistert u naar alles `AdBreakPlaybackEvent` en `AdPlaybackEvent` gebeurtenissen.

1. Implementeer gebeurtenislisteners voor elke gebeurtenis.

   Browser TVSDK keert parameterwaarden aan uw gebeurtenis-luisteraarcallbacks terug. Deze waarden bieden relevante informatie over de gebeurtenis die u in de listeners kunt gebruiken om de juiste handelingen uit te voeren.

   Bijvoorbeeld:

   * Type gebeurtenis: `AdobePSDK.PSDKEventType.STATUS_CHANGED`
   * Event, eigenschap: `MediaPlayerStatus.<event>` gebruikt als volgt:

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

1. Registreer uw callback luisteraars met `MediaPlayer` object gebruiken `MediaPlayer.addEventListener`.

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED,  
                                    onStatusChange);
   ```
