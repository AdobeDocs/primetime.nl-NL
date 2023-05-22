---
description: TVSDK ondersteunt het zoeken naar een specifieke positie (tijd) waar de stream een afspeellijst met schuifvensters is, zowel in video op aanvraag (VOD) als in live streams.
title: Een zoekbalk weergeven met de huidige afspeelpositie
exl-id: 8076521b-579d-491f-97de-c7b57daa9b2e
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%

---

# Een zoekbalk weergeven met de huidige afspeelpositie {#display-a-seek-scrub-bar-with-the-current-playback-position}

TVSDK ondersteunt het zoeken naar een specifieke positie (tijd) waar de stream een afspeellijst met schuifvensters is, zowel in video op aanvraag (VOD) als in live streams.

>[!IMPORTANT]
>
>Zoeken in een live stream is alleen toegestaan voor DVR.

1. Stel callbacks in voor zoeken.

       Zoeken is asynchroon, dus verzendt TVSDK de volgende gebeurtenissen met betrekking tot zoeken:
   
   * `QOSEventListener.onSeekStart` - De zoekactie begint.
   * `QOSEventListener.onSeekComplete` - Zoek succesvol.
   * `QOSEventListener.onOperationFailed` - Seek is mislukt.

1. Wacht tot de speler zich in een geldige staat bevindt om te zoeken.

   Geldige statussen worden BEREID, VOLTOOID, GEPAUZEERD en AFGESPEELD.

1. De native zoekbalk gebruiken om in te stellen `OnSeekBarChangeListener` om te zien wanneer de gebruiker scrubt.
1. Luisteren naar `QOSEventListener.onOperationFailed` en nemen passende maatregelen.

   Deze gebeurtenis geeft de juiste waarschuwing door. Uw toepassing bepaalt hoe u verdergaat, bijvoorbeeld door opnieuw te zoeken of door te gaan met afspelen vanaf de vorige positie.

1. Wacht tot TVSDK de `QOSEventListener.onSeekComplete` callback.
1. Haal de definitieve aangepaste spelpositie terug gebruikend de positieparameter van callback.

   Dit is belangrijk omdat de werkelijke startpositie na de zoekactie kan verschillen van de gewenste positie. Het afspeelgedrag kan worden beïnvloed als een zoekopdracht of een andere herpositionering halverwege een advertentie-einde eindigt of als een zoekactie wordt overgeslagen en afgebroken.

1. Gebruik de positiegegevens wanneer u een zoekbalk weergeeft.

<!--<a id="example_9657AA855B6A4355B0E7D854596FFB54"></a>-->

**Voorbeeld van zoeken**

In dit voorbeeld scrubt de gebruiker de zoekbalk om naar de gewenste positie te zoeken.

```java
// Use the native SeekBar to set OnSeekBarChangeListener to  
//see when the user is scrubbing. 
seekBar.setOnSeekBarChangeListener(new SeekBar.OnSeekBarChangeListener() { 
 
    @Override 
    public void onProgressChanged(SeekBar seekBar, int progress, boolean isFromUser) { 
        if (isFromUser) {  
            // Update the seek bar thumb, with the position provided by the user. 
            setPosition(progress); 
        } 
    } 
 
    @Override 
    public void onStartTrackingTouch(SeekBar seekBar) { 
        isSeeking = true; 
    } 
 
    @Override 
    public void onStopTrackingTouch(SeekBar seekBar) { 
        isSeeking = false; 
        // Retrieve the playback range. 
        TimeRange playbackRange = mediaPlayer.getPlaybackRange(); 
        // Make sure to seek inside the playback range. 
        long seekPosition = Math.min(Math.round(seekBar.getProgress()),  
                                     playbackRange.getDuration()); 
        // Perform seek. 
        seek(playbackRange.getBegin() + seekPosition); 
    } 
}; 
```
