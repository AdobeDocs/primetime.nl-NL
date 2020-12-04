---
description: Eén locatie instellen om fouten af te handelen.
seo-description: Eén locatie instellen om fouten af te handelen.
seo-title: Foutafhandeling instellen
title: Foutafhandeling instellen
uuid: ff56180d-aa74-4b7c-a24c-e536d874c2e6
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 1%

---


# Foutafhandeling instellen{#set-up-error-handling}

Eén locatie instellen om fouten af te handelen.

1. Voer een gebeurteniscallback functie voor `MediaPlayerStatusChangeEvent.STATUS_CHANGED` uit.

   TVSDK geeft gebeurtenisinformatie door, zoals een `MediaPlayerStatusChangeEvent`-object.
1. Wanneer in de callback de status van de gebeurtenisparameter `MediaPlayerStatus.ERROR` is, levert u logica op om alle fouten af te handelen.
1. Nadat de fout is afgehandeld, herstelt u het `MediaPlayer`-object of laadt u een nieuwe mediabron.

   Wanneer het `MediaPlayer` voorwerp in de FOUT staat is, kan het niet deze staat weggaan tot u of het `MediaPlayer` voorwerp (via de `MediaPlayer.reset` methode) terugstelt of een nieuwe media middel ( `MediaPlayer.replaceCurrentItem`) laadt.

<!--<a id="example_49FF225E92EA494AA06B2E5F26101F4C"></a>-->

Bijvoorbeeld:

```
mediaPlayer.addEventListener(MediaPlayerStatusChangeEvent.STATUS_CHANGED,  
                             onStatusChanged); 
 
private void onStatusChanged(event:MediaPlayerStatusChangeEvent):void { 
    if (event.status == MediaPlayerStatus.ERROR) { 
        var error:MediaError = event.error; 
        // handle TVSDK error here 
    } 
} 
```

