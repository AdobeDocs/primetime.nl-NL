---
description: De ReplaceTimeRange hulpprogrammaklasse is een uitbreiding van de klasse TimeRange die met CustomRangeMetadata moet worden gebruikt.
seo-description: De ReplaceTimeRange hulpprogrammaklasse is een uitbreiding van de klasse TimeRange die met CustomRangeMetadata moet worden gebruikt.
seo-title: ReplaceTimeRange, klasse
title: ReplaceTimeRange, klasse
uuid: d554c17a-2bdc-4c4a-bb8f-2d357511bb32
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '54'
ht-degree: 0%

---


# ReplaceTimeRange, klasse {#replacetimerange-class}

De ReplaceTimeRange hulpprogrammaklasse is een uitbreiding van de klasse TimeRange die met CustomRangeMetadata moet worden gebruikt.

```java
public class ReplaceTimeRange extends TimeRange {
    // Default constructor method
    public ReplaceTimeRange() { 
        ... 
    }

    // Details of begining, duration and replaceDuration 
    // provided at construction time 
    public ReplaceTimeRange(long begin, long duration, long replaceDuration) { 
        ... 
    }

    // Replace duration
    public long getReplaceDuration() { 
        ... 
    }
}
```
