---
description: U kunt tijdintervallen in VOD-inhoud aanwijzen als en als einden.
title: Markeringsbereiken
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---


# Markeringsbereiken{#mark-ranges}

U kunt tijdintervallen in VOD-inhoud aanwijzen als en als einden.

In dit geval wordt `TimeRanges` tussen `begin` en `end` in `localTime` gemarkeerd als een `AdBreak` in de tijdlijn. Andere advertentie-instellingen worden genegeerd.

>[!NOTE]
>
>Als u alleen bepaalde bereiken in de inhoud wilt markeren als advertenties (zonder dynamische invoeging), maakt u een `CustomRangeMetadata`-instantie en geeft u het type op als een MARK-bewerking met de gedefinieerde aangepaste bereiken.

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

