---
description: TVSDK ondersteunt zoeken naar een specifieke positie (tijd) waar de stream een afspeellijst met schuifvensters is, in video op aanvraag (VOD) en live streams.
title: Een zoekbalk weergeven met de huidige afspeelpositie
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---


# Een zoekscrubbalk weergeven met de huidige afspeelpositie {#display-a-seek-scrub-bar-with-the-current-playback-position}

TVSDK ondersteunt zoeken naar een specifieke positie (tijd) waar de stream een afspeellijst met schuifvensters is, in video op aanvraag (VOD) en live streams.

>[!TIP]
>
>Zoeken in een live stream is alleen toegestaan voor DVR.

1. Stel callbacks in voor zoeken.

   Zoeken is asynchroon, dus verzendt TVSDK de volgende gebeurtenissen met betrekking tot zoeken:

   * `MediaPlayerEvent.SEEK_BEGIN`, waar het zoeken begint.
   * `MediaPlayerEvent.SEEK_END`, waarbij de zoekactie succesvol is.
   * `MediaPlayerEvent.OPERATION_FAILED`, waar de zoekopdracht is mislukt.

1. Wacht tot de speler een geldige zoekstatus heeft.

   De geldige statussen worden BEREID, VOLTOOID, GEPAUZEERD EN AFGESPEELD.
1. Gebruik de native `SeekBar` om `OnSeekBarChangeListener` in te stellen, die bepaalt wanneer de gebruiker scrubt.
1. Geef de gewenste zoekpositie (milliseconden) door aan de methode `MediaPlayer.seek`.

   ```java
   void seek(long position) throws MediaPlayerException;
   ```

   U kunt alleen zoeken in de doorzoekbare duur van het element. Voor video op bestelling, dat wil zeggen van 0 tot en met de duur van het element.

   >[!TIP]
   >
   >Met deze stap wordt de afspeelkop naar een nieuwe positie in de stream verplaatst, maar de uiteindelijke berekende positie kan afwijken van de opgegeven zoekpositie.

1. Luister naar `MediaPlayerEvent.OPERATION_FAILED` en voer de juiste handelingen uit.

   Deze gebeurtenis geeft de juiste waarschuwing door. Uw toepassing bepaalt hoe u verder wilt gaan. Tot de opties behoren het opnieuw zoeken of het afspelen vanaf de vorige positie.

1. Wacht op TVSDK om `MediaPlayerEvent.SEEK_END` callback te roepen.
1. Haal de definitieve aangepaste spelpositie terug gebruikend de positieparameter van callback.

   Dit is belangrijk omdat de werkelijke startpositie na de zoekactie kan verschillen van de gewenste positie. De regels, inclusief het afspeelgedrag, worden beïnvloed wanneer een zoekopdracht of een andere herpositionering halverwege een advertentie-einde eindigt of wanneer afbrekingen worden overgeslagen en onderbroken.

1. Gebruik de positiegegevens wanneer u een zoekbalk weergeeft.

<!--<a id="example_EEB73818260C43C8B5AE12BA68548AB7"></a>-->

**Voorbeeld van zoeken**

In dit voorbeeld scrubt de gebruiker de zoekbalk om naar de gewenste positie te zoeken.

```java
//Use the native SeekBar to set an OnSeekBarChangeListener to 
// see when the user is scrubbing. 
seekBar.setOnSeekBarChangeListener(new SeekBar.OnSeekBarChangeListener() { 
    @Override 
    public void onProgressChanged(SeekBar seekBar, int progress, boolean isFromUser) { 
        if (isFromUser) { 
            // Update the seek bar thumb with the position provided by the user. 
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
