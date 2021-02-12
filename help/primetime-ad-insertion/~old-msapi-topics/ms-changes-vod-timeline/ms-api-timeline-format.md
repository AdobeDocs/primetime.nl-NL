---
description: U kunt tijdlijnen voor en onderbrekingen in VOD-inhoud opgeven of overschrijven met behulp van een opgemaakte lijst met advertentie- en inhoudssegmenten, pods genoemd.
seo-description: U kunt tijdlijnen voor en onderbrekingen in VOD-inhoud opgeven of overschrijven met behulp van een opgemaakte lijst met advertentie- en inhoudssegmenten, pods genoemd.
seo-title: Tijdlijnindeling VOD
title: Tijdlijnindeling VOD
uuid: 6daaf605-e5ee-48dc-a222-a5973b3d915a
translation-type: tm+mt
source-git-commit: e437f4143fb939f46d106c64efc391137c33fe17
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---


# Indeling VOD-tijdlijn {#vod-timeline-format}

U kunt tijdlijnen voor en onderbrekingen in VOD-inhoud opgeven of overschrijven met behulp van een opgemaakte lijst met advertentie- en inhoudssegmenten, pods genoemd.

## Pods {#section_606E9456E25E41C8B8537A023DDD96CE}

Een pod is een advertentie-einde of een inhoudssegment. Een tijdlijn bestaat uit een reeks pods, gescheiden door puntkomma&#39;s. De volgende typen pods bestaan:

### Ad break

```
B,duration,maximum_number_of_ads,position
```

De duur is in seconden, met nauwkeurigheid van 0,001 (milliseconden); Het aantal advertenties is een geheel getal. Positie is een van de volgende:
* **n** Geen — geen advertentie
* **p** Pre-roll — vóór de inhoud
* **m** Halve rol — binnen de inhoud
* **t** Na de rol — na de inhoud

`B,60,2,p` staat bijvoorbeeld voor een onderbreking van één minuut voor maximaal twee advertenties vóór de inhoud.

### Inhoudssegment - hoofdstuk

```
C,duration,number_of_lots
```

De duur is in seconden, met nauwkeurigheid van 0,001 (milliseconden); Het aantal partijen (inhoudsgedeelten) is een geheel getal. `C,300,1` vertegenwoordigt bijvoorbeeld één sectie van vijf minuten van inhoud.