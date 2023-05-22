---
description: HLS de stromen die door een Netwerk van de Levering van de Inhoud (CDN) worden geleverd kunnen authentificatietokens op manifest en segmentverzoeken voor controle soms gebruiken. Deze tokens kunnen worden opgegeven als URL-parameters of als cookiekopteksten.
title: Vertogende segmentstromen
exl-id: 20a3e8a2-2e9d-4c0d-abea-66edcbcf0003
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# Vertogende segmentstromen{#tokenized-segment-streams}

HLS de stromen die door een Netwerk van de Levering van de Inhoud (CDN) worden geleverd kunnen authentificatietokens op manifest en segmentverzoeken voor controle soms gebruiken. Deze tokens kunnen worden opgegeven als URL-parameters of als cookiekopteksten.

Tokens die als koekjes op master manifest (m3u8) reactie worden verstrekt worden niet gedeeld met de segment (ts) verzoeken zelfs wanneer de segmentverzoeken voor het zelfde domein zijn. Als u het delen van deze cookies in een segmentverzoek wilt inschakelen, stelt u de volgende eigenschap in op de knop `PTMetadata` -instantie die aan het Player-item wordt doorgegeven: 

```
PTMetadata *metadata = [[[PTMetadata alloc] init] autorelease]; 
[metadata setValue:[NSNumber numberWithBool:YES] forKey:kSyncCookiesWithAVAsset]; 
```

Er wordt een aanvullend verzoek ingediend voor het master manifest (m3u8) voordat de stream wordt afgespeeld.

>[!IMPORTANT]
>
>Deze functie voor het delen van cookies wordt alleen ondersteund op apparaten met iOS 8 of hoger.
