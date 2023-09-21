---
description: Met de markering forceflash in de bronlijst wordt voor een URL een Flash-fallback geforceerd. Voor deze URL kunt u Adobe Flash Player gebruiken om de inhoud af te spelen.
title: De Flash laten terugvallen met gebruik van de mediabronlijst
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---

# De Flash laten terugvallen met gebruik van de mediabronlijst{#forcing-the-flash-fallback-using-the-media-source-list}

Met de markering forceflash in de bronlijst wordt voor een URL een Flash-fallback geforceerd. Voor deze URL kunt u Adobe Flash Player gebruiken om de inhoud af te spelen.

In de lijst met mediabronnen (bijvoorbeeld in de `sources.js` bestand) kunt instellen `forceflash` tot `true`. Bijvoorbeeld:

```js
{ 
        "title":"Title of the item listed in the media source list",
        "description":"Description of the item listed in the media source list",
        "isLive":true,
        "content":[ 
            { 
                "format":"HLS",
                "url":"https://path_to_HLS_stream.m3u8"
            },
 
        ],
        "forceflash" : true
},
```
