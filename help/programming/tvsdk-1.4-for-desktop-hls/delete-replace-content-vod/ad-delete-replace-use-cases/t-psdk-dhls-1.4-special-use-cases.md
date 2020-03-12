---
description: 'null'
seo-description: 'null'
seo-title: Speciale gevallen
title: Speciale gevallen
uuid: 066bc256-4fdf-4083-b23e-0a916b3b532f
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Speciale gevallen{#special-use-cases}

TVSDK geeft de voorkeur aan aangepaste bereikinstellingen boven standaard-advertentie-instellingen. Als bijvoorbeeld MARK-bereiken zijn gedefinieerd, worden de invoeginstellingen van de advertentie genegeerd. Als de waaiers van de VERVANGING worden bepaald, gebruikt TVSDK automatisch de het `CustomRanges` signaleren wijze.

1. `ReplaceRange` zonder vervangende duur

   Als de vervangingsduur ontbreekt, wordt de daadwerkelijke vervangingsduur bepaald door de server. Het aantal advertenties dat in dit bestand wordt geplaatst, `AdBreak` wordt ook bepaald door de server.

   ```
   {
       "properties": [],
       "stream": {
           "manifests": [ {
               "url": "https://. . ./vanilla/index.m3u8",
               "type": "hls"
           } ],
           "metadata": {
               "signaling-mode": "custom time ranges",
               "time-ranges": {
                   "type": "replace",
                   "adjust-seek-position": true,
                   "time-range-list": [{
                   "begin": 0,
                   "end": 30000
               }, {
                   "begin": 60000,
                   "end": 75000
               }, {
                   "begin": 255000,
                   "end": 300000
               } ]
               },
               "ad": {             
                   "domain": "sandbox2.auditude.com",
                   "mediaid": "psdk_000105",
                   "zoneid": "121781"
               }     
           }
       },
       "title": "Verify 30Sec Pre-Roll, 15 Sec Mid roll Ad and 
       45 second Post-Roll can be replaced in one shot.",
       "thumbnail": {
           "large": "https://example.com",
           "small": "https://example.com"
       },
       "type": "vod",
       "id": "vod_001"
   }
   ```

1. MARK- en DELETE-bereiken met vervangende duur

   De extra vervangingsduur wordt genegeerd.
