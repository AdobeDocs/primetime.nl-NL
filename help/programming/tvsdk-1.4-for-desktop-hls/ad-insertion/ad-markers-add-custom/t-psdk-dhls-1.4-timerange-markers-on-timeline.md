---
description: In dit voorbeeld wordt de aanbevolen manier getoond om tijdbereikspecificaties op de afspeeltijdlijn op te nemen.
seo-description: In dit voorbeeld wordt de aanbevolen manier getoond om tijdbereikspecificaties op de afspeeltijdlijn op te nemen.
seo-title: Tijdbereik en markeertekens op de tijdlijn plaatsen
title: Tijdbereik en markeertekens op de tijdlijn plaatsen
uuid: cbcc4c84-0d56-4331-b555-b8e59f7d52d4
translation-type: tm+mt
source-git-commit: fd21a29bb186238142d43e0277bbf92f8406f6f7
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---


# Tijdbereik en markeertekens op de tijdlijn plaatsen {#place-timerange-ad-markers-on-the-timeline}

In dit voorbeeld wordt de aanbevolen manier getoond om tijdbereikspecificaties op de afspeeltijdlijn op te nemen.

1. Vertaal de out-of-band ad-positioneringsinformatie in een lijst van `TimeRange` specificaties (namelijk instanties van de `TimeRange` klasse).
1. Gebruik de set met `TimeRange`-specificaties om een instantie van de klasse `TimeRangeCollection` te vullen.
1. Geef de instantie Metagegevens, die kan worden verkregen uit de instantie `TimeRangeCollection`, door aan de methode `replaceCurrentItem` (onderdeel van de interface `MediaPlayer`).
1. Wacht op TVSDK aan overgang aan de PREPARED staat door op `PlaybackEventListener#onPrepared` callback te wachten om worden teweeggebracht.
1. Start het afspelen van video door de methode `play()` aan te roepen (onderdeel van de interface `MediaPlayer`).

* Conflicten in tijdlijn afhandelen: Er kunnen zich gevallen voordoen waarin bepaalde `TimeRange`-specificaties elkaar op de afspeeltijdlijn overlappen. De waarde van de beginpositie die overeenkomt met een `TimeRange`-specificatie kan bijvoorbeeld lager zijn dan de waarde van de eindpositie die al is geplaatst. In dit geval past TVSDK de beginpositie van de desbetreffende `TimeRange`-specificatie ongemerkt aan om tijdlijnconflicten te voorkomen. Door deze aanpassing wordt de nieuwe `TimeRange` korter dan oorspronkelijk opgegeven. Als de aanpassing zo extreem is dat deze zou leiden tot een `TimeRange` met een duur van nul ms, laat TVSDK de beledigende `TimeRange` specificatie zachtjes vallen.

* Wanneer `TimeRange` specificaties voor aangepaste advertentie-einden worden verstrekt, probeert TVSDK om deze in advertenties te vertalen die binnen en pauzes worden gegroepeerd. TVSDK zoekt naar aangrenzende `TimeRange`-specificaties en voegt deze in afzonderlijke ad-einden samen. Als er tijdbereiken zijn die niet aan een ander tijdbereik grenzen, worden ze omgezet in ad-einden die één advertentie bevatten.

* Aangenomen wordt dat het item van de mediaspeler dat wordt geladen, naar een VOD-element verwijst. TVSDK controleert dit telkens wanneer uw toepassing een mediabron probeert te laden waarvan de metagegevens `TimeRange`-specificaties bevatten die alleen kunnen worden gebruikt in de context van de aangepaste functie voor advertenties. Als het onderliggende element niet van het type VOD is, genereert de TVSDK-bibliotheek een uitzondering.

* Bij het omgaan met aangepaste advertentiemarkeringen deactiveert TVSDK andere ad-resolving mechanismen (via Adobe Primetime en besluitvorming (voorheen bekend als Auditude) of een ander ad-provisioning systeem). U kunt een van de verschillende ad-resolver-modules van TVSDK of het aangepaste ad-markeermechanisme gebruiken. Wanneer u de API voor aangepaste advertentiemarkeringen gebruikt, wordt de advertentie-inhoud beschouwd als al opgelost en op de tijdlijn geplaatst.

<!--<a id="example_639BD1B66CE74F3DB65ED06CAD23EB09"></a>-->

Het volgende codefragment biedt een eenvoudig voorbeeld waarin een set van drie `TimeRange`-specificaties als aangepaste ad-markeertekens op de tijdlijn worden geplaatst.

```
// Assume that the 3 timerange specs are obtained through external means: CMS, etc. 
// Use these 3 timerange specs to populate the TimeRangeCollection instance 
var timeRanges:TimeRangeCollection = new TimeRangeCollection(); 
timeRanges.addTimeRange(new TimeRange(0,10000)); 
timeRanges.addTimeRange(new TimeRange(15000,20000)); 
timeRanges.addTimeRange(new TimeRange(25000,30000)); 
  
// create and configure a MediaResource instance 
MediaResource mediaResource =  
  MediaResource.createFromUrl("www.example.com/video/test_video.m3u8",  
                             timeRanges.toMetadata(null));
```
