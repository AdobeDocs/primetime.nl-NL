---
description: De het hulpprogrammaklasse van TimeRangeCollection onttrekt het begrip van een bevolen inzameling van specificaties TimeRange en verleent de diensten om zich in een instantie van Metadata te vertalen.
seo-description: De het hulpprogrammaklasse van TimeRangeCollection onttrekt het begrip van een bevolen inzameling van specificaties TimeRange en verleent de diensten om zich in een instantie van Metadata te vertalen.
seo-title: TimeRangeCollection, klasse
title: TimeRangeCollection, klasse
uuid: 5705dc9d-4325-44b0-b5aa-196d09c3a67e
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# TimeRangeCollection, klasse{#timerangecollection-class}

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

De `type` parameter, de eerste positieparameter in de handtekening van de constructormethoden, is een instantie van de `TimeRangeCollection#Type` opsomming. Dit is onderdeel van de `TimeRangeCollection` klasse. De waarden die momenteel door deze opsomming worden bepaald zijn `MARK_RANGES`, `DELETE_RANGES`en `REPLACE_RANGES`. U kunt `TimeRangeCollection` objecten maken met deze drie typen.
