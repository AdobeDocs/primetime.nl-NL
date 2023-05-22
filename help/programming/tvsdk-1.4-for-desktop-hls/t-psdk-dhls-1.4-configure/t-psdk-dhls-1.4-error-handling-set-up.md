---
description: Eén locatie instellen om fouten af te handelen.
title: Foutafhandeling instellen
exl-id: ce4a2954-0166-43af-afdf-0aa24659f1ae
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '99'
ht-degree: 0%

---

# Foutafhandeling instellen{#set-up-error-handling}

Eén locatie instellen om fouten af te handelen.

1. Een gebeurteniscallback-functie implementeren voor `MediaPlayerStatusChangeEvent.STATUS_CHANGED`.

   TVSDK geeft gebeurtenisinformatie door, zoals een `MediaPlayerStatusChangeEvent` object.
1. In callback, wanneer de status van de gebeurtenisparameter is `MediaPlayerStatus.ERROR`, biedt logica voor de afhandeling van alle fouten.
1. Nadat de fout is afgehandeld, stelt u de `MediaPlayer` een nieuwe mediabron te laden of te gebruiken.

   Wanneer de `MediaPlayer` Het object bevindt zich in de status ERROR. Deze status kan pas worden afgesloten als u de status opnieuw instelt `MediaPlayer` object (via de `MediaPlayer.reset` methode) of laad een nieuwe mediabron ( `MediaPlayer.replaceCurrentItem`).

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
