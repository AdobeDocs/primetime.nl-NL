---
description: U kunt tijdintervallen in VOD-inhoud aanwijzen als en als einden.
seo-description: U kunt tijdintervallen in VOD-inhoud aanwijzen als en als einden.
seo-title: Markeringsbereiken
title: Markeringsbereiken
uuid: 6ae2adee-fb7a-4cef-a8e8-ecf671ed3660
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---


# Markeringsbereiken {#mark-ranges}

U kunt tijdintervallen in VOD-inhoud aanwijzen als en als einden.

De `TimeRanges` tussen `begin` en `end` in `localTime` zal als `AdBreak` in de chronologie worden gemerkt. Andere advertentie-instellingen worden genegeerd.

>[!TIP]
>
>Als u alleen bepaalde bereiken in de inhoud wilt markeren als advertenties, zonder dynamische invoeging, maakt u een `CustomRangeMetadata`-instantie en geeft u het type op als een `MARK`-bewerking met de gedefinieerde aangepaste bereiken.

1. Tik teken de bereiken:

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
                   "type": "mark",
               "adjust-seek-position" : true,   
                   "time-range-list": [
                     {
                        "begin": 0,
                        "end": 15000
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
   
                 }
            }           
       },   
       "title": "VOD - MARK TimeRanges and no ads",
       "thumbnail": {
           "large": "https://example.com",
           "small": "https://example.com"
          },
       "type": "vod",
       "id": "vod_004"
   }
   ```

