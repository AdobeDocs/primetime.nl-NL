---
description: Eén locatie instellen om fouten af te handelen.
seo-description: Eén locatie instellen om fouten af te handelen.
seo-title: Foutafhandeling instellen
title: Foutafhandeling instellen
uuid: a3182fce-85ac-4dad-bdb3-f9bfbdb2c62d
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 2%

---


# Foutafhandeling instellen{#set-up-error-handling}

Eén locatie instellen om fouten af te handelen.

1. Voer een gebeurteniscallback functie voor `MediaPlayerEvent.STATUS_CHANGED` uit.

   TVSDK geeft gebeurtenisinformatie door, zoals een `MediaPlayerStatusChangeEvent`-object.
1. In callback, wanneer de teruggekeerde staat `MediaPlayerState.ERROR` is, verstrek logica om alle fouten te behandelen.
1. Nadat de fout is afgehandeld, herstelt u het `MediaPlayer`-object of laadt u een nieuwe mediabron.

   Wanneer het `MediaPlayer` voorwerp in de foutenstaat is, blijft het in die staat tot u het terugstelt gebruikend de `MediaPlayer.reset` methode.

<!--<a id="example_49FF225E92EA494AA06B2E5F26101F4C"></a>-->

Bijvoorbeeld:

```java
mediaPlayer.addEventListener( 
  MediaPlayerEvent.STATUS_CHANGED, new StatusChangedEventListener() { 
    @Override 
    public void onStatusChanged(MediaPlayerStatusChangeEvent event) { 
        if (event.getStatus() == MediaPlayerStatus.ERROR) { 
            // handle TVSDK error here 
        } 
    } 
});
```

