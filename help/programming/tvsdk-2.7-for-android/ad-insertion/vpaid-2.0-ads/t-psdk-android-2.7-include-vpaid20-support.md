---
description: Als u ondersteuning voor VPAID 2.0 wilt toevoegen, voegt u een aangepaste advertentieweergave en de juiste listeners toe.
title: VPAID 2.0-integratie implementeren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

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
   >In een VPAID 2.0-workflow is het voor aangepaste en weergaven erg belangrijk dat u uw `CustomAdView` instantie over `AdBreak` start (gebeurtenis) `AD_BREAK_START`) en `AdBreak` completes (gebeurtenis) `AD_BREAK_COMPLETE`), vanaf het moment dat u de aangepaste advertentie maakt tot aan het moment dat u deze verwijdert. Maak dus niet elke keer dat een advertentie-einde begint, een aangepaste advertentie-weergave en verwijder deze op elk advertentie-einde voltooid.
   >
   >
   >Bovendien moet u alleen een aangepaste advertentieweergave maken als de speler de status PREPARED heeft,
   >
   >
   >Gooi de aangepaste advertentieweergave alleen weg wanneer de voorinstelling wordt aangeroepen. Bijvoorbeeld:
   >
   >```
   >// on reset 
   >if (_mediaPlayer != null) { 
   >       _mediaPlayer.disposeCustomAdView(); 
   >       ... 
   >} 
   >```
   >
   >Voordat u de aangepaste advertentieweergave kunt verwijderen, moet u deze verwijderen uit het dialoogvenster `FrameLayout`. Bijvoorbeeld:
   >
   >```
   >if (_playerFrame != null) 
   >       _playerFrame.removeAllViews(); 
   >```
