---
description: Met de markering forceflash in de bronlijst forceert u Flash-fallback voor een URL. Voor deze URL kunt u de inhoud afspelen met Adobe Flash Player.
seo-description: Met de markering forceflash in de bronlijst forceert u Flash-fallback voor een URL. Voor deze URL kunt u de inhoud afspelen met Adobe Flash Player.
seo-title: Flash-fallback forceren met gebruik van de lijst met mediabronnen
title: Flash-fallback forceren met gebruik van de lijst met mediabronnen
uuid: 04b09734-15f7-4e7e-8802-344f550f9b05
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Flash-fallback forceren met gebruik van de lijst met mediabronnen{#forcing-the-flash-fallback-using-the-media-source-list}

Met de markering forceflash in de bronlijst forceert u Flash-fallback voor een URL. Voor deze URL kunt u de inhoud afspelen met Adobe Flash Player.

In de lijst met mediabronnen (bijvoorbeeld in het `sources.js` bestand) kunt u instellen `forceflash` op `true`. Bijvoorbeeld:

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

