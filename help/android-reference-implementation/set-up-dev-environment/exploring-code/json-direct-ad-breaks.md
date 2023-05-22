---
title: JSON-object voor directe en automatische regeleinden
description: Geeft het JSON-object in detail wanneer de tekstwaarde direct is en wordt onderbroken
exl-id: d5e3ddd5-b963-4e7d-b04b-087d4fe96faf
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---

# JSON-object voor directe en automatische regeleinden{#json-object-for-direct-ad-breaks}

In het volgende codeblok worden de details van het JSON-object gedefinieerd wanneer de waarde van het type direct is en wordt afgebroken.

De `MetadataNode` geretourneerd door `IFeedItemAdapter:getStreamMetadata()` bevat een item met het type key `com.adobe.mediacore.metadata.DefaultMetadataKeys.JSON_METADATA_KEY` en waarde van een tekenreeksrepresentatie van de details van de JSON-objectwaarde hieronder.

```
“metadata”: { 
    “ad” :  { 
        “type”: “direct ad breaks”, 
        “details”: { 
            "ad-breaks": [ 
                { 
                    "tag": "break-001", 
                    "time": 0, 
                    "replace": 0, 
                    "ad-list": [ 
                        { 
                        }, 
                        { 
                        } 
                    ] 
                }, 
                { 
                    "tag": "break-002", 
                    "time": 300000, 
                    "replace": 0, 
                    "ad-list": [ 
                        { 
                        } 
                    ] 
                } 
            ] 
        } 
    } 
} 
```

| Eigenschap | Beschrijving |
|---|---|
| `tag` | Een tekenreeks die is toegewezen aan het tagveld in `com.adobe.mediacore.timeline.advertising.AdBreak`. |
| `time` | Geeft de begintijd aan voor het advertentietak, wordt toegewezen aan het tijdveld in `com.adobe.mediacore.timeline.advertising.AdBreak`. De waarde 0 geeft een advertentie vóór de rol aan. |
| `replace` | Geeft de vervangingsduur van het advertentiepakket aan en koppelt deze aan de `replaceDuration` veld in `com.adobe.mediacore.timeline.advertising.AdBreak`. |
| `ad-list` | Een lijst met advertenties die tijdens de opgegeven advertentie-einde moeten worden afgespeeld, verwijst naar de `List<Ad>` veld in `com.adobe.mediacore.timeline.advertising.AdBreak`. |

Het volgende codeblok definieert het JSON-object voor de array met advertenties.

```
"ad-list": [ 
    { 
        "url": "https://cdn.auditude.com/player/downloads/data/espn/ads/csx/prog_index.m3u8", 
        "duration": 15000, 
        "tag": "1st break - 1st ad" 
    }, 
    { 
        "url": "https://cdn.auditude.com/player/downloads/data/espn/ads/csx/prog_index.m3u8", 
        "duration": 30000, 
        "tag": "1st break - 2nd ad" 
    } 
], 
```

| Eigenschap | Beschrijving |
|---|---|
| `url` | De URL naar de advertentie-inhoud, verwijst naar het URL-veld in `com.adobe.mediacore.timeline.advertising.Ad`. |
| `duration` | De duur van de advertentie, verwijst naar het veld Duur in `com.adobe.mediacore.timeline.advertising.Ad`. |
| `tag` | Een beschrijvende tekenreeks. |
