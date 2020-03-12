---
description: Als u ondersteuning voor VPAID 2.0 wilt toevoegen, voegt u een aangepaste advertentieweergave en de juiste listeners toe.
seo-description: Als u ondersteuning voor VPAID 2.0 wilt toevoegen, voegt u een aangepaste advertentieweergave en de juiste listeners toe.
seo-title: VPAID 2.0-integratie implementeren
title: VPAID 2.0-integratie implementeren
uuid: fa5b9cdd-e684-4656-91b7-50781dc59e23
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# VPAID 2.0-integratie implementeren {#implement-vpaid-integration}

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
   >In een VPAID 2.0-workflow is het voor aangepaste en weergaven erg belangrijk om uw `CustomAdView` instantie te behouden bij `AdBreak` het starten (gebeurtenis `AD_BREAK_START`) en `AdBreak` voltooien (gebeurtenis `AD_BREAK_COMPLETE`), vanaf het moment dat u de aangepaste advertentie maakt tot aan het moment dat u deze verwijdert. Maak dus niet elke keer dat een advertentie-einde begint, een aangepaste advertentie-weergave en verwijder deze op elk advertentie-einde voltooid.
   >
   >
   >Bovendien moet u alleen een aangepaste advertentieweergave maken als de speler de status PREPARED heeft,
   >
   >
   >Gooi de aangepaste advertentieweergave alleen weg wanneer de voorinstelling wordt aangeroepen. Bijvoorbeeld:    >
   >
   >
   ```>
   >// on reset 
   >if (_mediaPlayer != null) { 
   >       _mediaPlayer.disposeCustomAdView(); 
   >       ... 
   >} 
   >
   >
   ```   >
   >



   >Voordat u de aangepaste advertentieweergave kunt verwijderen, moet u deze eerst uit het deelvenster verwijderen `FrameLayout`. Bijvoorbeeld:    >
   >
   >
   ```>
   if (_playerFrame != null) 
      _playerFrame.removeAllViews(); 
   ```
