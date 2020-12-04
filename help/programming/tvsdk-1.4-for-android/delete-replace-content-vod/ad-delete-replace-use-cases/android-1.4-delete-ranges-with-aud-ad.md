---
description: U kunt TimeRanges verwijderen tussen begin en eind in localTime van de chronologie.
seo-description: U kunt TimeRanges verwijderen tussen begin en eind in localTime van de chronologie.
seo-title: Bereiken verwijderen
title: Bereiken verwijderen
uuid: 2f4afa0d-69e3-4929-8dbd-b553c8a64d96
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---


# Bereiken verwijderen{#delete-ranges}

U kunt TimeRanges verwijderen tussen begin en eind in localTime van de chronologie.

>[!NOTE]
>
>Als u alleen bepaalde bereiken uit de inhoud wilt verwijderen en de advertentiekaart moet worden gebruikt zoals gedefinieerd door de advertentieserver, maakt u een `CustomRangeMetadata`-instantie en geeft u het type op als een DELETE-bewerking met de gedefinieerde aangepaste bereiken.

Hiermee verwijdert u bereiken met een Adobe Primetime-advertentie.

```
{   
    "properties": [],
    "stream": {
        "manifests": [
            {
                "url": "https://xyz.cloudfront.net/e2e-vod/cloudfront_vod_hls_tos_30fps.m3u8",
                "type": "hls"
            }
        ],
     
        "metadata": {
            "time-ranges": {
                "type": "delete",
                "time-range-list": [
                    {
                        "begin": 0,
                        "end": 20000
                    },
                    {
                        "begin": 69000,
                        "end": 99000
                    },
                    {
                        "begin": 251000,
                        "end": 281000
                    },
                    {
                        "begin": 514000,
                        "end": 544000
                    }
                ]
     
            },
            "ad": {
                "targeting": [
                    {
                        "value": "MulAdsAvail12346",
                        "key": "osmfKeyMulAdsAvail12346"
                    }
                ],
                "domain": "sandbox2.auditude.com",
                "mediaid": "psdk_000105",
                "zoneid": "121781"
            }     
        }
    },   
    "title": "VOD - DELETE TimeRange with Primetime ad decisioning Ads",
    "thumbnail": {
        "large": "https://example.com",
        "small": "https://example.com"
    },
    "type": "vod",
    "id": "vod_003"
}
```

