---
description: TVSDK verzendt gebeurtenissen/meldingen in de over het algemeen verwachte reeksen. De speler kan handelingen implementeren op basis van gebeurtenissen in de verwachte volgorde.
seo-description: TVSDK verzendt gebeurtenissen/meldingen in de over het algemeen verwachte reeksen. De speler kan handelingen implementeren op basis van gebeurtenissen in de verwachte volgorde.
seo-title: Volgorde van afspeelgebeurtenissen
title: Volgorde van afspeelgebeurtenissen
uuid: 4a9ea66b-a383-46ff-9ab8-983b1dd7f935
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Volgorde van afspeelgebeurtenissen{#order-of-playback-events}

TVSDK verzendt gebeurtenissen/meldingen in de over het algemeen verwachte reeksen. De speler kan handelingen implementeren op basis van gebeurtenissen in de verwachte volgorde.

<!--<a id="section_6E34A6C7936245D88DEB3315DA64598B"></a>-->

In de volgende voorbeelden wordt de volgorde van bepaalde gebeurtenissen getoond, waaronder afspeelgebeurtenissen.

* Wanneer het laden van een mediabron is geslaagd, is de volgorde van gebeurtenissen: `MediaPlayer.replaceCurrentResource`

   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` met status `MediaPlayerStatus.INITIALIZING`

   * `MediaPlayerItemEvent.ITEM_CREATED`
   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` met status `MediaPlayerStatus.INITIALIZED`

* Wanneer u het afspelen voorbereidt, is de volgorde van gebeurtenissen: `MediaPlayer.prepareToPlay`

   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` met status `MediaPlayerStatus.PREPARING`

   * `TimelineEvent.TIMELINE_UPDATED` als er advertenties zijn ingevoegd
   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` met status `MediaPlayerStatus.PREPARED`

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

