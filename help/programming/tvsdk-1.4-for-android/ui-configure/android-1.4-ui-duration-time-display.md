---
description: U kunt TVSDK gebruiken om informatie op te halen over de media die u op de zoekbalk kunt weergeven.
seo-description: U kunt TVSDK gebruiken om informatie op te halen over de media die u op de zoekbalk kunt weergeven.
seo-title: De duur, de huidige tijd en de resterende tijd van de video weergeven
title: De duur, de huidige tijd en de resterende tijd van de video weergeven
uuid: afb43169-2d82-4137-ba38-27caef3d8c21
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---


# Geef de duur, de huidige tijd en de resterende tijd van de video weer{#display-the-duration-current-time-and-remaining-time-of-the-video}

U kunt TVSDK gebruiken om informatie op te halen over de media die u op de zoekbalk kunt weergeven.

1. Wacht tot de speler de status PREPARED heeft.
1. Haal de huidige tijd van de afspeelkop op met de methode `MediaPlayer.getCurrentTime`.

   Hiermee wordt de huidige positie van de afspeelkop op de virtuele tijdlijn in milliseconden geretourneerd. De tijd wordt berekend ten opzichte van de opgeloste stream die meerdere instanties van alternatieve inhoud kan bevatten, zoals meerdere advertenties of ad-einden die in de hoofdstream worden gespliceerd. Voor live/lineaire streams bevindt de geretourneerde tijd zich altijd in het bereik van het afspeelvenster.

   ```java
   long getCurrentTime() throws IllegalStateException;
   ```

1. Haal het afspeelbereik van de stream op en bepaal de duur.
   1. Gebruik de methode `mediaPlayer.getPlaybackRange` om het tijdbereik van de virtuele tijdlijn op te halen.

      ```java
      TimeRange getPlaybackRange() throws IllegalStateException;
      ```

   1. Analyseer het tijdbereik met `mediacore.utils.TimeRange`.
   1. Als u de duur wilt bepalen, trekt u het begin af aan het einde van het bereik.

      Dit omvat de duur van extra inhoud die in de stream (advertenties) wordt ingevoegd.

      Bij VOD begint het bereik altijd met nul en is de eindwaarde gelijk aan de som van de duur van de hoofdinhoud en de duur van de extra inhoud die in de stream (advertenties) wordt ingevoegd.

      Voor een lineair/actief-element vertegenwoordigt het bereik van het afspeelvenster en verandert dit bereik tijdens het afspelen.

      TVSDK roept uw `onUpdated` callback om erop te wijzen dat het media punt werd verfrist en dat zijn attributen (met inbegrip van de playbackwaaier) werden bijgewerkt.

1. Gebruik de methoden die beschikbaar zijn in de klasse `MediaPlayer` en `SeekBar` die algemeen beschikbaar is in de Android-SDK om de parameters voor de zoekbalk in te stellen.

   Hier ziet u bijvoorbeeld een mogelijke indeling met de elementen `SeekBar` en `TextView`.

   ```xml
   <LinearLayout 
    android:id="@+id/controlBarLayout" 
    android:layout_width="match_parent" 
    android:layout_height="wrap_content" 
    android:layout_alignParentBottom="true" 
    android:background="@android:color/black" 
    android:orientation="horizontal" > 
    <TextView 
       android:id="@+id/playerCurrentTimeText" 
       android:layout_width="wrap_content" 
       android:layout_height="wrap_content" 
       android:layout_margin="7dp" 
       android:text="00:00" 
       android:textColor="@android:color/white" /> 
    <SeekBar 
       android:id="@+id/playerSeekBar" 
       android:layout_width="wrap_content" 
       android:layout_height="wrap_content" 
       android:layout_weight="1" /> 
    <TextView 
       android:id="@+id/playerTotalTimeText" 
       android:layout_width="wrap_content" 
       android:layout_height="wrap_content" 
       android:layout_margin="7dp" 
       android:text="00:00" 
       android:textColor="@android:color/white" /> 
   </LinearLayout>
   ```

1. Gebruik een tijdopnemer om de huidige tijd periodiek terug te winnen en SeekBar bij te werken.

   In het volgende voorbeeld wordt de hulpklasse `Clock.java` gebruikt als de timer, die beschikbaar is in PrimetimeReference van de referentiespeler. Deze klasse stelt een gebeurtenislistener in en activeert elke seconde een gebeurtenis `onTick` of een andere time-outwaarde die u kunt opgeven.

   ```java
   playbackClock = new Clock(PLAYBACK_CLOCK, CLOCK_TIMER); 
   playbackClockEventListener = new Clock.ClockEventListener() { 
   @Override 
   public void onTick(String name) { 
       // Timer event is received. Update the SeekBar here. 
   } 
   }; 
   playbackClock.addClockEventListener(playbackClockEventListener);
   ```

   Op elke kloktik haalt dit voorbeeld de huidige positie van de mediaspeler op en werkt de zoekbalk bij. De twee TextView-elementen worden gebruikt om de eindpositie van de huidige tijd en het afspeelbereik als numerieke waarden te markeren.

   ```java
   @Override 
   public void onTick(String name) { 
   if (mediaPlayer != null && mediaPlayer.getStatus() == PlayerState.PLAYING) { 
       handler.post(new Runnable() { 
           @Override 
           public void run() { 
               seekBar.setProgress((int)  
                    mediaPlayer.getCurrentTime()); 
               currentTimeText.setText(timeStampToText( 
                  mediaPlayer.getCurrentTime())); 
               totalTimeText.setText(timeStampToText( 
                   mediaPlayer.getPlaybackRange().getEnd())); 
           } 
       }); 
   } 
   }
   ```

