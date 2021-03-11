---
description: Eén locatie instellen om fouten af te handelen.
title: Foutafhandeling instellen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '88'
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

