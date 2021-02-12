---
description: CRS verstrekt just-in-time (JIT) en asynchrone het herverpakken en omzetten HLS-aan-HLS. Het resultaat van het opnieuw verpakken is een HLS-opgemaakte versie van het origineel en de creatieve versie. CRS plaatst de HLS geformatteerde versie op de server van het netwerk van de inhoudslevering (CDN) voor gebruik wanneer nodig.
seo-description: CRS verstrekt just-in-time (JIT) en asynchrone het herverpakken en omzetten HLS-aan-HLS. Het resultaat van het opnieuw verpakken is een HLS-opgemaakte versie van het origineel en de creatieve versie. CRS plaatst de HLS geformatteerde versie op de server van het netwerk van de inhoudslevering (CDN) voor gebruik wanneer nodig.
seo-title: Belangrijkste toepassingen van CRS
title: Belangrijkste toepassingen van CRS
uuid: df2caa67-bc94-4146-9b93-14edc060c3d5
translation-type: tm+mt
source-git-commit: e1e33d3ac0aad44859cd49566331524da72ac7e4
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---


# Belangrijkste toepassingen van CRS {#main-uses-of-crs}

CRS verstrekt just-in-time (JIT) en asynchrone het herverpakken en omzetten HLS-aan-HLS. Het resultaat van het opnieuw verpakken is een HLS-opgemaakte versie van het origineel en de creatieve versie. CRS plaatst de HLS geformatteerde versie op de server van het netwerk van de inhoudslevering (CDN) voor gebruik wanneer nodig.

In JIT begint het herverpakken van Adobe Primetime en begint het invoegproces wanneer het voor het eerst een niet-HLS en creatieve functie tegenkomt. Dit betekent meestal dat er tijdens het herverpakken kansen verloren gaan om de advertentie uit te voeren.

In asynchrone herverpakking, wordt de advertentie getranscodeerd en opgeslagen alvorens het nodig is, die die verloren kansen kunnen elimineren.

Bij HLS-aan-HLS-omzetting, herformatteert CRS HLS en creatief in aangewezen grote brokken om verenigbare playback te verzekeren.

## Just-in-Time-herverpakking {#section_1BA344F2300B49F291865A7461EDFEAE}

De volgorde voor JIT-herverpakken is als volgt:

1. De manifestserver haalt een advertentie op.
1. Als de advertentievorm HLS is, neemt de manifestserver de advertentie in de inhoudsstroom op.
1. Als de indeling geen HLS is (bijvoorbeeld MP4, FLV of WebM), zoekt de manifestserver naar een getranscodeerde versie op de CDN-server. Als er een wordt gevonden, wordt de getranscodeerde en in de inhoudsstroom ingevoegd.
1. Als het formaat niet HLS is en de server CDN heeft geen getranscodeerde versie, gaat de duidelijke server de advertentie tot CRS over, die de advertentie transcodeert en het resultaat op de server CDN voor later gebruik opslaat.
1. De manifestserver keert de inhoud zonder de advertentie terug.

## Asynchroon opnieuw verpakken {#section_ACDFB43FDA4B445CB9F2A107FEB4F2F7}

U kunt de API gebruiken die in [API opnieuw verpakken](../~old-creative-repackaging-service/api-repackage.md) wordt beschreven om een niet-HLS creatief pretranscoderen om verlies van indrukkingen te minimaliseren en monetisatie te maximaliseren.

## HLS-aan-HLS-omzetting {#section_877A0E7E8FAF4C2DB086A31C24D53435}

Om buffering en vertraging te voorkomen, downloadt een cliënt een video in kleine brokken. Als de brokgrootten inconsistent zijn, kan het afspelen schokkerig zijn. De omzetting HLS-aan-HLS zorgt ervoor dat de gegevensbrokken allen van de zelfde duur (bijvoorbeeld, 6 seconden) zijn.

>[!NOTE]
>
>CRS veroorzaakt HLS versie 3, ongeacht welke versie HLS het ontvangt.