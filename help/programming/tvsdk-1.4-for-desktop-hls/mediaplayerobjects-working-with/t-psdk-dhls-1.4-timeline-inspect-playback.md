---
description: U kunt een beschrijving verkrijgen van de tijdlijn die is gekoppeld aan het geselecteerde item dat door TVSDK wordt afgespeeld. Dit is vooral handig wanneer uw toepassing een aangepast scrub-bar besturingselement weergeeft waarin de inhoudssecties worden geïdentificeerd die overeenkomen met advertentie-inhoud.
seo-description: U kunt een beschrijving verkrijgen van de tijdlijn die is gekoppeld aan het geselecteerde item dat door TVSDK wordt afgespeeld. Dit is vooral handig wanneer uw toepassing een aangepast scrub-bar besturingselement weergeeft waarin de inhoudssecties worden geïdentificeerd die overeenkomen met advertentie-inhoud.
seo-title: De afspeeltijdlijn controleren
title: De afspeeltijdlijn controleren
uuid: 2f903493-2d88-4af2-ac71-36300b49735b
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# De afspeeltijdlijn controleren{#inspect-the-playback-timeline}

U kunt een beschrijving verkrijgen van de tijdlijn die is gekoppeld aan het geselecteerde item dat door TVSDK wordt afgespeeld. Dit is vooral handig wanneer uw toepassing een aangepast scrub-bar besturingselement weergeeft waarin de inhoudssecties worden geïdentificeerd die overeenkomen met advertentie-inhoud.

Hier ziet u een voorbeeldimplementatie die u kunt zien in de volgende schermafbeelding.
<!--<a id="fig_6D9FB3764F3947A38B8E7726187BD461"></a>-->

![](assets/inspect-playback.jpg){width=&quot;368.641pt&quot;}

1. Open het `Timeline` object in de `MediaPlayer` toepassing met de `get` methode.

   De `Timeline` klasse omvat de informatie die verwant is aan de inhoud van de chronologie die met het media punt wordt geassocieerd dat momenteel door de `MediaPlayer` instantie wordt geladen. De `Timeline` klasse biedt toegang tot een alleen-lezen weergave van de onderliggende tijdlijn. De `Timeline` klasse biedt een methode getter voor het ophalen van alle geplaatste `TimelineMarker` objecten.

1. Doorloop de lijst met geretourneerde gegevens `TimelineMarkers` en gebruik deze om uw tijdlijn te implementeren.

       Een object TimelineMarker bevat twee gegevens:
   
   * Positie van het markeerteken op de tijdlijn (in milliseconden)
   * Duur van het markeerteken op de tijdlijn (in milliseconden)

<!--<a id="example_BA936629E82B4082A2E2C548E3FC3357"></a>-->

```
// access the timeline object 
var timeline:Timeline = mediaPlayer.timeline; 
 
// iterate through the list of TimelineMarkers 
var markers:Vector.<TimelineMarker> = timeline.timelineMarkers; 
markers.forEach(function(item:TimelineMarker,  
                         index:int,  
                         vector:Vector.<TimelineMarker>):void { 
    
    // the start position of the marker 
    var startPos:Number = item.time; 
 
    // the duration of the marker 
    var duration:Number = item.duration; 
 
    // draw the marker on the scrub-bar 
}
```

