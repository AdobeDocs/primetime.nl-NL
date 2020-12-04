---
description: U kunt TVSDK gebruiken om informatie op te halen over de positie van de speler in de media en deze weer te geven op de zoekbalk.
seo-description: U kunt TVSDK gebruiken om informatie op te halen over de positie van de speler in de media en deze weer te geven op de zoekbalk.
seo-title: De duur, de huidige tijd en de resterende tijd van de video weergeven
title: De duur, de huidige tijd en de resterende tijd van de video weergeven
uuid: 29bb6bc2-dab1-4f35-abcf-d3213605ee70
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---


# De duur, de huidige tijd en de resterende tijd van de video {#display-the-duration-current-time-and-remaining-time-of-the-video} weergeven

U kunt TVSDK gebruiken om informatie op te halen over de positie van de speler in de media en deze weer te geven op de zoekbalk.

1. Wacht tot de speler zich ten minste in de staat PREPARED bevindt.
1. Haal de huidige playhead tijd door `MediaPlayer.getCurrentTime` methode terug te gebruiken.

   Hiermee wordt de huidige positie van de afspeelkop op de virtuele tijdlijn in milliseconden geretourneerd. De tijd wordt berekend ten opzichte van de opgeloste stream die meerdere instanties van alternatieve inhoud kan bevatten, zoals meerdere advertenties of ad-einden die in de hoofdstream worden gespliceerd. Voor live/lineaire streams bevindt de geretourneerde tijd zich altijd in het bereik van het afspeelvenster.

   ```java
   long getCurrentTime() throws MediaPlayerException;
   ```

1. Haal het afspeelbereik van de stream op en bepaal de duur.
   1. Gebruik de methode `MediaPlayer.getPlaybackRange` om het tijdbereik van de virtuele tijdlijn op te halen.

      ```java
      TimeRange getPlaybackRange() throws MediaPlayerException;
      ```

   1. Gebruik de methode `MediaPlayer.getPlaybackRange` om het tijdbereik van de virtuele tijdlijn op te halen.

      * Bij VOD begint het bereik altijd met nul en is de eindwaarde gelijk aan de som van de duur van de hoofdinhoud en de duur van de extra inhoud in de stream (advertenties).
      * Voor een lineair/actief-element vertegenwoordigt het bereik van het afspeelvenster. Dit bereik verandert tijdens het afspelen.

         TVSDK roept `ITEM_Updated` callback om erop te wijzen dat het media punt werd verfrist en dat zijn attributen, met inbegrip van de playbackwaaier, werden bijgewerkt.

1. Gebruik de methoden die beschikbaar zijn op `MediaPlayer` en op de `SeekBar`-klasse in de Android-SDK om de zoekbalkparameters in te stellen.

   Hier ziet u bijvoorbeeld een mogelijke lay-out die de zoekbalk en twee `TextView` elementen bevat.

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

1. Gebruik een tijdopnemer om de huidige tijd periodiek terug te winnen en de zoekbar bij te werken, zoals aangetoond in het cijfer:

   <!--<a id="fig_689CEDDD02094C0C8E91C5195F8EAD3F"></a>-->

   ![](assets/seek-bar.jpg){width=&quot;477.000pt&quot;}

   In het volgende voorbeeld wordt de hulpklasse `Clock.java`, die beschikbaar is in `ReferencePlayer`, gebruikt als de timer. Deze klasse stelt een gebeurtenislistener in en activeert elke seconde een gebeurtenis `onTick` of een andere time-outwaarde die u kunt opgeven.

   ```java
   playbackClock = new Clock(PLAYBACK_CLOCK, CLOCK_TIMER); 
   playbackClockEventListener = new Clock.ClockEventListener() { 
       @Override 
       public void onTick(String name) { 
           // Timer event is received. Update the seek bar here. 
       } 
   }; 
   playbackClock.addClockEventListener(playbackClockEventListener);
   ```

   In dit voorbeeld wordt de huidige positie van de mediaspeler opgehaald en wordt de zoekbalk bijgewerkt op elke klok. De twee `TextView`-elementen worden gebruikt om de huidige tijd en de eindpositie van het afspeelbereik als numerieke waarden te markeren.

   ```java
   @Override 
   public void onTick(String name) { 
       if (mediaPlayer != null &&  
         mediaPlayer.getStatus() == MediaPlayerStatus.PLAYING) { 
           handler.post(new Runnable() { 
               @Override 
               public void run() { 
                   seekBar.setProgress((int) mediaPlayer.getCurrentTime()); 
                   currentTimeText.setText(timeStampToText(mediaPlayer.getCurrentTime())); 
                   totalTimeText.setText(timeStampToText(mediaPlayer.getPlaybackRange().getEnd())); 
               } 
           }); 
       } 
   } 
   ```
