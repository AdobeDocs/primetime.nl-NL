---
description: U kunt TimeRanges verwijderen tussen begin en eind in localTime van de chronologie.
seo-description: U kunt TimeRanges verwijderen tussen begin en eind in localTime van de chronologie.
seo-title: Bereiken verwijderen
title: Bereiken verwijderen
uuid: 637829a7-efa8-4b83-9a04-ef01c043621f
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Bereiken verwijderen{#delete-ranges}

U kunt TimeRanges verwijderen tussen begin en eind in localTime van de chronologie.

>[!TIP]
>
>Als u alleen bepaalde bereiken uit de inhoud wilt verwijderen, maakt u een `CustomRangeMetadata` instantie en geeft u het type op als een `DELETE` bewerking met de gedefinieerde aangepaste bereiken.

De advertentiekaart moet worden gebruikt zoals gedefinieerd door de advertentieserver.

1. U verwijdert bereiken met een Adobe Primetime-advertentie voor beslissingen:

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
       "title": "VOD - DELETE TimeRange with xm-replace_text Phrase Ads",
       "thumbnail": {
           "large": "https://example.com",
           "small": "https://example.com"
       },
       "type": "vod",
       "id": "vod_003"
   },
   ```

