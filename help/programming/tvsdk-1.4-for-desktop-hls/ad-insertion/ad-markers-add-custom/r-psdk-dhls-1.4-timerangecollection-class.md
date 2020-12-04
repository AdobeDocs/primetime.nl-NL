---
description: De het hulpprogrammaklasse van TimeRangeCollection onttrekt het begrip van een bevolen inzameling van specificaties TimeRange en verleent de diensten om zich in een instantie van Metadata te vertalen.
seo-description: De het hulpprogrammaklasse van TimeRangeCollection onttrekt het begrip van een bevolen inzameling van specificaties TimeRange en verleent de diensten om zich in een instantie van Metadata te vertalen.
seo-title: TimeRangeCollection, klasse
title: TimeRangeCollection, klasse
uuid: da781df4-6b19-47e1-8dc5-ea83c139f061
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---


# TimeRangeCollection-klasse{#timerangecollection-class}

De het hulpprogrammaklasse van TimeRangeCollection onttrekt het begrip van een bevolen inzameling van specificaties TimeRange en verleent de diensten om zich in een instantie van Metadata te vertalen.

<!--<a id="section_D87AA7BC628D458DAB12D5247AD34B41"></a>-->

```
public final class TimeRangeCollection { 
    public static const MARK_RANGES:String = "mark_ranges"; 
  
    public function TimeRangeCollection(timeRanges:Vector.<TimeRange>) {…} 
    public function addTimeRange(timeRange:TimeRange):void {…} 
    public function toMetadata(options:Metadata):Metadata {…} 
}
```

De gedefinieerde waarde voor het type verzameling is `MARK_RANGES`, `DELETE_RANGES` en `REPLACE_RANGES`. U kunt `TimeRangeCollection`s tot stand brengen gebruikend deze drie types.
