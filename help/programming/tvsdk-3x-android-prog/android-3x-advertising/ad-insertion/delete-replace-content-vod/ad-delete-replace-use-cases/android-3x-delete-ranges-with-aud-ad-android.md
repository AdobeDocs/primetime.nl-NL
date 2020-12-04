---
description: U kunt TimeRanges verwijderen tussen begin en eind in localTime van de chronologie.
seo-description: U kunt TimeRanges verwijderen tussen begin en eind in localTime van de chronologie.
seo-title: Bereiken verwijderen
title: Bereiken verwijderen
uuid: 2aaea7a0-5d52-49a1-901c-f71e4b081d91
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---


# Bereiken {#delete-ranges} verwijderen

U kunt `TimeRanges` tussen `begin` en `end` in `localTime` uit de tijdlijn verwijderen.

>[!TIP]
>
>Als u alleen bepaalde bereiken uit de inhoud wilt verwijderen, maakt u een `CustomRangeMetadata`-instantie en geeft u het type op als een `DELETE`-bewerking met de gedefinieerde aangepaste bereiken.

De advertentiekaart moet worden gebruikt zoals gedefinieerd door de advertentieserver.

1. U verwijdert bereiken met een Adobe Primetime en een beslissingsadvertentie:

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
