---
description: Als u ondersteuning voor VPAID 2.0 wilt toevoegen, voegt u een aangepaste advertentieweergave en de juiste listeners toe.
seo-description: Als u ondersteuning voor VPAID 2.0 wilt toevoegen, voegt u een aangepaste advertentieweergave en de juiste listeners toe.
seo-title: VPAID 2.0-integratie implementeren
title: VPAID 2.0-integratie implementeren
uuid: 7d11ffd8-240c-4a95-94e6-ff4417c8942e
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# VPAID 2.0-integratie implementeren{#implement-vpaid-integration}

Als u ondersteuning voor VPAID 2.0 wilt toevoegen, voegt u een aangepaste advertentieweergave en de juiste listeners toe.

U voegt als volgt VPAID 2.0-ondersteuning toe:

1. Voeg de aangepaste advertentieweergave toe aan de Player-interface.

   ```java
   _playerFrame.addView(mediaPlayer.createCustomAdView());
   ```

1. Voeg een listener toe voor aangepaste advertentiegebeurtenissen.

   ```java
   mediaplayer.addEventListener(MediaPlayer.Event.CUSTOM_AD,  
     _customAdEventListener);
   ```

