---
title: JSON-object voor aangepaste advertentiemarkeringen
description: JSON-object voor aangepaste advertentiemarkeringen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---


# JSON-object voor aangepaste advertentiemarkeringen {#json-object-for-custom-ad-markers}

In het codeblok hieronder wordt het JSON-object &quot;details&quot; gedefinieerd wanneer het type aangepaste advertentiemarkeringen is.

De MetadataNode die door IFeedItemAdapter:getStreamMetadata() wordt geretourneerd, bevat 2 items:
1. een item met de sleutel van het type `com.adobe.mediacore.metadata.DefaultMetadataKeys.CUSTOM_AD_MARKERS_METADATA_KEY` en de waarde van een instantie van de MetadataNode die door `TimeRangeCollection.toMetadata()` is geretourneerd.
1. De tweede vermelding heeft een sleutel van het type `com.adobe.mediacore.metadata.DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED` met de waarde van *adjust-seek-position* hieronder attributen.

```
“metadata”: {
    “ad” :  {
        “type”: “custom ad markers”,
        “details”: {
            "adjust-seek-position": true,
            "time-ranges": [
                {
                    "begin": 5000,
                    "end":15000
                },
                {
                    "begin": 120000,
                    "end":135000
                }
            ]
        }
    }
}
```

| Eigenschap | Beschrijving |
|---|---|
| adjust-seek-positie | true of false, gebruikt om de waarde van de sleutel com.adobe.mediacore.metadata.DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED in te stellen in de MetadataNode. |
| tijdsbereik | Een array van JSON-objecten die het tijdbereik voor elke advertentiemarkering aangeeft. Elke JSON-objectvermelding verwijst naar een instantie van com.adobe.mediacore.utils.TimeRange. |
| time-ranges.begin | Waarde in ms die de begintijd van de advertentiemarkering aangeeft. |
| time-ranges.end | Waarde in ms die de eindtijd van de advertentiemarkering aangeeft. |

Raadpleeg de TVSDK-documentatie voor meer informatie over de werking van aangepaste advertentiemarkeringen.
