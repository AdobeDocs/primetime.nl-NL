---
title: Voorbeeld van een aangepast VOD-element
description: Voorbeeld van een aangepast VOD-element
copied-description: true
exl-id: 4990ef96-f8bf-4b3b-83a0-979bf8c0e70c
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 0%

---

# Voorbeeld van een aangepast VOD-element{#example-of-a-customized-vod-asset}

Hier volgt een voorbeeld van een aangepast VOD-element:

```
#EXTM3U
#EXT-X-VERSION:3
#EXT-X-TARGETDURATION:7
 
#EXT-X-ASSET:AID=10
 
#EXTINF:9.9766,
seg1.ts
 
#EXTINF:9.9766,
seg2.ts
 
#EXTINF:9.9766,
seg3.ts
 
#EXT-X-AD:DURATION=10
#EXTINF:9.9766,
seg4.ts
 
#EXTINF:9.9766,
seg5.ts
 
#EXT-X-ENDLIST
```

Uw toepassing kan de volgende scenario&#39;s instellen:

* Een melding wanneer `#EXT-X-ASSET` -tags of een andere set aangepaste tagnamen waarop u zich hebt geabonneerd, bestaan in het bestand.
* Advertenties invoegen wanneer een `#EXT-X-AD` -tag of een andere aangepaste tagnaam in de stream wordt gevonden.
