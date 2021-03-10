---
description: Registreer de juiste gebeurtenislisteners om meldingen over tijdlijnupdates te ontvangen.
title: Listeners toevoegen voor TimelineUpdatedEvent
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 0%

---


# Voeg luisteraars voor TimelineUpdatedEvent{#add-listeners-for-timelineupdatedevent} toe

Registreer de juiste gebeurtenislisteners om meldingen over tijdlijnupdates te ontvangen.

Elke keer dat de tijdlijn wordt bijgewerkt, verzendt `MediaPlayer` `AdobePSDK.TimelineEvent` met type `AdobePSDK.PSDKEventType.TIMELINE_UPDATED`.
1. Voer de aangewezen luisteraars uit.

   ```js
   function onTimelineUpdatedEvent(event) { 
       var timelineMarkers = event.timeline.timelineMarkers; 
       //add code to remove old timeline markers from scrub-bar. 
       var range = player.playbackRange; 
       //iterate through the list of timelineMarkers 
       for(var i = 0; i < timelineMarkers.length; i++) 
       { 
           var markerLocalTime = timelineMarkers[i].localRange.begin; 
           var markerVirtualTime = timelineMarkers[i].virtualRange.begin; 
           var duration = timelineMarkers[i].duration; 
        // add code to draw a particular marker on scrub-bar 
       }      
   }
   ```

1. Registreer de gebeurtenislisteners.

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.TIMELINE_UPDATED,  
       onTimelineUpdatedEvent);
   ```

