---
description: U kunt een beschrijving verkrijgen van de tijdlijn die is gekoppeld aan het geselecteerde item dat door TVSDK wordt afgespeeld. Dit is vooral handig wanneer uw toepassing een aangepast scrub-bar besturingselement weergeeft waarin de inhoudssecties worden geïdentificeerd die overeenkomen met advertentie-inhoud.
title: De afspeeltijdlijn Inspect
exl-id: 2a12fe28-9a8a-45b7-af05-87c17dd25302
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# De afspeeltijdlijn Inspect {#inspect-the-playback-timeline}

U kunt een beschrijving verkrijgen van de tijdlijn die is gekoppeld aan het geselecteerde item dat door TVSDK wordt afgespeeld. Dit is vooral handig wanneer uw toepassing een aangepast scrub-bar besturingselement weergeeft waarin de inhoudssecties worden geïdentificeerd die overeenkomen met advertentie-inhoud.

Hier ziet u een voorbeeldimplementatie die u kunt zien in de volgende schermafbeelding.  ![](assets/inspect-playback.jpg){width="368.641pt"}

1. Toegang krijgen tot `Timeline` object in het `MediaPlayer` met de `getTimeline()` methode.

   De `Timeline` De klasse omvat de informatie die verwant is aan de inhoud van de chronologie die met het media punt wordt geassocieerd dat momenteel door wordt geladen `MediaPlayer` -instantie. De `Timeline` biedt toegang tot een alleen-lezen weergave van de onderliggende tijdlijn. De `Timeline` klasse biedt een methode getter die een iterator in een lijst met `TimelineMarker` objecten.

1. Doorlopen in de lijst met `TimelineMarkers` en gebruik de geretourneerde informatie om uw tijdlijn te implementeren.

       Een object TimelineMarker bevat twee gegevens:
   
   * Positie van het markeerteken op de tijdlijn (in milliseconden)
   * Duur van het markeerteken op de tijdlijn (in milliseconden)

1. Luister naar de `MediaPlayerEvent.TIMELINE_UPDATED` gebeurtenis op de `MediaPlayer` -instantie, en implementeert de `TimelineUpdatedEventListener.onTimelineUpdated()` callback.

   De `Timeline` object kan uw toepassing informeren over wijzigingen die zich kunnen voordoen in de afspeeltijdlijn door uw `OnTimelineUpdated` listener.

```java
// access the timeline object 
Timeline timeline = mediaPlayer.getTimeline(); 
 
// Iterate through the list of TimelineMarkers 
Iterator<TimelineMarker> iterator = timeline.timelineMarkers(); 
 
while (iterator.hasNext()) { 
    TimelineMarker marker = iterator.next(); 
    // the start position of the marker 
    long startPos = marker.getTime(); 
    // the duration of the marker 
    long duration = marker.getDuration(); 
}
```
