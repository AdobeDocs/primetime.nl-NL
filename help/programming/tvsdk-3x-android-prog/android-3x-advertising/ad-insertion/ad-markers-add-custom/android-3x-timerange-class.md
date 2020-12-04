---
description: Met aangepaste advertentiemarkeringen kunt u een set tijdbereikspecificaties die tijdlijnsegmenten vertegenwoordigen, doorgeven aan TVSDK.
seo-description: Met aangepaste advertentiemarkeringen kunt u een set tijdbereikspecificaties die tijdlijnsegmenten vertegenwoordigen, doorgeven aan TVSDK.
seo-title: TimeRange, klasse
title: TimeRange, klasse
uuid: af3ce5e6-44b5-457f-a6e7-aa232defb91e
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---


# TimeRange, klasse {#timerange-class}

Met aangepaste advertentiemarkeringen kunt u een set tijdbereikspecificaties die tijdlijnsegmenten vertegenwoordigen, doorgeven aan TVSDK.

<!--<a id="section_42EB6D62627A424ABA250E3246EFEFC3"></a>-->

Elke `TimeRange`-specificatie in de set vertegenwoordigt een segment in de afspeeltijdlijn dat intern door TVSDK wordt onderhouden en dat op de juiste wijze moet worden gemarkeerd als een periode met betrekking tot een advertentie.

De klasse `TimeRange` is een eenvoudige gegevensstructuur die de startpositie en de eindpositie op de tijdlijn beschikbaar maakt. Deze twee alleen-lezen-eigenschappen onttrekken het idee van een tijdbereik in de afspeeltijdlijn.

>[!TIP]
>
>Beide waarden worden uitgedrukt in milliseconden.

Hier volgt een overzicht van de klasse `TimeRange`:

```java
public final class TimeRange {
    // the start/end values are provided at construction time
    public static TimeRange createRange(long begin, long duration) {...} 

    // only getters are available
    public long getBegin() {...} 
    public long getEnd() {...} 
    public long getDuration() {...}
}
```
