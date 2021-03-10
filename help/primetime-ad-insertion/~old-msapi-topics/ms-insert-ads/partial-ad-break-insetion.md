---
description: Met de PABI-functie (Partial Ad Break Insertion) bootst u een tv-achtige ervaring na waarin de gebruiker, als hij of zij zich bij een live stream aanmeldt in een mid-roll break, middenroladvertenties in plaats van een pre-roll advertentie of leisteen weergeeft.
title: Gedeeltelijke invoeging van advertentie-einde
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---


# Onvolledige invoeging van advertentie {#partial-ad-break-insertion}

Met de PABI-functie (Partial Ad Break Insertion) bootst u een tv-achtige ervaring na waarin de gebruiker, als hij of zij zich bij een live stream aanmeldt in een mid-roll break, middenroladvertenties in plaats van een pre-roll advertentie of leisteen weergeeft.

Wanneer de advertentieserver pre-rol advertenties voor een levende stroom terugkeert, zal de manifestserver pre-rol en onderbreking vóór het levende punt injecteren en zal de markering EXT-X-START met zijn waarde TIMEOFFSET opnemen die aan het begin van de pre-rol en onderbreking richt. Dit standaardgedrag zorgt ervoor dat de volledige pre-rol en de onderbreking vóór de inhoud bij het levende punt worden gespeeld. Als een gebruiker zich bij een stroom aansluit wanneer het levende punt dichtbij een middenrol en een onderbreking is, zal de gebruiker de pre-rol en onderbreking vóór de middenrol en onderbreking bij het levende punt tonen.

De eigenschap PABI instrueert de manifestserver de pre-rol en onderbreking negeren en plaatst de waarde EXT-X-START:TIMEOFFSET aan het begin van de mid-roll en heden bij live-point. Dit zorgt ervoor dat de gebruiker de volledige middenrol ziet en momenteel op het live punt speelt zonder dat hij de pre-rol en de onderbreking hoeft te bekijken.

>[!NOTE]
>
>Deze functionaliteit is alleen beschikbaar voor live streams. De manifestserver neemt pre-rol en onderbreking op VOD playlist door gebrek op.

>[!NOTE]
>
>Om PABI toe te laten, zult u [query_params](/help/primetime-ad-insertion/~old-msapi-topics/ms-getting-started/ms-api-query-params.md) in bootstrap URL moeten specificeren.

>[!NOTE]
>
>De [EXT-X-START](https://tools.ietf.org/html/rfc8216#section-4.3.5.2) is een standaard HLS-markering die op een aangewezen uitgangspunt binnen playlist wijst.

## Recommendations {#section_4CF0733B14504F2A99690310B9F3B130}

* Gebruik tracering aan de clientzijde omdat de client meer controle heeft over het vuren van trackingbeacons.
* Gedeeltelijke add-einden mogen alleen worden gebruikt in de modus voor het bijhouden van de server als de speler EXT-X-START ondersteunt.