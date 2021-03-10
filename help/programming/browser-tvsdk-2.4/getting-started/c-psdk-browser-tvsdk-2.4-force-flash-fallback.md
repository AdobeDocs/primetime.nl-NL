---
description: De markering forceflash in de bronlijst forceert Flash fallback voor een URL. Voor deze URL kunt u Adobe Flash Player gebruiken om de inhoud af te spelen.
title: De Flash-fallback forceren met gebruik van de lijst met mediabronnen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 2%

---


# De Flash-fallback forceren met de mediabronlijst{#forcing-the-flash-fallback-using-the-media-source-list}

De markering forceflash in de bronlijst forceert Flash fallback voor een URL. Voor deze URL kunt u Adobe Flash Player gebruiken om de inhoud af te spelen.

In de lijst met mediabronnen (bijvoorbeeld in het bestand `sources.js`) kunt u `forceflash` instellen op `true`. Bijvoorbeeld:

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

