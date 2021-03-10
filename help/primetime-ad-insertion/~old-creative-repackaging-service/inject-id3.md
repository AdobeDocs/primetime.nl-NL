---
description: CRS kan metagegevens met ID3-timing in HLS-indeling en creatieve documenten injecteren om het bijhouden van advertenties op de client te vergemakkelijken.
seo-description: CRS kan metagegevens met ID3-timing in HLS-indeling en creatieve documenten injecteren om het bijhouden van advertenties op de client te vergemakkelijken.
seo-title: CRS gebruiken om ID3-tags met getimede metagegevens te injecteren
title: CRS gebruiken om ID3-tags met getimede metagegevens te injecteren
uuid: 491bbb9e-15de-4871-baa1-f7bb0ea0dde2
translation-type: tm+mt
source-git-commit: e1e33d3ac0aad44859cd49566331524da72ac7e4
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---


# CRS gebruiken om ID3 getimede metagegevenstags {#using-crs-to-inject-id-timed-metadata-tags} te injecteren

CRS kan metagegevens met ID3-timing in HLS-indeling en creatieve documenten injecteren om het bijhouden van advertenties op de client te vergemakkelijken.

De clientspeler leest de ID3-metagegevens om framenauwkeurigheid en tekstspatiëring mogelijk te maken.

>[!NOTE]
>
>Injecteren van metagegevens met ID3-timing werkt alleen op Safari op iOS.

## Workflow voor CRS voor ID3-injectie {#workflow-for-crs-for-id3-injection}

De workflow voor ID3-injectie is gelijk aan die in [Gedetailleerde workflows voor JIT-herverpakking.](../~old-creative-repackaging-service/jit-repackage.md) Als de manifestserver de  `ptplayer=ios-mobileweb` parameter ontvangt, vertelt het CRS om ID3 pakketten in getranscodeerd en creatief te injecteren alvorens het aan de CDN server te uploaden.

>[!NOTE]
>
>In een multi-CDN opstelling, gebruikt de manifestserver `ptcdn` parameter in bootstrap URL om de server te identificeren CDN om de advertentie te uploaden creatief.