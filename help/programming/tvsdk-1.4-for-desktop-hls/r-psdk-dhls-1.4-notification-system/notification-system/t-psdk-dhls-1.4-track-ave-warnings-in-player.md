---
description: Gebruikend NotificationEvent, kunt u waarschuwingen volgen die van de Adobe VideoMotor (AVE) worden overgegaan.
seo-description: Gebruikend NotificationEvent, kunt u waarschuwingen volgen die van de Adobe VideoMotor (AVE) worden overgegaan.
seo-title: AVE-waarschuwingen bijhouden in uw speler
title: AVE-waarschuwingen bijhouden in uw speler
uuid: 236aee5e-6b1a-4298-9d3b-f33b40416c19
translation-type: tm+mt
source-git-commit: d2b8cb67c54fadb8e0e7d2bdc15e393fdce8550e
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 1%

---


# Houd AVE-waarschuwingen bij in uw speler{#track-ave-warnings-in-your-player}

Gebruikend NotificationEvent, kunt u waarschuwingen volgen die van de Adobe VideoMotor (AVE) worden overgegaan.

Uw speler-app kan afspeelwaarschuwingen en fouten bijhouden die door de AVE zijn gegenereerd, zoals failover- of netwerk-downgebeurtenissen die het afspelen niet stoppen en waarvoor niet noodzakelijkerwijs een actie van uw app nodig is. Hoewel sommige AVE-fouten worden afgehandeld door de TVSDK, fungeert `NotificationEvent` als een algemeen doorvoermechanisme voor AVE-waarschuwingen naar uw toepassingslaag. Na het ontvangen van waarschuwingen van de AVE, zou u kunnen verkiezen om wat actie te voeren, zoals proactief het tegenhouden van playback, het activeren van een rampenplan, het registreren van berichten, etc.

Gebruik de volgende API-elementen om AVE-waarschuwingen in uw speler bij te houden:

**NotificationCode**

```
public final class NotificationCode { 
    /** 
     * Warning message for playback status. 
     */ 
    public static const GENERAL_WARNING:int = 101100; 
}
```

**NotificationEvent**

```
/** 
 * Event dispatched by MediaPlayer when a notification is available 
 * for the current media stream being played. 
 */ 
public class NotificationEvent extends Event { 
    /** 
     * Event dispatched when a new warning has been received for the current item. 
     * 
     * The newly created Notification object can be accessed through  
     * the notification property of this event. 
     */ 
    public static const WARNING_AVAILABLE:String = "warningAvailable"; 
    /** 
     * Helper method for creating NotificationEvent events. 
     * Throws an ArgumentError if the specified ad break is null. 
     * @param notification Associated notification object. 
     * 
     * @return a valid notification event instance. 
     */ 
    public static function create( 
           type:String, notification:Notification):NotificationEvent; 
     /** 
     * Default constructor 
     * Throws an ArgumentError if the specified ad break is null. 
     * @param type           Event type. 
     * @param bubbles        Whether the event can bubble up the display list hierarchy. 
     * @param cancelable     Whether the behavior associated with the event can be prevented. 
     * @param notification   Associated notification object. 
     */ 
    public function NotificationEvent(type:String,  
                                      bubbles:Boolean=false,  
                                      cancelable:Boolean=false,  
                                      notification:Notification= null); 
     /** 
     * The notification associated with this event. 
     */ 
    public function get notification():Notification; 
    /** 
     * @inheritDoc 
     */ 
    public override function clone():Event; 
}
```

Voeg een gebeurtenislistener toe aan de speler om AVE-waarschuwingen af te vangen.

Bijvoorbeeld:

```
var _player:DefaultMediaPlayer = new DefaultMediaPlayer(context); 
_player.addEventListener(NotificationEvent.WARNING_AVAILABLE, onWarningAvailable); 
 
private function onWarningAvailable(event:NotificationEvent):void { 
    var metadata:Metadata = event.notification.metadata; 
    if (metadata != null) { 
        for each (var key:String in metadata.keySet()) { 
            var value:String = metadata.getValue(key); 
            if (!StringUtils.isEmpty(key) && !StringUtils.isEmpty(value)) { 
                _logger.warn("#onWarningAvailable metadata [{0}:{1}]", key, value); 
            } 
        } 
    } 
} 
```

<!--<a id="example_C35262605D394718B40C084B569A5052"></a>-->

Hier volgt een voorbeeld van AVE-waarschuwingen die zijn bijgehouden met `NotificationEvent`:

```
[WARN ] [psdkdemo::PSDKDemo] #onWarningAvailable metadata [resourceType:HLS] 
[WARN ] [psdkdemo::PSDKDemo] #onWarningAvailable metadata [resourceId:0] 
[WARN ] [psdkdemo::PSDKDemo] #onWarningAvailable metadata [runtimeCode:66] 
[WARN ] [psdkdemo::PSDKDemo] #onWarningAvailable metadata [runtimeCodeMessage:SEGMENT_SKIPPED_ON_FAILURE] 
[WARN ] [psdkdemo::PSDKDemo] #onWarningAvailable metadata [eventType:Warning] 
 
<pre>
  [WARN ] [psdkdemo::PSDKDemo] #onWarningAvailable metadata [description:url::= 
   https://xyz.corp.adobe.com/pmp/assets/abc/failover/tc.1.04/content/backup-01/ 
   low-res/main-stream4-4x3-info6.ts,periodIndex::=0, 
   sizeBytes::=0,downloadTime(ms)::=0,mediaDuration(ms)::=0] 
</pre>
```
