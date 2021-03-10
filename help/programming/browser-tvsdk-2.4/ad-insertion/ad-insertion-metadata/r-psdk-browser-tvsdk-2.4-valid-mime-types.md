---
description: Een advertentie kan meerdere creatieve elementen bevatten, waaruit een advertentie kan worden afgespeeld.
title: Geldige mime-typen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 0%

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

Als er meerdere mediabestanden worden geretourneerd voor een advertentie, is de selectie afhankelijk van de volgorde waarin de mediabestanden in `validMimeTypes`-array worden weergegeven. De mime-typen met een lagere index krijgen een voorkeur boven de typen met een hogere index.
