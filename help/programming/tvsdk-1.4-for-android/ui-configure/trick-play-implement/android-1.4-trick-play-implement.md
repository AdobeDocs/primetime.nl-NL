---
description: Wanneer gebruikers snel vooruit of snel terugspoelen door de media, zijn zij in de truc spelwijze. Als u de speelmodus voor truc wilt inschakelen, moet u de afspeelsnelheid van MediaPlayer instellen op een andere waarde dan 1.
title: Snel vooruit en terugspoelen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Overzicht {#implement-fast-forward-and-rewind-overview}

Wanneer gebruikers snel vooruit of snel terugspoelen door de media, zijn zij in de truc spelwijze. Als u de speelmodus voor truc wilt inschakelen, moet u de afspeelsnelheid van MediaPlayer instellen op een andere waarde dan 1.

U moet één waarde instellen om van snelheid te wisselen.

1. Ga van normale speelwijze (1x) naar truc speelwijze door het tarief op te plaatsen `MediaPlayer` op een toegestane waarde.

   * De `MediaPlayerItem` -klasse definieert de toegestane afspeelsnelheden.
   * TVSDK selecteert de dichtstbijzijnde toegestane snelheid als de opgegeven snelheid niet is toegestaan.

   In dit voorbeeld wordt de interne afspeelsnelheid van de speler ingesteld op de gewenste snelheid.

   ```java
   import com.adobe.mediacore.MediaPlayer; 
   import com.adobe.mediacore.MediaPlayerItem; 
   import com.adobe.mediacore.MediaPlayerException; 
   import java.util.List; 
   import java.lang.Float; 
   
   private boolean setPlaybackRate(MediaPlayer player, float rate) throws MediaPlayerException  
   { 
       //Get list of playback rates that the media player supports 
       MediaPlayerItem item = player.getCurrentItem(); 
       if(item == null) return false; 
       List<Float> availableRates = player.getCurrentItem().getAvailablePlaybackRates(); 
   
       //Return false if requested rate is not supported 
       if(availableRates.indexOf(rate) == -1) return false; 
   
       //Otherwise set the playback rate to the requested rate  
       //(this can throw MediaPlayerException) 
       player.setRate(rate); 
       return true; 
   }
   ```

1. U kunt naar keuze luisteren op snelheid-verandering gebeurtenissen, die u laten weten wanneer u om een tariefverandering vroeg en wanneer een snelheidsverandering eigenlijk gebeurt.

       TVSDK verzendt de volgende gebeurtenissen met betrekking tot truc-play:
   
   * `AdobePSDK.PSDKEventType.RATE_SELECTED` wanneer de `rate` De waarde verandert in een andere waarde.

   * `AdobePSDK.PSDKEventType.RATE_PLAYING` wanneer het afspelen wordt hervat met de geselecteerde frequentie.

     TVSDK verzendt beide gebeurtenissen wanneer de speler van de truc-spelmodus naar de normale afspeelmodus terugkeert.
