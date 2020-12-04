---
description: U kunt advertenties invoegen in VOD-inhoud.
seo-description: U kunt advertenties invoegen in VOD-inhoud.
seo-title: Tijdbereiken vervangen door een advertentie
title: Tijdbereiken vervangen door een advertentie
uuid: 8f09560c-bca3-4662-bc58-6c9cd0892476
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---


# Tijdbereiken vervangen door een advertentie {#replace-time-ranges-with-an-ad}

U kunt advertenties invoegen in VOD-inhoud.

De `TimeRanges` tussen `begin` en `end` in `localTime` worden verwijderd uit de tijdlijn. Deze bereiken worden vervangen door een `AdBreak` van `begin` tot `begin+replaceDuration`. Als `replacement-duration` niet als parameter bestaat, bepaalt de server de bepaling op teruggekeerde `Adbreak`.

>[!TIP]
>
>Geef altijd een `replacement-duration` op voor aangepaste bereiken. Als er geen advertenties zijn die dit aangepaste bereik moeten vervangen, geeft u een `replacement-duration` van 0 op.

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

