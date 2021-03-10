---
description: U kunt TVSDK gebruiken om informatie op te halen over de media die u op de zoekbalk kunt weergeven.
title: De duur, de huidige tijd en de resterende tijd van de video weergeven
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---


# Geef de duur, de huidige tijd en de resterende tijd van de video weer{#display-the-duration-current-time-and-remaining-time-of-the-video}

U kunt TVSDK gebruiken om informatie op te halen over de media die u op de zoekbalk kunt weergeven.

1. Wacht tot de speler de status INITIALIZED heeft.
1. Haal de huidige tijd van de afspeelkop op met de eigenschap `MediaPlayer.currentTime`.

   Hiermee wordt de huidige positie van de afspeelkop op de virtuele tijdlijn in milliseconden geretourneerd. De tijd wordt berekend ten opzichte van de opgeloste stream die meerdere instanties van alternatieve inhoud kan bevatten, zoals meerdere advertenties of ad-einden die in de hoofdstream worden gespliceerd. Voor live/lineaire streams bevindt de geretourneerde tijd zich altijd in het bereik van het afspeelvenster.

   ```
   function get currentTime():Number;
   ```

1. Haal het afspeelbereik van de stream op en bepaal de duur.
   1. Gebruik de eigenschap `mediaPlayer.playbackRange` om het tijdbereik van de virtuele tijdlijn op te halen.

      ```
      function get playbackRange():TimeRange;
      ```

   1. Analyseer het tijdbereik met `mediacore.utils.TimeRange`.
   1. Als u de duur wilt bepalen, trekt u het begin af aan het einde van het bereik.

      Dit omvat de duur van extra inhoud die in de stream (advertenties) wordt ingevoegd.

      Bij VOD begint het bereik altijd met nul en is de eindwaarde gelijk aan de som van de duur van de hoofdinhoud en de duur van de extra inhoud die in de stream (advertenties) wordt ingevoegd.

      Voor een lineair/actief-element vertegenwoordigt het bereik van het afspeelvenster en verandert dit bereik tijdens het afspelen.

      TVSDK verzendt een gebeurtenis `MediaPlayerItemEvent.ITEM_UPDATED` om aan te geven dat het media-item is vernieuwd en dat de kenmerken ervan (inclusief het afspeelbereik) zijn bijgewerkt.

1. Gebruik de methoden die beschikbaar zijn in de klasse `MediaPlayer` en `HSlider` die algemeen beschikbaar is in de SDK van Flex om de parameters voor de zoekbalk in te stellen.

1. Gebruik een tijdopnemer om de huidige tijd periodiek terug te winnen en `SeekBar` bij te werken.
