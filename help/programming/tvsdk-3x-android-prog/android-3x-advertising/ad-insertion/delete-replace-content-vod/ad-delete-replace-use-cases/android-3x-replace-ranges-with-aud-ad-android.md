---
description: U kunt advertenties invoegen in VOD-inhoud.
title: Tijdbereiken vervangen door een advertentie
exl-id: bee5308a-f867-4824-84a8-751746785971
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 0%

---

# Tijdbereiken vervangen door een advertentie {#replace-time-ranges-with-an-ad}

U kunt advertenties invoegen in VOD-inhoud.

De `TimeRanges` tussen de `begin` en `end` in `localTime` worden verwijderd uit de tijdlijn. Deze bereiken worden vervangen door een `AdBreak` van `begin` tot `begin+replaceDuration`. Als de `replacement-duration` bestaat niet als parameter, de server maakt de bepaling op teruggekeerde `Adbreak`.

>[!TIP]
>
>U moet altijd een `replacement-duration` voor aangepaste bereiken. Als er geen advertenties zijn die dit aangepaste bereik moeten vervangen, voert u een `replacement-duration` van 0.

1. U kunt als volgt de bereiken vervangen door Primetime en beslissingsadvertenties:

   ```
   {   
       "properties": [],
       "stream": {
           "manifests": [
               {
                   "url": "https://d398890tia84ty.cloudfront.net/e2e-vod/cloudfront_vod_hls_tos_30fps.m3u8",
                   "type": "hls"
               }
           ],
           "metadata": {
               "time-ranges": {
                   "type": "replace",
                   "time-range-list": [
                       {
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
       "title": "VOD - Replace TimeRange with Auditude Ads",
       "thumbnail": {
           "large": "https://example.com",
           "small": "https://example.com"
       },
       "type": "vod",
       "id": "vod_003"
   }
   ```
