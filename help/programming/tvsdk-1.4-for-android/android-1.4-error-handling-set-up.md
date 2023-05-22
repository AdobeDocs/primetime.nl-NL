---
description: Eén locatie instellen om fouten af te handelen.
title: Foutafhandeling instellen
exl-id: 2d0e0d08-d932-4b6e-8f95-494a2e666827
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 0%

---

# Foutafhandeling instellen{#set-up-error-handling}

Eén locatie instellen om fouten af te handelen.

1. Een gebeurteniscallback-functie implementeren voor `MediaPlayerEvent.STATUS_CHANGED`.

   TVSDK geeft gebeurtenisinformatie door, zoals een `MediaPlayerStatusChangeEvent` object.
1. In callback, wanneer de teruggekeerde staat is `MediaPlayerState.ERROR`, biedt logica voor de afhandeling van alle fouten.
1. Nadat de fout is afgehandeld, stelt u de `MediaPlayer` een nieuwe mediabron te laden of te gebruiken.

   Wanneer de `MediaPlayer` Het object bevindt zich in de foutstatus en blijft in die status totdat u het opnieuw instelt met de opdracht `MediaPlayer.reset` methode.

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
