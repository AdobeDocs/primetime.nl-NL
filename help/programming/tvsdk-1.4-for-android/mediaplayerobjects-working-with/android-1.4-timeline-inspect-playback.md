---
description: U kunt een beschrijving verkrijgen van de tijdlijn die is gekoppeld aan het geselecteerde item dat door TVSDK wordt afgespeeld. Dit is vooral handig wanneer uw toepassing een aangepast scrub-bar besturingselement weergeeft waarin de inhoudssecties worden geïdentificeerd die overeenkomen met advertentie-inhoud.
title: De afspeeltijdlijn Inspect
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---


# De afspeeltijdlijn Inspect{#inspect-the-playback-timeline}

U kunt een beschrijving verkrijgen van de tijdlijn die is gekoppeld aan het geselecteerde item dat door TVSDK wordt afgespeeld. Dit is vooral handig wanneer uw toepassing een aangepast scrub-bar besturingselement weergeeft waarin de inhoudssecties worden geïdentificeerd die overeenkomen met advertentie-inhoud.

Hier ziet u een voorbeeldimplementatie die u kunt zien in de volgende schermafbeelding.  ![](assets/inspect-playback.jpg){width=&quot;368.641pt&quot;}

1. Open het `Timeline`-object in `MediaPlayer` met de methode `getTimeline`.

   Met de klasse `Timeline` wordt de informatie ingekapseld die betrekking heeft op de inhoud van de tijdlijn die is gekoppeld aan het media-item dat momenteel wordt geladen door de instantie `MediaPlayer`. De klasse `Timeline` biedt toegang tot een alleen-lezen weergave van de onderliggende tijdlijn. De klasse `Timeline` biedt een methode getter die een iterator door een lijst met objecten `TimelineMarker` biedt.

1. Doorloop de lijst van `TimelineMarkers` en gebruik de teruggekeerde informatie om uw chronologie uit te voeren.

       Een object TimelineMarker bevat twee gegevens:
   
   * Positie van het markeerteken op de tijdlijn (in milliseconden)
   * Duur van het markeerteken op de tijdlijn (in milliseconden)

1. Voer de luisteraarcallback interface `MediaPlayer.PlaybackEventListener.onTimelineUpdated` uit en registreer het met het `Timeline` voorwerp.

   Het `Timeline`-object kan uw toepassing informeren over wijzigingen die zich in de afspeeltijdlijn kunnen voordoen door uw `OnTimelineUpdated`-listener aan te roepen.

```java
// access the timeline object 
Timeline timeline = mediaPlayer.getTimeline(); 
// iterate through the list of TimelineMarkers 
Iterator<TimelineMarker> iterator = timeline.timelineMarkers(); 
while (iterator.hasNext()) { 
   TimelineMarker marker = iterator.next(); 
   // the start position of the marker 
   long startPos = marker.getTime(); 
   // the duration of the marker 
   long duration = marker.getDuration(); 
}
```

