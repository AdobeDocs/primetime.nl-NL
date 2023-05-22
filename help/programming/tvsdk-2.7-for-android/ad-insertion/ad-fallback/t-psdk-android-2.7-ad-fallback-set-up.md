---
description: U kunt fallback inschakelen wanneer een inline VMAP-bestand een ongeldig mediatype bevat.
title: Definieer de fallback en het gedrag voor inline VMAP-advertenties
exl-id: 57fd1b89-bcee-4c23-88e7-7a576c47c6f9
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
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
