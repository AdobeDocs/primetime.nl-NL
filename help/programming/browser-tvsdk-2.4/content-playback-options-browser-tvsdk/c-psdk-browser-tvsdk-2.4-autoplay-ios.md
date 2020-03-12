---
description: 'null'
seo-description: 'null'
seo-title: Automatisch afspelen op iOS
title: Automatisch afspelen op iOS
uuid: d15bad24-be50-49e5-90f4-68dbda96fb6d
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Automatisch afspelen op iOS{#autoplay-on-ios}

Met de implementatie van de volume-API van AdobePSDK.MediaPlayer kan inhoud automatisch worden afgespeeld op apparaten met iOS versie 10 of hoger. In iOS is automatisch afspelen alleen toegestaan wanneer het volume wordt gedempt. Wanneer het volume op nul wordt geplaatst, plaatst API het `muted` bezit van de videomarkering aan `true`, anders wordt het `muted` bezit geplaatst aan `false`. De `play` API start het afspelen zonder tussenkomst van de gebruiker of beweging van de gebruiker.

Voor automatisch afspelen op iPhone stelt u bovendien de `playsInline` eigenschap van de `video` tag in op `true`.

```
videoDiv.getElementsByTagName('video')[0].playsInline = true;
```

>[!NOTE]
>
>Met `playsInline` eigenschap wordt het afspelen gestart zonder de modus Volledig scherm.

