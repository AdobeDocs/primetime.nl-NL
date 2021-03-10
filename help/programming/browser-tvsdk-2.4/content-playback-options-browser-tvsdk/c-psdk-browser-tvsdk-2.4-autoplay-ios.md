---
title: Automatisch afspelen op iOS
description: Automatisch afspelen op iOS
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---


# Automatisch afspelen op iOS{#autoplay-on-ios}

Met de implementatie van de volume-API van AdobePSDK.MediaPlayer kan inhoud automatisch worden afgespeeld op apparaten met iOS versie 10 of hoger. In iOS is automatisch afspelen alleen toegestaan wanneer het volume wordt gedempt. Wanneer het volume is ingesteld op nul, stelt de API de eigenschap `muted` van de videotag in op `true`, anders wordt de eigenschap `muted` ingesteld op `false`. Met de API `play` wordt het afspelen gestart zonder tussenkomst van de gebruiker of beweging van de gebruiker.

Voor automatisch afspelen op iPhone stelt u bovendien de eigenschap `playsInline` van de tag `video` in op `true`.

```
videoDiv.getElementsByTagName('video')[0].playsInline = true;
```

>[!NOTE]
>
>Met de eigenschap `playsInline` wordt het afspelen gestart zonder de modus Volledig scherm.

