---
description: U kunt fallback inschakelen wanneer een inline VMAP-bestand een ongeldig mediatype bevat.
title: Definieer de fallback en het gedrag voor inline VMAP-advertenties
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '108'
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
