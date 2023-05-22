---
description: In dit voorbeeld wordt de aanbevolen manier getoond om tijdbereikspecificaties op de afspeeltijdlijn op te nemen.
title: Tijdbereik en markeertekens op de tijdlijn plaatsen
exl-id: a4d45395-38a4-4345-9ba3-87cd9200b9f6
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# Tijdbereik en markeertekens op de tijdlijn plaatsen {#place-timerange-ad-markers-on-the-timeline}

In dit voorbeeld wordt de aanbevolen manier getoond om tijdbereikspecificaties op de afspeeltijdlijn op te nemen.

1. Vertaal de out-of-band ad-positioneringsinformatie in een lijst van `TimeRange` specificaties (d.w.z. `TimeRange` klasse).
1. De set met `TimeRange` specificaties om een instantie van de `TimeRangeCollection` klasse.
1. Geef de instantie Metagegevens door, die kan worden verkregen via de `TimeRangeCollection` van de `replaceCurrentItem` methode (deel van de `MediaPlayer` interface).
1. Wacht tot TVSDK overgaat naar de status PREPARED door te wachten op de `PlaybackEventListener#onPrepared` callback die moet worden geactiveerd.
1. Het afspelen van video starten door het `play()` methode (deel van de `MediaPlayer` interface).

* Conflicten in tijdlijn afhandelen: Er kunnen zich gevallen voordoen waarin `TimeRange` de specificaties overlappen op de afspeeltijdlijn. De waarde van de beginpositie die overeenkomt met een `TimeRange` specificatie kan lager zijn dan de waarde van de eindpositie die al is geplaatst. In dit geval past TVSDK de startpositie van de overtreding stilletjes aan `TimeRange` specificatie om tijdlijnconflicten te voorkomen. Door deze aanpassing worden de nieuwe `TimeRange` wordt korter dan oorspronkelijk opgegeven. Als de aanpassing zo extreem is dat dit tot `TimeRange` met een duur van 0 ms laat TVSDK de overtreding stil vallen `TimeRange` specificatie.

* Wanneer `TimeRange` Er zijn specificaties voor aangepaste advertentie-einden. TVSDK probeert deze te vertalen in advertenties die zijn gegroepeerd in ad-einden. TVSDK zoekt naar naast elkaar `TimeRange` specificaties en deze in afzonderlijke ad-hocpauzes samenvoegen. Als er tijdbereiken zijn die niet aan een ander tijdbereik grenzen, worden ze omgezet in ad-einden die één advertentie bevatten.

* Aangenomen wordt dat het item van de mediaspeler dat wordt geladen, naar een VOD-element verwijst. TVSDK controleert dit telkens wanneer uw toepassing een mediabron probeert te laden waarvan de metagegevens `TimeRange` specificaties die alleen kunnen worden gebruikt in de context van de aangepaste functie voor advertenties. Als het onderliggende element niet van het type VOD is, genereert de TVSDK-bibliotheek een uitzondering.

* Bij het omgaan met aangepaste advertentiemarkeringen deactiveert TVSDK andere ad-resolving mechanismen (via Adobe Primetime en besluitvorming (voorheen bekend als Auditude) of een ander ad-provisioning systeem). U kunt een van de verschillende ad-resolver-modules van TVSDK of het aangepaste ad-markeermechanisme gebruiken. Wanneer u de API voor aangepaste advertentiemarkeringen gebruikt, wordt de advertentie-inhoud beschouwd als al opgelost en op de tijdlijn geplaatst.

<!--<a id="example_639BD1B66CE74F3DB65ED06CAD23EB09"></a>-->

Het volgende codefragment geeft een eenvoudig voorbeeld van een set van drie `TimeRange` specificaties worden op de tijdlijn geplaatst als aangepaste ad-markeertekens.

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
