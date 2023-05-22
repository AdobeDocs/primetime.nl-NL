---
title: Markeringsbereiken
description: Markeringsbereiken
copied-description: true
exl-id: 173769cd-6580-4461-9dbc-5bb2fed346d2
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '24'
ht-degree: 0%

---

# Markeringsbereiken{#mark-ranges}

Mark `TimeRanges` tussen de `begin` en `end` in `localTime` als `AdBreak` uit de tijdlijn. Andere advertentie-instellingen worden genegeerd.

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
