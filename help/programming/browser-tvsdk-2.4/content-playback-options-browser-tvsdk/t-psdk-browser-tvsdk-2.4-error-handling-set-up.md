---
description: U kunt één plaats in uw toepassing instellen om fout behandeling in antwoord op de FOUTstatus uit te voeren.
title: Foutafhandeling instellen
exl-id: c0ce1d80-85d5-4344-9ab0-bd56906421cb
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Foutafhandeling instellen{#set-up-error-handling}

U kunt één plaats in uw toepassing instellen om fout behandeling in antwoord op de FOUTstatus uit te voeren.

1. Een gebeurtenislistener toevoegen voor `AdobePSDK.MediaPlayerStatusChangeEvent`.

   Bijvoorbeeld:

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED, 
                           onStatusChange);
   ```

1. In uw gebeurtenislistener, wanneer de `event.status` is `AdobePSDK.MediaPlayerStatus.ERROR`, geeft u de logica op om alle fouten af te handelen.
1. Nadat de fout is afgehandeld, stelt u de `MediaPlayer` een nieuwe mediabron te laden of te gebruiken.

       Wanneer het MediaPlayer-object de status ERROR heeft, kan deze status pas worden afgesloten wanneer u een van de volgende taken uitvoert:
   
   * Het MediaPlayer-object opnieuw instellen met de opdracht `MediaPlayer.reset` methode.
   * Laad een nieuwe mediabron met de `MediaPlayer.replaceCurrentResource` methode.

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
