---
description: Met aangepaste advertentiemarkeringen kunt u een set tijdbereikspecificaties die tijdlijnsegmenten vertegenwoordigen, doorgeven aan TVSDK.
seo-description: Met aangepaste advertentiemarkeringen kunt u een set tijdbereikspecificaties die tijdlijnsegmenten vertegenwoordigen, doorgeven aan TVSDK.
seo-title: TimeRange, klasse
title: TimeRange, klasse
uuid: adf4f1ad-6b3b-48ac-a388-ee1fd54f770b
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# TimeRange, klasse{#timerange-class}

Met aangepaste advertentiemarkeringen kunt u een set tijdbereikspecificaties die tijdlijnsegmenten vertegenwoordigen, doorgeven aan TVSDK.

<!--<a id="section_42EB6D62627A424ABA250E3246EFEFC3"></a>-->

Elke TimeRange-specificatie in de set vertegenwoordigt een segment in de afspeeltijdlijn dat intern door TVSDK wordt onderhouden en dat op de juiste wijze moet worden gemarkeerd als een periode die met advertenties verband houdt.

De `TimeRange` klasse is een eenvoudige gegevensstructuur die de startpositie en de eindpositie op de tijdlijn beschikbaar maakt. Deze twee alleen-lezen-eigenschappen onttrekken het idee van een tijdbereik in de afspeeltijdlijn.

>[!TIP]
>
>Beide waarden worden uitgedrukt in milliseconden.

Hier volgt een overzicht van de `TimeRange` klasse:

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

