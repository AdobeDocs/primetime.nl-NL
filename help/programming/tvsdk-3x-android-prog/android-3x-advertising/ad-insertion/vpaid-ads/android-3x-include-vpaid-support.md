---
description: Als u ondersteuning voor VPAID 2.0 wilt toevoegen, voegt u een aangepaste advertentieweergave en de juiste listeners toe.
title: VPAID 2.0-integratie implementeren
exl-id: a0d9a370-8fb6-4246-b59d-3b7c0b043bed
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# VPAID 2.0-integratie implementeren {#implement-vpaid-integration}

Als u ondersteuning voor VPAID 2.0 wilt toevoegen, voegt u een aangepaste advertentieweergave en de juiste listeners toe.

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

1. Listeners maken en de in [Gebeurtenissen](../../../../tvsdk-3x-android-prog/android-3x-events-notifications/events-summary/android-3x-events-summary.md).

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
   >
   ```
   >// on reset 
   >if (_mediaPlayer != null) { 
   >       _mediaPlayer.disposeCustomAdView(); 
   >       ... 
   >} 
   >
   >```
   >
   >Voordat u de aangepaste advertentieweergave kunt verwijderen, moet u deze verwijderen uit het dialoogvenster `FrameLayout`. Bijvoorbeeld:
   >
   >
   ```
   >if (_playerFrame != null) 
   >       _playerFrame.removeAllViews(); 
   >```
