---
description: De markering forceflash in de bronlijst forceert Flash fallback voor een URL. Voor deze URL kunt u Adobe Flash Player gebruiken om de inhoud af te spelen.
title: De Flash-fallback forceren met gebruik van de lijst met mediabronnen
exl-id: 657bf9b1-d911-489d-80ca-2956b008431b
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---

# De Flash-fallback forceren met gebruik van de lijst met mediabronnen{#forcing-the-flash-fallback-using-the-media-source-list}

De markering forceflash in de bronlijst forceert Flash fallback voor een URL. Voor deze URL kunt u Adobe Flash Player gebruiken om de inhoud af te spelen.

In de lijst met mediabronnen (bijvoorbeeld in het dialoogvenster `sources.js` bestand), kunt u instellen `forceflash` tot `true`. Bijvoorbeeld:

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
