---
description: U kunt advertenties invoegen in VOD-inhoud.
title: Tijdbereiken vervangen door een advertentie
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---

# Tijdbereiken vervangen door een advertentie{#replace-time-ranges-with-an-ad}

U kunt advertenties invoegen in VOD-inhoud.

In dit geval: `TimeRanges` tussen de `begin` en `end` in `localTime` worden verwijderd uit de tijdlijn. Zij worden vervangen door een `AdBreak` van `begin` tot `begin+replaceDuration`. Als de vervanging-duur niet als parameter bestaat, maakt de server de bepaling op teruggekeerde Adbreak.

>[!NOTE]
>
>Geef altijd een specifieke vervangende duur op voor aangepaste bereiken. Als er geen advertenties zijn die dit aangepaste bereik moeten vervangen, geeft u een vervangende duur op van 0.

Hiermee vervangt u bereiken door primetime- en beslissingsadvertenties.

```
{   
    "properties": [],
    "stream": {
        "manifests": [ {
            "url": 
              "https://d398890tia84ty.cloudfront.net/e2e-vod/cloudfront_vod_hls_tos_30fps.m3u8",
            "type": "hls"
        } ],
                 
        "metadata": {
            "time-ranges": {
                "type": "replace",
                "time-range-list": [ {
                    "begin": 0,
                    "end": 15000,
                    "replacement-duration": 15000 
                },
                {
                    "begin": 69000,
                    "end": 99000,
                    "replacement-duration": 30000
                },
                {
                    "begin": 251000,
                    "end": 281000,
                    "replacement-duration": 30000
                },
                {
                    "begin": 514000,
                    "end": 544000,
                    "replacement-duration": 30000
                } ]
            },
            "ad": {
                "targeting": [ {
                    "value": "MulAdsAvail12346",
                    "key": "osmfKeyMulAdsAvail12346"
                } ],
                "domain": "sandbox2.auditude.com",
                "mediaid": "psdk_000105",
                "zoneid": "121781"
            }     
        }
    },   
    "title": "VOD - Replace TimeRange with Auditude Ads",
    "thumbnail": {
        "large": "https://example.com",
        "small": "https://example.com"
    },
    "type": "vod",
    "id": "vod_003"
}
```
