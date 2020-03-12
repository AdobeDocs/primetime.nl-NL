---
description: U kunt één locatie instellen om fouten af te handelen.
seo-description: U kunt één locatie instellen om fouten af te handelen.
seo-title: Foutafhandeling instellen
title: Foutafhandeling instellen
uuid: fde47fa5-5ca5-4be5-a7e7-3227c5e4c670
translation-type: tm+mt
source-git-commit: 21d1eae53cea303221de00765724e787cf6e84ef

---


# Foutafhandeling instellen {#set-up-error-handling}

U kunt één locatie instellen om fouten af te handelen.

1. Hiermee wordt een callback-functie voor gebeurtenissen geïmplementeerd `MediaPlayerEvent.STATUS_CHANGED`.

   TVSDK geeft gebeurtenisinformatie, zoals een `MediaPlayerStatusChangeEvent` object, door.
1. Wanneer de geretourneerde status in de callback is `MediaPlayerStatus.ERROR`, geeft u logica op om alle fouten af te handelen.
1. Nadat de fout is afgehandeld, herstelt u het `MediaPlayer` object of laadt u een nieuwe mediabron.

   Wanneer de foutstatus van het `MediaPlayer` object is ingesteld, blijft deze in die status totdat u het opnieuw instelt met de `MediaPlayer.reset` methode.

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

