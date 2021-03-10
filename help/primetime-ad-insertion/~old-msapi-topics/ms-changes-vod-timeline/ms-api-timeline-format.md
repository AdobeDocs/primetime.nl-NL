---
description: U kunt tijdlijnen voor en onderbrekingen in VOD-inhoud opgeven of overschrijven met behulp van een opgemaakte lijst met advertentie- en inhoudssegmenten, pods genoemd.
title: Tijdlijnindeling VOD
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '163'
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