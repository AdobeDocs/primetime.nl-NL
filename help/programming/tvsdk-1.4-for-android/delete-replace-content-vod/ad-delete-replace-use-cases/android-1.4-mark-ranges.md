---
description: U kunt tijdintervallen in VOD-inhoud aanwijzen als en als einden.
title: Markeringsbereiken
exl-id: cd661327-20b2-4a49-8002-6ecee86c2a2c
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---

# Markeringsbereiken{#mark-ranges}

U kunt tijdintervallen in VOD-inhoud aanwijzen als en als einden.

In dit geval: `TimeRanges` tussen de `begin` en `end` in `localTime` wordt gemarkeerd als een `AdBreak` in de tijdlijn. Andere advertentie-instellingen worden genegeerd.

>[!NOTE]
>
>Als u alleen bepaalde bereiken in de inhoud wilt markeren als advertenties (zonder dynamische invoeging), maakt u een `CustomRangeMetadata` en geeft u het type op als een MARK-bewerking met de gedefinieerde aangepaste bereiken.

1. Markeringsbereiken.

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
