---
description: U kunt fallback inschakelen wanneer een inline VMAP-bestand een ongeldig mediatype bevat.
seo-description: U kunt fallback inschakelen wanneer een inline VMAP-bestand een ongeldig mediatype bevat.
seo-title: Definieer de fallback en het gedrag voor inline VMAP-advertenties
title: Definieer de fallback en het gedrag voor inline VMAP-advertenties
uuid: a7b5c9a6-f546-4d3a-9d49-7e5484acff7a
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---


# Definieer fallback en gedrag voor inline VMAP-advertenties {#define-fallback-ad-behavior-for-vmap-inline-ads}

U kunt fallback inschakelen wanneer een inline VMAP-bestand een ongeldig mediatype bevat.

1. Stel `setFallbackOnInvalidCreativeEnabled` in op `true` om VMAP terug te laten vallen wanneer het mediatype voor een lineaire/inline-advertentie ongeldig is voor HLS.

   De standaardwaarde is `false`. Als een lineaire advertentie mislukt omdat deze een ongeldig mediatype heeft of omdat de advertentie niet opnieuw kan worden verpakt, staat deze markering toe dat Primetime en de beslissing hetzelfde fallback-gedrag volgen als wanneer de advertentie een lege VAST-wrapper was.

   ```java
   AuditudeSettings result = new AuditudeSettings(); 
   result.setFallbackOnInvalidCreative(true);
   ```

