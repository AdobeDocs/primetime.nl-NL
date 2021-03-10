---
description: Als u ondersteuning voor VPAID 2.0 wilt toevoegen, voegt u een aangepaste advertentieweergave en de juiste listeners toe.
title: VPAID 2.0-integratie implementeren
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '50'
ht-degree: 0%

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

