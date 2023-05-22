---
description: Een advertentie kan meerdere creatieve elementen bevatten, waaruit een advertentie kan worden afgespeeld.
title: Geldige mime-typen
exl-id: 878cae20-2a94-4795-8908-be7daffefb41
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
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

waar `mimeTypes` is een array van tekenreeksen en elke tekenreeks vertegenwoordigt een mime-type.

Als meerdere mediabestanden worden geretourneerd voor een advertentie, is de selectie afhankelijk van de volgorde waarin de mediabestanden worden weergegeven in `validMimeTypes` array. De mime-typen met een lagere index krijgen een voorkeur boven de typen met een hogere index.
