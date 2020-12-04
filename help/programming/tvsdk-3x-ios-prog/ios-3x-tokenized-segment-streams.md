---
description: HLS de stromen die door een Netwerk van de Levering van de Inhoud (CDN) worden geleverd kunnen authentificatietokens op manifest en segmentverzoeken voor controle soms gebruiken. Deze tokens kunnen worden opgegeven als URL-parameters of als cookiekopteksten.
seo-description: HLS de stromen die door een Netwerk van de Levering van de Inhoud (CDN) worden geleverd kunnen authentificatietokens op manifest en segmentverzoeken voor controle soms gebruiken. Deze tokens kunnen worden opgegeven als URL-parameters of als cookiekopteksten.
seo-title: Vertogende segmentstromen
title: Vertogende segmentstromen
uuid: 62e3b858-2605-4960-b504-9010674f80ad
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---


# Vertogende segmentstromen {#tokenized-segment-streams}

HLS de stromen die door een Netwerk van de Levering van de Inhoud (CDN) worden geleverd kunnen authentificatietokens op manifest en segmentverzoeken voor controle soms gebruiken. Deze tokens kunnen worden opgegeven als URL-parameters of als cookiekopteksten.

Tokens die als koekjes op master manifest (m3u8) reactie worden verstrekt worden niet gedeeld met de segment (ts) verzoeken zelfs wanneer de segmentverzoeken voor het zelfde domein zijn. Als u het delen van deze cookies wilt inschakelen in een segmentverzoek, stelt u de volgende eigenschap in voor de instantie `PTMetadata` die aan het speleritem wordt geleverd: 

```
PTMetadata *metadata = [[[PTMetadata alloc] init] autorelease]; 
[metadata setValue:[NSNumber numberWithBool:YES] forKey:kSyncCookiesWithAVAsset]; 
```

Er wordt een aanvullend verzoek ingediend voor het master manifest (m3u8) voordat de stream wordt afgespeeld.

>[!IMPORTANT]
>
>Deze functie voor het delen van cookies wordt alleen ondersteund op apparaten met iOS 8 of hoger.

