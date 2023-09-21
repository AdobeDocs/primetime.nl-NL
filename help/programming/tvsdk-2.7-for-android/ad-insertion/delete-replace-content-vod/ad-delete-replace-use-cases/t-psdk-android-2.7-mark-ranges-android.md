---
description: U kunt tijdintervallen in VOD-inhoud aanwijzen als en als einden.
title: Markeringsbereiken
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---

# Markeringsbereiken {#mark-ranges}

U kunt tijdintervallen in VOD-inhoud aanwijzen als en als einden.

De `TimeRanges` tussen de `begin` en `end` in `localTime` wordt gemarkeerd als een `AdBreak` in de tijdlijn. Andere advertentie-instellingen worden genegeerd.

>[!TIP]
>
>Als u alleen bepaalde bereiken in de inhoud wilt markeren als advertenties, zonder dynamische invoeging, maakt u een `CustomRangeMetadata` -instantie en geeft u de tekst op als een `MARK` bewerking met de gedefinieerde aangepaste bereiken.

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
