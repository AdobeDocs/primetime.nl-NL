---
description: U kunt een beschrijving verkrijgen van de tijdlijn die is gekoppeld aan het geselecteerde item dat door TVSDK wordt afgespeeld. Dit is vooral handig wanneer uw toepassing een aangepast scrub-bar besturingselement weergeeft waarin de inhoudssecties worden geïdentificeerd die overeenkomen met advertentie-inhoud.
seo-description: U kunt een beschrijving verkrijgen van de tijdlijn die is gekoppeld aan het geselecteerde item dat door TVSDK wordt afgespeeld. Dit is vooral handig wanneer uw toepassing een aangepast scrub-bar besturingselement weergeeft waarin de inhoudssecties worden geïdentificeerd die overeenkomen met advertentie-inhoud.
seo-title: De afspeeltijdlijn controleren
title: De afspeeltijdlijn controleren
uuid: d0fe7926-9b9a-4203-a1c7-e57ba25b882e
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# De afspeeltijdlijn controleren {#inspect-the-playback-timeline}

U kunt een beschrijving verkrijgen van de tijdlijn die is gekoppeld aan het geselecteerde item dat door TVSDK wordt afgespeeld. Dit is vooral handig wanneer uw toepassing een aangepast scrub-bar besturingselement weergeeft waarin de inhoudssecties worden geïdentificeerd die overeenkomen met advertentie-inhoud.

Hier ziet u een voorbeeldimplementatie die u kunt zien in de volgende schermafbeelding.  ![](assets/inspect-playback.jpg){width=&quot;368.641pt&quot;}

1. Open het `Timeline` object in de `MediaPlayer` toepassing met de `getTimeline()` methode.

   De `Timeline` klasse omvat de informatie die verwant is aan de inhoud van de chronologie die met het media punt wordt geassocieerd dat momenteel door de `MediaPlayer` instantie wordt geladen. De `Timeline` klasse biedt toegang tot een alleen-lezen weergave van de onderliggende tijdlijn. De `Timeline` klasse biedt een methode getter die een iterator door een lijst met `TimelineMarker` objecten biedt.

1. Doorloop de lijst met geretourneerde gegevens `TimelineMarkers` en gebruik deze om uw tijdlijn te implementeren.

       Een object TimelineMarker bevat twee gegevens:
   
   * Positie van het markeerteken op de tijdlijn (in milliseconden)
   * Duur van het markeerteken op de tijdlijn (in milliseconden)

1. Luister naar de `MediaPlayerEvent.TIMELINE_UPDATED` gebeurtenis op de `MediaPlayer` instantie en implementeer de `TimelineUpdatedEventListener.onTimelineUpdated()` callback.

   Het `Timeline` object kan de toepassing informeren over wijzigingen die zich in de afspeeltijdlijn kunnen voordoen door de `OnTimelineUpdated` listener aan te roepen.

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
