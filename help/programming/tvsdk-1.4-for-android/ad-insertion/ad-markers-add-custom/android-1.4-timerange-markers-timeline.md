---
description: In dit voorbeeld wordt de aanbevolen manier getoond om tijdbereikspecificaties op de afspeeltijdlijn op te nemen.
seo-description: In dit voorbeeld wordt de aanbevolen manier getoond om tijdbereikspecificaties op de afspeeltijdlijn op te nemen.
seo-title: Tijdbereik en markeertekens op de tijdlijn plaatsen
title: Tijdbereik en markeertekens op de tijdlijn plaatsen
uuid: 12935eba-2e91-40ea-a60e-02d0060c3cce
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Tijdbereik en markeertekens op de tijdlijn plaatsen {#place-timerange-ad-markers-on-the-timeline}

In dit voorbeeld wordt de aanbevolen manier getoond om tijdbereikspecificaties op de afspeeltijdlijn op te nemen.

1. Vertaal de out-of-band ad-positioneringsinformatie in een lijst van `TimeRange` specificaties (namelijk instanties van de `TimeRange` klasse).
1. Gebruik de set `TimeRange` specificaties om een instantie van de `TimeRangeCollection` klasse te vullen.
1. Geef de instantie Metadata (die kan worden verkregen van de `TimeRangeCollection` instantie) door aan de `replaceCurrentItem` methode (onderdeel van de interface MediaPlayer).
1. Wacht op TVSDK aan overgang aan de `PREPARED` staat door op `PlaybackEventListener#onPrepared` callback te wachten om worden teweeggebracht.
1. Start het afspelen van video door de `play()` methode aan te roepen (onderdeel van de `MediaPlayer` interface).

* Conflicten in tijdlijn afhandelen: Er kunnen zich gevallen voordoen waarin bepaalde `TimeRange` specificaties elkaar overlappen op de afspeeltijdlijn. De waarde van de beginpositie die overeenkomt met een `TimeRange` specificatie kan bijvoorbeeld lager zijn dan de waarde van de eindpositie die al is geplaatst. In dit geval past TVSDK de beginpositie van de conflicterende `TimeRange` specificatie op de achtergrond ongemerkt aan om tijdlijnconflicten te voorkomen. Door deze aanpassing, `TimeRange` wordt het nieuwe korter dan oorspronkelijk gespecificeerd. Als de aanpassing zo extreem is dat deze tot een `TimeRange` duur van 0 ms zou leiden, laat TVSDK de betreffende `TimeRange` specificatie zachtjes vallen.
* Wanneer `TimeRange` specificaties voor aangepaste advertentie-einden worden opgegeven, probeert TVSDK deze te vertalen in advertenties die binnen ad-einden zijn gegroepeerd. TVSDK zoekt naar aangrenzende `TimeRange` specificaties en voegt deze in afzonderlijke ad-einden samen. Als er tijdbereiken zijn die niet aan een ander tijdbereik grenzen, worden ze omgezet in ad-einden die één advertentie bevatten.
* Aangenomen wordt dat het item van de mediaspeler dat wordt geladen, naar een VOD-element verwijst. TVSDK controleert dit telkens wanneer uw toepassing een mediabron probeert te laden waarvan de metagegevens `TimeRange` specificaties bevatten die alleen kunnen worden gebruikt in de context van de aangepaste functie voor advertenties. Als het onderliggende element niet van het type VOD is, genereert de TVSDK-bibliotheek een uitzondering.
* Wanneer u werkt met aangepaste advertentiemarkeringen, deactiveert TVSDK andere ad-resolving mechanismen (via Adobe Primetime en besluitvorming (voorheen bekend als Auditude) of een ander ad-provisioning systeem). U kunt een van de verschillende ad-resolver-modules van TVSDK of het aangepaste ad-markeermechanisme gebruiken. Wanneer u de API voor aangepaste advertentiemarkeringen gebruikt, wordt de advertentie-inhoud beschouwd als al opgelost en op de tijdlijn geplaatst.

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
