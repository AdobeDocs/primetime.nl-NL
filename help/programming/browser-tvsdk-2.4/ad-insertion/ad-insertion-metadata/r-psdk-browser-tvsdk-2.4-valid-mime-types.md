---
description: Een advertentie kan meerdere creatieve elementen bevatten, waaruit een advertentie kan worden afgespeeld.
seo-description: Een advertentie kan meerdere creatieve elementen bevatten, waaruit een advertentie kan worden afgespeeld.
seo-title: Geldige mime-typen
title: Geldige mime-typen
uuid: ab2baac9-a9ef-44f1-83a1-2e6e471e3231
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Geldige mime-typen{#valid-mime-types}

Een advertentie kan meerdere creatieve elementen bevatten, waaruit een advertentie kan worden afgespeeld.

Met mime-typen kunt u opgeven aan welke gebruikers van het creatieve type prioriteit kunnen geven. De mime types die door gebruikers en de mime types worden gespecificeerd die door Browser TVSDK worden gesteund worden gebruikt om te bepalen welke creatief zal voorrang krijgen.

U kunt als volgt de geldige mime-typen instellen in Browser-TVSDK:

```js
var auditudeSettings = new AdobePSDK.AuditudeSettings(); 
var mimeTypes = [“video/mp4”, “application/x-mpegURL”]; 
auditudeSettings.validMimeTypes = mimeTypes; 
```

waarbij `mimeTypes` een array van tekenreeksen is en elke tekenreeks een mime-type vertegenwoordigt.

Als meerdere mediabestanden worden geretourneerd voor een advertentie, is de selectie afhankelijk van de volgorde waarin de mediabestanden in de `validMimeTypes` array worden weergegeven. De mime-typen met een lagere index krijgen een voorkeur boven de typen met een hogere index.
