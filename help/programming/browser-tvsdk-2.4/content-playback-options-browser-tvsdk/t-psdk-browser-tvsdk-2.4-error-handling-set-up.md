---
description: U kunt één plaats in uw toepassing instellen om fout behandeling in antwoord op de FOUTstatus uit te voeren.
seo-description: U kunt één plaats in uw toepassing instellen om fout behandeling in antwoord op de FOUTstatus uit te voeren.
seo-title: Foutafhandeling instellen
title: Foutafhandeling instellen
uuid: 9e650ea7-86cb-4489-a3fd-80cd2ccef41f
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 2%

---


# Foutafhandeling instellen{#set-up-error-handling}

U kunt één plaats in uw toepassing instellen om fout behandeling in antwoord op de FOUTstatus uit te voeren.

1. Voeg een gebeurtenislistener toe voor `AdobePSDK.MediaPlayerStatusChangeEvent`.

   Bijvoorbeeld:

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED, 
                           onStatusChange);
   ```

1. Wanneer de `event.status` `AdobePSDK.MediaPlayerStatus.ERROR` is in uw gebeurtenislistener, geeft u de logica op om alle fouten af te handelen.
1. Nadat de fout is afgehandeld, herstelt u het `MediaPlayer`-object of laadt u een nieuwe mediabron.

       Wanneer het MediaPlayer-object de status ERROR heeft, kan deze status pas worden afgesloten wanneer u een van de volgende taken uitvoert:
   
   * Herstel het MediaPlayer-object met de methode `MediaPlayer.reset`.
   * Laad een nieuwe media bron door de `MediaPlayer.replaceCurrentResource` methode te gebruiken.

<!--<a id="example_342CA5A8CD7C45BD88233C5BDBB17220"></a>-->

Bijvoorbeeld:

```js
player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED, onStatusChange); 
onStatusChange = function (event) { 
    switch (event.status) { 
        case AdobePSDK.MediaPlayerStatus.ERROR: 
            //handle error 
            break; 
    } 
} 
```

