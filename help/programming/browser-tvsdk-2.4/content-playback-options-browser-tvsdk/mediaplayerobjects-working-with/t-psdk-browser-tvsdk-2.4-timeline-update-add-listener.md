---
description: Registreer de juiste gebeurtenislisteners om meldingen over tijdlijnupdates te ontvangen.
title: Listeners toevoegen voor TimelineUpdatedEvent
exl-id: 7b55beb5-fd84-4144-8d02-bbd998f99e3a
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 0%

---

# Listeners toevoegen voor TimelineUpdatedEvent{#add-listeners-for-timelineupdatedevent}

Registreer de juiste gebeurtenislisteners om meldingen over tijdlijnupdates te ontvangen.

Telkens wanneer de tijdlijn wordt bijgewerkt, wordt `MediaPlayer` verzendingen `AdobePSDK.TimelineEvent` met type `AdobePSDK.PSDKEventType.TIMELINE_UPDATED`.
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
