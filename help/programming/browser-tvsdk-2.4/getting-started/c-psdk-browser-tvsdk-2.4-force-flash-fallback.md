---
description: De markering forceflash in de bronlijst forceert Flash fallback voor een URL. Voor deze URL kunt u Adobe Flash Player gebruiken om de inhoud af te spelen.
seo-description: De markering forceflash in de bronlijst forceert Flash fallback voor een URL. Voor deze URL kunt u Adobe Flash Player gebruiken om de inhoud af te spelen.
seo-title: De Flash-fallback forceren met gebruik van de lijst met mediabronnen
title: De Flash-fallback forceren met gebruik van de lijst met mediabronnen
uuid: 04b09734-15f7-4e7e-8802-344f550f9b05
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 1%

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

