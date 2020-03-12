---
description: Eén locatie instellen om fouten af te handelen.
seo-description: Eén locatie instellen om fouten af te handelen.
seo-title: Foutafhandeling instellen
title: Foutafhandeling instellen
uuid: a3182fce-85ac-4dad-bdb3-f9bfbdb2c62d
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Foutafhandeling instellen{#set-up-error-handling}

Eén locatie instellen om fouten af te handelen.

1. Hiermee wordt een callback-functie voor gebeurtenissen geïmplementeerd `MediaPlayerEvent.STATUS_CHANGED`.

   TVSDK geeft gebeurtenisinformatie, zoals een `MediaPlayerStatusChangeEvent` object, door.
1. In callback, wanneer de teruggekeerde staat is `MediaPlayerState.ERROR`, verstrek logica om alle fouten te behandelen.
1. Nadat de fout is afgehandeld, herstelt u het `MediaPlayer` object of laadt u een nieuwe mediabron.

   Wanneer de foutstatus van het `MediaPlayer` object is hersteld, blijft deze status actief totdat u het opnieuw instelt met de `MediaPlayer.reset` methode.

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

