---
description: Met aangepaste advertentiemarkeringen kunt u een set tijdbereikspecificaties die tijdlijnsegmenten vertegenwoordigen, doorgeven aan TVSDK.
title: TimeRange, klasse
exl-id: 7451c4f6-40df-48b2-a2c7-6d7826724716
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---

# TimeRange, klasse{#timerange-class}

Met aangepaste advertentiemarkeringen kunt u een set tijdbereikspecificaties die tijdlijnsegmenten vertegenwoordigen, doorgeven aan TVSDK.

<!--<a id="section_42EB6D62627A424ABA250E3246EFEFC3"></a>-->

Elke TimeRange-specificatie in de set vertegenwoordigt een segment in de afspeeltijdlijn dat intern door TVSDK wordt onderhouden en dat op de juiste wijze moet worden gemarkeerd als een periode die met advertenties verband houdt.

De `TimeRange` klasse is een eenvoudige gegevensstructuur die de startpositie en de eindpositie op de tijdlijn beschikbaar maakt. Deze twee alleen-lezen-eigenschappen onttrekken het idee van een tijdbereik in de afspeeltijdlijn.

>[!TIP]
>
>Beide waarden worden uitgedrukt in milliseconden.

Hier volgt een samenvatting van de `TimeRange` klasse:

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
