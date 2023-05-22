---
description: Met aangepaste advertentiemarkeringen kunt u een set tijdbereikspecificaties die tijdlijnsegmenten vertegenwoordigen, doorgeven aan TVSDK.
title: TimeRange, klasse
exl-id: 9dc2abe1-189a-4ef4-9918-37835014bf1b
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---

# TimeRange, klasse{#timerange-class}

Met aangepaste advertentiemarkeringen kunt u een set tijdbereikspecificaties die tijdlijnsegmenten vertegenwoordigen, doorgeven aan TVSDK.

<!--<a id="section_42EB6D62627A424ABA250E3246EFEFC3"></a>-->

Elk `TimeRange` De specificatie in de set vertegenwoordigt een segment in de afspeeltijdlijn dat intern door TVSDK wordt onderhouden en dat op de juiste wijze moet worden gemarkeerd als een periode die met advertenties verband houdt.

De `TimeRange` klasse is een eenvoudige gegevensstructuur die de startpositie en de eindpositie op de tijdlijn beschikbaar maakt. Deze twee alleen-lezen-eigenschappen onttrekken het idee van een tijdbereik in de afspeeltijdlijn.

>[!TIP]
>
>Beide waarden worden uitgedrukt in milliseconden.

Hier volgt een overzicht van de klasse TimeRange:

```
public final class TimeRange {
    // the start/end values are provided at construction 
    public static function createRange(begin:Number, duration:Number {…}
 
    public function get begin():Number {…}
    public function get end():Number {…}
    public function get duration():Number {…}
}
```
