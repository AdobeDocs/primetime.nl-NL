---
description: U kunt één locatie instellen om fouten af te handelen.
seo-description: U kunt één locatie instellen om fouten af te handelen.
seo-title: Foutafhandeling instellen
title: Foutafhandeling instellen
uuid: fde47fa5-5ca5-4be5-a7e7-3227c5e4c670
translation-type: tm+mt
source-git-commit: 21d1eae53cea303221de00765724e787cf6e84ef
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 1%

---


# Foutafhandeling instellen {#set-up-error-handling}

U kunt één locatie instellen om fouten af te handelen.

1. Voer een gebeurteniscallback functie voor `MediaPlayerEvent.STATUS_CHANGED` uit.

   TVSDK geeft gebeurtenisinformatie door, zoals een `MediaPlayerStatusChangeEvent`-object.
1. In callback, wanneer de teruggekeerde status `MediaPlayerStatus.ERROR` is, verstrek logica om alle fouten te behandelen.
1. Nadat de fout is afgehandeld, herstelt u het `MediaPlayer`-object of laadt u een nieuwe mediabron.

   Wanneer het `MediaPlayer` voorwerp in de foutenstatus is blijft het in die status tot u het terugstelt gebruikend de `MediaPlayer.reset` methode.

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

