---
title: Speciale gevallen
description: Speciale gevallen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---


# Speciale gebruiksgevallen{#special-use-cases}

TVSDK geeft de voorkeur aan aangepaste bereikinstellingen boven standaard-advertentie-instellingen. Als bijvoorbeeld MARK-bereiken zijn gedefinieerd, worden de invoeginstellingen van de advertentie genegeerd. Als de waaiers van de VERVANGING worden bepaald, gebruikt TVSDK automatisch de `CustomRanges` signalerende wijze.

1. `ReplaceRange` zonder vervangende duur

   Als de vervangingsduur ontbreekt, wordt de daadwerkelijke vervangingsduur bepaald door de server. Het aantal advertenties dat in deze `AdBreak` wordt geplaatst, wordt ook bepaald door de server.

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

1. MARK en DELETE bereiken met vervangingsduur

   De extra vervangingsduur wordt genegeerd.
