---
description: U kunt één locatie instellen om fouten af te handelen.
title: Foutafhandeling instellen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 0%

---

# Foutafhandeling instellen {#set-up-error-handling}

U kunt één locatie instellen om fouten af te handelen.

1. Een gebeurteniscallback-functie implementeren voor `MediaPlayerEvent.STATUS_CHANGED`.

   TVSDK geeft gebeurtenisinformatie door, zoals een `MediaPlayerStatusChangeEvent` object.
1. In callback, wanneer de teruggekeerde status is `MediaPlayerStatus.ERROR`, biedt logica voor de afhandeling van alle fouten.
1. Nadat de fout is afgehandeld, stelt u de `MediaPlayer` een nieuwe mediabron te laden of te gebruiken.

   Wanneer de `MediaPlayer` -object bevindt zich in de foutstatus en blijft deze status behouden totdat u het opnieuw instelt met de functie `MediaPlayer.reset` methode.

<!--<a id="example_E74BB605ED08450295B8902F1E4BB8F5"></a>-->

Bijvoorbeeld:

```java
mediaPlayer.addEventListener(MediaPlayerEvent.STATUS_CHANGED,  
  new StatusChangeEventListener() { 
    @Override 
    public void onStatusChanged(MediaPlayerStatusChangeEvent event) { 
        if (event.getStatus() == MediaPlayerStatus.ERROR) { 
        // handle TVSDK error here 
        } 
    } 
});
```
