---
description: 'null'
seo-description: 'null'
seo-title: Markeringsbereiken
title: Markeringsbereiken
uuid: d98efb92-701e-4ee2-b574-823c1e5d5149
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Markeringsbereiken{#mark-ranges}

Markeren `TimeRanges` tussen de tijdlijn `begin` en `end` in `localTime` als een `AdBreak` van de tijdlijn. Andere advertentie-instellingen worden genegeerd.

1. Tijdbereiken markeren.

   ```
   {   
       "properties": [],
       "stream": {
           "manifests": [ {
               "url": "https://d398890tia84ty.cloudfront.net/e2e-vod/cloudfront_vod_hls_tos_30fps.m3u8",
               "type": "hls"
           } ],
           "metadata": {
               "time-ranges": {
                   "type": "mark",
                   "adjust-seek-position" : true,   
                   "time-range-list": [ {
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
                   } ]
   
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

