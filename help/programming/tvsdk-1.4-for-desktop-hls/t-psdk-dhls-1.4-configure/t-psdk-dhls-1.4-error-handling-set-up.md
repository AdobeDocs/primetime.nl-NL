---
description: Eén locatie instellen om fouten af te handelen.
seo-description: Eén locatie instellen om fouten af te handelen.
seo-title: Foutafhandeling instellen
title: Foutafhandeling instellen
uuid: ff56180d-aa74-4b7c-a24c-e536d874c2e6
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Foutafhandeling instellen{#set-up-error-handling}

Eén locatie instellen om fouten af te handelen.

1. Hiermee wordt een callback-functie voor gebeurtenissen geïmplementeerd `MediaPlayerStatusChangeEvent.STATUS_CHANGED`.

   TVSDK geeft gebeurtenisinformatie, zoals een `MediaPlayerStatusChangeEvent` object, door.
1. Wanneer in de callback de status van de gebeurtenisparameter is, `MediaPlayerStatus.ERROR`moet u logica opgeven om alle fouten af te handelen.
1. Nadat de fout is afgehandeld, herstelt u het `MediaPlayer` object of laadt u een nieuwe mediabron.

   Wanneer het `MediaPlayer` object de status ERROR heeft, kan deze status pas worden afgesloten wanneer u het `MediaPlayer` object opnieuw instelt (via de `MediaPlayer.reset` methode) of een nieuwe mediabron laadt ( `MediaPlayer.replaceCurrentItem`).

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

