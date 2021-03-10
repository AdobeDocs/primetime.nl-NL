---
title: JSON-object voor directe en automatische regeleinden
description: Geeft het JSON-object in detail wanneer de tekstwaarde direct is en wordt onderbroken
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---


# JSON-object voor directe ad-einden{#json-object-for-direct-ad-breaks}

In het volgende codeblok worden de details van het JSON-object gedefinieerd wanneer de waarde van het type direct is en wordt afgebroken.

De `MetadataNode` die door `IFeedItemAdapter:getStreamMetadata()` is geretourneerd, bevat een item met de sleutel van het type `com.adobe.mediacore.metadata.DefaultMetadataKeys.JSON_METADATA_KEY` en de waarde van een tekenreeksrepresentatie van de details hieronder in de waarde van het JSON-object.

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
| `tag` | Een tekenreeks die wordt toegewezen aan het tagveld in `com.adobe.mediacore.timeline.advertising.AdBreak`. |
| `time` | Geeft de begintijd voor het ad-einde aan, wordt toegewezen aan het tijdveld in `com.adobe.mediacore.timeline.advertising.AdBreak`. De waarde 0 geeft een advertentie vóór de rol aan. |
| `replace` | Hiermee wordt de vervangingsduur van het advertentiepad aangegeven. Deze wordt toegewezen aan het veld `replaceDuration` in `com.adobe.mediacore.timeline.advertising.AdBreak`. |
| `ad-list` | Een lijst met advertenties die tijdens de opgegeven advertentie-einde moeten worden afgespeeld, verwijst naar het veld `List<Ad>` in `com.adobe.mediacore.timeline.advertising.AdBreak`. |

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
| `duration` | De duur van de advertentie, wordt toegewezen aan het duurveld in `com.adobe.mediacore.timeline.advertising.Ad`. |
| `tag` | Een beschrijvende tekenreeks. |

