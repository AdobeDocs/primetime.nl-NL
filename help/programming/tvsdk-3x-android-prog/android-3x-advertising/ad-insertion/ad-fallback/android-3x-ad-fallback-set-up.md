---
description: U kunt fallback inschakelen wanneer een inline VMAP-bestand een ongeldig mediatype bevat.
title: Definieer de fallback en het gedrag voor inline VMAP-advertenties
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 0%

---

# Definieer de fallback en het gedrag voor inline VMAP-advertenties {#define-fallback-ad-behavior-for-vmap-inline-ads}

U kunt fallback inschakelen wanneer een inline VMAP-bestand een ongeldig mediatype bevat.

1. Set `setFallbackOnInvalidCreativeEnabled` tot `true` om VMAP terug te vallen wanneer het media type voor lineair/gealigneerd en ongeldig voor HLS is.

   De standaardwaarde is `false`. Als een lineaire advertentie mislukt omdat deze een ongeldig mediatype heeft of omdat de advertentie niet opnieuw kan worden verpakt, staat deze markering toe dat Primetime en de beslissing hetzelfde fallback-gedrag volgen als wanneer de advertentie een lege VAST-wrapper was.

   ```java
   AuditudeSettings result = new AuditudeSettings(); 
   result.setFallbackOnInvalidCreative(true);
   ```
