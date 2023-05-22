---
title: Automatisch afspelen op iOS
description: Automatisch afspelen op iOS
copied-description: true
exl-id: 591e8f74-63c3-4f74-9df4-024eb8aab646
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---

# Automatisch afspelen op iOS{#autoplay-on-ios}

Met de implementatie van de volume-API van AdobePSDK.MediaPlayer kan inhoud automatisch worden afgespeeld op apparaten met iOS versie 10 of hoger. iOS staat automatisch afspelen alleen toe wanneer het volume wordt gedempt. Wanneer het volume is ingesteld op nul, stelt de API de `muted` eigenschap van de videotag naar `true`anders `muted` eigenschap is ingesteld op `false`. De `play` API start het afspelen zonder tussenkomst van de gebruiker of beweging van de gebruiker.

Voor automatisch afspelen op iPhone stelt u bovendien de optie `playsInline` eigendom van de `video` label naar `true`.

```
videoDiv.getElementsByTagName('video')[0].playsInline = true;
```

>[!NOTE]
>
>Gebruik van `playsInline` wordt het afspelen gestart zonder de modus Volledig scherm.
