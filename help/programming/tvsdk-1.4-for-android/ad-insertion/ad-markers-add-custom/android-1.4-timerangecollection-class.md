---
description: De het hulpprogrammaklasse van TimeRangeCollection onttrekt het begrip van een bevolen inzameling van specificaties TimeRange en verleent de diensten om zich in een instantie van Metadata te vertalen.
title: TimeRangeCollection, klasse
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---


# TimeRangeCollection-klasse{#timerangecollection-class}

De het hulpprogrammaklasse van TimeRangeCollection onttrekt het begrip van een bevolen inzameling van specificaties TimeRange en verleent de diensten om zich in een instantie van Metadata te vertalen.

<!--<a id="section_D87AA7BC628D458DAB12D5247AD34B41"></a>-->

```java
public final class TimeRangeCollection {
    // default constructor method
    public TimeRangeCollection(Type type) {...}

    // the list of timerange specifications provided at construction time 
    public TimeRangeCollection(Type type, List<TimeRange> timeRanges) {...}

    // timerange specs can also be added later
    public void addTimeRange(TimeRange timeRange) {...}

    // translate the set of timerange specs into a Metadata instance 
    public Metadata toMetadata(Metadata options) {...}
}
```

De parameter `type`, de eerste positieparameter in de handtekening van de constructormethoden, is een instantie van de opsomming `TimeRangeCollection#Type`. Dit is onderdeel van de klasse `TimeRangeCollection`. De waarden die momenteel door deze opsomming worden bepaald zijn `MARK_RANGES`, `DELETE_RANGES`, en `REPLACE_RANGES`. U kunt `TimeRangeCollection` voorwerpen tot stand brengen gebruikend deze drie types.
