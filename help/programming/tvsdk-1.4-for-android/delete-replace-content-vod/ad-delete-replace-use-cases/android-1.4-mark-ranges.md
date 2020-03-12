---
description: U kunt tijdintervallen in VOD-inhoud aanwijzen als en als einden.
seo-description: U kunt tijdintervallen in VOD-inhoud aanwijzen als en als einden.
seo-title: Markeringsbereiken
title: Markeringsbereiken
uuid: eb99a1c2-6c0c-40a4-bac2-98dce45acfad
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Markeringsbereiken{#mark-ranges}

U kunt tijdintervallen in VOD-inhoud aanwijzen als en als einden.

In dit geval wordt `TimeRanges` tussen de `begin` en `end` binnen `localTime` gemarkeerd als een `AdBreak` in de tijdlijn. Andere advertentie-instellingen worden genegeerd.

>[!NOTE]
>
>Als u alleen bepaalde bereiken in de inhoud wilt markeren als advertenties (zonder dynamische invoeging), maakt u een `CustomRangeMetadata` instantie en geeft u de tekst op als een MARK-bewerking met de gedefinieerde aangepaste bereiken.

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

