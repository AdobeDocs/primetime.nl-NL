---
description: TVSDK verzendt gebeurtenissen/meldingen in de over het algemeen verwachte reeksen. De speler kan handelingen implementeren op basis van gebeurtenissen in de verwachte volgorde.
title: Volgorde van afspeelgebeurtenissen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---


# Volgorde van afspeelgebeurtenissen{#order-of-playback-events}

TVSDK verzendt gebeurtenissen/meldingen in de over het algemeen verwachte reeksen. De speler kan handelingen implementeren op basis van gebeurtenissen in de verwachte volgorde.

<!--<a id="section_6E34A6C7936245D88DEB3315DA64598B"></a>-->

In de volgende voorbeelden wordt de volgorde van bepaalde gebeurtenissen getoond, waaronder afspeelgebeurtenissen.

* Wanneer het laden van een mediabron via `MediaPlayer.replaceCurrentResource` is voltooid, is de volgorde van gebeurtenissen:

   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` met status  `MediaPlayerStatus.INITIALIZING`

   * `MediaPlayerItemEvent.ITEM_CREATED`
   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` met status  `MediaPlayerStatus.INITIALIZED`

* Bij het voorbereiden op afspelen via `MediaPlayer.prepareToPlay` is de volgorde van gebeurtenissen:

   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` met status  `MediaPlayerStatus.PREPARING`

   * `TimelineEvent.TIMELINE_UPDATED` als er advertenties zijn ingevoegd
   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` met status  `MediaPlayerStatus.PREPARED`

* Voor live/lineaire streams, tijdens het afspelen terwijl het afspeelvenster vordert en er extra mogelijkheden worden opgelost, is de volgorde van gebeurtenissen:

   * `MediaPlayerItemEvent.ITEM_UPDATED`
   * `TimelineEvent.TIMELINE_UPDATED` als er advertenties zijn ingevoegd

<!--<a id="section_76C13548AF934868B70757CA5489E516"></a>-->

In het volgende voorbeeld wordt een typische progressie van gebeurtenissen getoond:

```
mediaPlayer.addEventListener(MediaPlayerItemEvent.ITEM_CREATED, onItemCreated); 
public function onItemCreated(event:MediaPlayerItemEvent):void { 
    var item:MediaPlayerItem = event.item; 
    ... 
} 
mediaPlayer.addEventListener(MediaPlayerItemEvent.ITEM_UPDATED, onItemUpdated); 
public function onItemUpdated(event:MediaPlayerItemEvent):void { 
    var item:MediaPlayerItem = event.item; 
    ... 
} 
mediaPlayer.addEventListener(MediaPlayerStatusChangeEvent.STATUS_CHANGED,  
                             onStatusChanged); 
public function onStatusChanged(event:MediaPlayerStatusChangeEvent):void { 
    switch(event.status){ 
        case MediaPlayerStatus.INITIALIZING: 
        case MediaPlayerStatus.INITIALIZED: 
        ... 
    } 
    ... 
} 
mediaPlayer.addEventListener(TimeChangeEvent.TIME_CHANGED, onTimeChanged); 
public function onTimeChanged(event:TimeChangeEvent):void { 
    var timeInMilliseconds:Number = event.time; 
    ... 
}
```

