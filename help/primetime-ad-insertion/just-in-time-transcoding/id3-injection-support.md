---
description: Just-in-Time-transcoding kan ID3-metagegevens met tijdslimiet in ad-hocgroepen injecteren om het bijhouden van advertenties op de client te vergemakkelijken.
seo-description: Just-in-Time-transcoding kan ID3-metagegevens met tijdslimiet in HLS-indeling en creatieve documenten injecteren om het bijhouden van advertenties op de client te vergemakkelijken.
seo-title: Just-in-Time-transcodering gebruiken om ID3-getimede metagegevenstags te injecteren
title: Just-in-Time-transcodering gebruiken om ID3-getimede metagegevenstags te injecteren
uuid: 491bbb9e-15de-4871-baa1-f7bb0ea0dde2
translation-type: tm+mt
source-git-commit: 0f98b9848f1764e7c66e3692d8a845513493597f
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 0%

---


# Just-in-Time-transformatie gebruiken om ID3-getimede metagegevenstags {#using-crs-to-inject-id-timed-metadata-tags} te injecteren

CRS kan ID3-metagegevens met tijdslimiet in ad-hocgroepen injecteren om het bijhouden van advertenties op de client te vergemakkelijken.

De clientspeler leest de ID3-metagegevens om framenauwkeurigheid en tekstspatiëring mogelijk te maken.

>[!NOTE]
>
>ID3-injectiefuncties voor metagegevens met tijdslimiet alleen voor Safari/iOS.

## Workflow voor CRS voor ID3-injectie {#workflow-for-crs-for-id3-injection}

Als Primetime Ad Insertion de parameter `ptplayer=ios-mobileweb` ontvangt, zal het ID3 pakketten in getranscodeerd en creatief injecteren alvorens aan aangewezen en opslagCDN te uploaden.