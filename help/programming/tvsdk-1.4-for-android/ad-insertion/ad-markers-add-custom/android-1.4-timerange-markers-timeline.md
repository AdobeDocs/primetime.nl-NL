---
description: In dit voorbeeld wordt de aanbevolen manier getoond om tijdbereikspecificaties op de afspeeltijdlijn op te nemen.
title: Tijdbereik en markeertekens op de tijdlijn plaatsen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---


# Tijdbereik en markeertekens op de tijdlijn plaatsen {#place-timerange-ad-markers-on-the-timeline}

In dit voorbeeld wordt de aanbevolen manier getoond om tijdbereikspecificaties op de afspeeltijdlijn op te nemen.

1. Vertaal de out-of-band ad-positioneringsinformatie in een lijst van `TimeRange` specificaties (namelijk instanties van de `TimeRange` klasse).
1. Gebruik de set met `TimeRange`-specificaties om een instantie van de klasse `TimeRangeCollection` te vullen.
1. Geef de instantie Metagegevens, die kan worden verkregen uit de instantie `TimeRangeCollection`, door aan de methode `replaceCurrentItem` (deel van de interface MediaPlayer).
1. Wacht op TVSDK aan overgang aan de `PREPARED` staat door op &lt;a1 te wachten callback om worden teweeggebracht.`PlaybackEventListener#onPrepared`
1. Start het afspelen van video door de methode `play()` aan te roepen (onderdeel van de interface `MediaPlayer`).

* Conflicten in tijdlijn afhandelen: Er kunnen zich gevallen voordoen waarin bepaalde `TimeRange`-specificaties elkaar op de afspeeltijdlijn overlappen. De waarde van de beginpositie die overeenkomt met een `TimeRange`-specificatie kan bijvoorbeeld lager zijn dan de waarde van de eindpositie die al is geplaatst. In dit geval past TVSDK de beginpositie van de desbetreffende `TimeRange`-specificatie ongemerkt aan om tijdlijnconflicten te voorkomen. Door deze aanpassing wordt de nieuwe `TimeRange` korter dan oorspronkelijk opgegeven. Als de aanpassing zo extreem is dat deze zou leiden tot een `TimeRange` met een duur van nul ms, laat TVSDK de beledigende `TimeRange` specificatie zachtjes vallen.
* Wanneer `TimeRange` specificaties voor aangepaste advertentie-einden worden verstrekt, probeert TVSDK om deze in advertenties te vertalen die binnen en pauzes worden gegroepeerd. TVSDK zoekt naar aangrenzende `TimeRange`-specificaties en voegt deze in afzonderlijke ad-einden samen. Als er tijdbereiken zijn die niet aan een ander tijdbereik grenzen, worden ze omgezet in ad-einden die één advertentie bevatten.
* Aangenomen wordt dat het item van de mediaspeler dat wordt geladen, naar een VOD-element verwijst. TVSDK controleert dit telkens wanneer uw toepassing een mediabron probeert te laden waarvan de metagegevens `TimeRange`-specificaties bevatten die alleen kunnen worden gebruikt in de context van de aangepaste functie voor advertenties. Als het onderliggende element niet van het type VOD is, genereert de TVSDK-bibliotheek een uitzondering.
* Bij het omgaan met aangepaste advertentiemarkeringen deactiveert TVSDK andere ad-resolving mechanismen (via Adobe Primetime en besluitvorming (voorheen bekend als Auditude) of een ander ad-provisioning systeem). U kunt een van de verschillende ad-resolver-modules van TVSDK of het aangepaste ad-markeermechanisme gebruiken. Wanneer u de API voor aangepaste advertentiemarkeringen gebruikt, wordt de advertentie-inhoud beschouwd als al opgelost en op de tijdlijn geplaatst.

Het volgende codefragment geeft een eenvoudig voorbeeld van het feit dat een set van drie TimeRange-specificaties op de tijdlijn worden geplaatst als aangepaste ad-markeertekens.

```java>
// Assume that the 3 timerange specs are obtained through external means: CMS, etc. 
// Use these 3 timerange specs to populate the TimeRangeCollection instance 
TimeRangeCollection timeRanges = new TimeRangeCollection();  
timeRanges.addTimeRange(new TimeRange(0,10000)); 
timeRanges.addTimeRange(new TimeRange(15000,20000)); 
timeRanges.addTimeRange(new TimeRange(25000,30000)); 
 
// create and configure a MediaResource instance 
MediaResource mediaResource =  
  MediaResource.createFromUrl("www.example.com/video/test_video.m3u8",  
                               timeRanges.toMetadata(null)); 
 
// prepare the content for playback by creating 
// NOTE: mediaPlayer is an instance of a properly configured MediaPlayer  
mediaPlayer.replaceCurrentItem(mediaResource); 
// wait for TVSDK to reach the PREPARED state 
... 
MediaPlayer.PlaybackEventListener playbackEventListener = new 
  MediaPlayer.PlaybackEventListener() { 
    @Override 
    public void onPrepared() { 
        // TVSDK in in the PREPARED state. We are allowed to start the playback  
        mediaPlayer.play(); 
    } 
} 
```
