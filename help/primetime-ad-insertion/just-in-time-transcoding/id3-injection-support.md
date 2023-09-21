---
description: Just-in-Time-transcoding kan ID3-metagegevens met tijdslimiet in ad-hocgroepen injecteren om het bijhouden van advertenties op de client te vergemakkelijken.
title: Just-in-Time-transcodering gebruiken om ID3-getimede metagegevenstags te injecteren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---

# Using Just-in-Time Transcoding to InjecID3 Timed Metadata Tags {#using-crs-to-inject-id-timed-metadata-tags}

CRS kan ID3-metagegevens met tijdslimiet in ad-hocgroepen injecteren om het bijhouden van advertenties op de client te vergemakkelijken.

De clientspeler leest de ID3-metagegevens om framenauwkeurigheid en tekstspatiëring mogelijk te maken.

>[!NOTE]
>
>ID3-injectiefuncties voor metagegevens met tijdslimiet alleen voor Safari/iOS.

## Werkschema voor CRS voor ID3-injectie {#workflow-for-crs-for-id3-injection}

Als Primetime Ad Insertion de `ptplayer=ios-mobileweb` worden ID3-pakketten in de getranscodeerde en creatieve code gespoeld voordat naar de juiste CDN voor opslag wordt geüpload.
