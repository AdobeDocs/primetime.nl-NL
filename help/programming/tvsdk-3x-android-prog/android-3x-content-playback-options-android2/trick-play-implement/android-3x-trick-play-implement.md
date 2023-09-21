---
description: Wanneer gebruikers snel vooruit of snel terugspoelen door de media, zijn zij in de truc spelwijze. Stel de afspeelsnelheid van MediaPlayer in op een andere waarde dan 1 om de modus voor bedrieglijk afspelen te activeren.
title: Snel vooruit en terugspoelen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---

# Overzicht {#implement-fast-forward-and-rewind}

Wanneer gebruikers snel vooruit of snel terugspoelen door de media, zijn zij in de truc spelwijze. Stel de afspeelsnelheid van MediaPlayer in op een andere waarde dan 1 om de modus voor bedrieglijk afspelen te activeren.

U moet één waarde instellen om van snelheid te wisselen.

1. Ga van normale speelwijze (1x) naar truc speelwijze door het tarief op te plaatsen `MediaPlayer` op een toegestane waarde.

       De volgende informatie onthouden:
   
   * De `MediaPlayerItem` -klasse definieert de toegestane afspeelsnelheden.
   * TVSDK selecteert de dichtstbijzijnde toegestane snelheid als de opgegeven snelheid niet is toegestaan.

     In het volgende voorbeeld wordt de interne afspeelsnelheid van de speler ingesteld op de gewenste snelheid:

     ```
     import com.adobe.mediacore.MediaPlayer; 
     import com.adobe.mediacore.MediaPlayerItem; 
     import com.adobe.mediacore.MediaPlayerException; 
     import java.util.List; 
     import java.lang.Float; 
     
     private boolean setPlaybackRate(MediaPlayer player, float rate)  
       throws MediaPlayerException { 
         // Get list of playback rates that the media player supports 
         MediaPlayerItem item = player.getCurrentItem(); 
         if (item == null) return false; 
         List<Float> availableRates = player.getCurrentItem().getAvailablePlaybackRates(); 
     
         // Return false if requested rate is not supported 
         if (availableRates.indexOf(rate) == -1) return false; 
     
         // Otherwise set the playback rate to the requested rate  
         // (this can throw MediaPlayerException) 
         player.setRate(rate); 
         return true; 
     }
     ```

1. U kunt naar keuze luisteren op snelheid-verandering gebeurtenissen, die u op de hoogte brengen wanneer u om een tariefverandering verzoekt en wanneer de snelheidsverandering eigenlijk voorkomt.

TVSDK verzendt de volgende gebeurtenissen die betrekking hebben op truc-spelen:

* `MediaPlayerEvent.RATE_SELECTED`, wanneer de `rate` De waarde verandert in een andere waarde.

* `MediaPlayerEvent.RATE_PLAYING`, wanneer het afspelen wordt hervat met de geselecteerde frequentie.

  TVSDK verzendt deze gebeurtenissen wanneer de speler van de truc-afspeelmodus naar de normale afspeelmodus terugkeert.
