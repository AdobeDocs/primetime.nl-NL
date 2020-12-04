---
description: Als u ondersteuning voor VPAID 2.0 wilt toevoegen, voegt u een aangepaste advertentieweergave en de juiste listeners toe.
seo-description: Als u ondersteuning voor VPAID 2.0 wilt toevoegen, voegt u een aangepaste advertentieweergave en de juiste listeners toe.
seo-title: VPAID 2.0-integratie implementeren
title: VPAID 2.0-integratie implementeren
uuid: fa5b9cdd-e684-4656-91b7-50781dc59e23
translation-type: tm+mt
source-git-commit: 25f97c8d296f71deddc8f9d12b97007ddf73f603
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 2%

---


# Implementeer VPAID 2.0-integratie {#implement-vpaid-integration}

Als u ondersteuning voor VPAID 2.0 wilt toevoegen, voegt u een aangepaste advertentieweergave en de juiste listeners toe.

U voegt als volgt VPAID 2.0-ondersteuning toe:

1. Voeg de aangepaste advertentieweergave toe aan de Player-interface wanneer de speler zich in de status PREPARED bevindt.

   ```java
   ... 
   private FrameLayout _playerFrame; 
       ... 
       case PREPARED: 
           ... 
           addCustomView(); 
   ... 
   private void addCustomView() { 
       ... 
       WebView view = (WebView)_mediaPlayer.getCustomAdView(); 
       ... 
       _playerFrame.addView(view);
   ```

1. Maak listeners en verwerk de gebeurtenissen die in gebeurtenislisteners worden beschreven.

   >[!IMPORTANT]
   >
   >In een VPAID 2.0-workflow is het voor aangepaste en weergaven erg belangrijk om uw `CustomAdView`-instantie te behouden over `AdBreak` start (gebeurtenis `AD_BREAK_START`) en `AdBreak` voltooit (gebeurtenis `AD_BREAK_COMPLETE`), vanaf het moment dat u de aangepaste en weergave maakt tot aan het moment dat u de aangepaste en weergavebewerking verwijdert. Maak dus niet elke keer dat een advertentie-einde begint, een aangepaste advertentie-weergave en verwijder deze op elk advertentie-einde voltooid.
   >
   >
   >Bovendien moet u alleen een aangepaste advertentieweergave maken als de speler de status PREPARED heeft,
   >
   >
   >Gooi de aangepaste advertentieweergave alleen weg wanneer de voorinstelling wordt aangeroepen. Bijvoorbeeld:
   >
   >
   ```
   >// on reset 
   >if (_mediaPlayer != null) { 
   >       _mediaPlayer.disposeCustomAdView(); 
   >       ... 
   >} 
   >```
   >
   >Tot slot moet u het verwijderen uit `FrameLayout` alvorens u uw douane ad mening verwijdert. Bijvoorbeeld:
   >
   >
   ```
   >if (_playerFrame != null) 
   >       _playerFrame.removeAllViews(); 
   >```
