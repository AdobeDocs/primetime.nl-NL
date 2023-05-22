---
description: CRS kan metagegevens met ID3-timing in HLS-indeling en creatieve documenten injecteren om het bijhouden van advertenties op de client te vergemakkelijken.
title: CRS gebruiken om ID3-tags met getimede metagegevens te injecteren
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---


# CRS gebruiken om ID3-tags met getimede metagegevens te injecteren {#using-crs-to-inject-id-timed-metadata-tags}

CRS kan metagegevens met ID3-timing in HLS-indeling en creatieve documenten injecteren om het bijhouden van advertenties op de client te vergemakkelijken.

De clientspeler leest de ID3-metagegevens om framenauwkeurigheid en tekstspatiëring mogelijk te maken.

>[!NOTE]
>
>Injecteren van metagegevens met ID3-timing werkt alleen in Safari op iOS.

## Werkschema voor CRS voor ID3-injectie {#workflow-for-crs-for-id3-injection}

De workflow voor ID3-injectie is gelijk aan die in [Gedetailleerde workflows voor JIT-herverpakken.](../~old-creative-repackaging-service/jit-repackage.md) Als de manifestserver de `ptplayer=ios-mobileweb` wordt aangegeven dat CRS ID3-pakketten moet injecteren in de getranscodeerde en creatieve schijven voordat deze naar de CDN-server worden geüpload.

>[!NOTE]
>
>In een multi-CDN opstelling, gebruikt de manifestserver `ptcdn` in de laarzentrekker-URL om de CDN-server te identificeren die de advertentie moet uploaden.