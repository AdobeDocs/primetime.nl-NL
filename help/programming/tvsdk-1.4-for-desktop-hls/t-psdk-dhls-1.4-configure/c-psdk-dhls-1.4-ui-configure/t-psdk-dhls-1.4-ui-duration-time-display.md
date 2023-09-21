---
description: U kunt TVSDK gebruiken om informatie op te halen over de media die u op de zoekbalk kunt weergeven.
title: De duur, de huidige tijd en de resterende tijd van de video weergeven
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# De duur, de huidige tijd en de resterende tijd van de video weergeven{#display-the-duration-current-time-and-remaining-time-of-the-video}

U kunt TVSDK gebruiken om informatie op te halen over de media die u op de zoekbalk kunt weergeven.

1. Wacht tot de speler de status INITIALIZED heeft.
1. De huidige tijd van de afspeelkop ophalen met de opdracht `MediaPlayer.currentTime` eigenschap.

   Hiermee wordt de huidige positie van de afspeelkop op de virtuele tijdlijn in milliseconden geretourneerd. De tijd wordt berekend ten opzichte van de opgeloste stream die meerdere instanties van alternatieve inhoud kan bevatten, zoals meerdere advertenties of ad-einden die in de hoofdstream worden gespliceerd. Voor live/lineaire streams bevindt de geretourneerde tijd zich altijd in het bereik van het afspeelvenster.

   ```
   function get currentTime():Number;
   ```

1. Haal het afspeelbereik van de stream op en bepaal de duur.
   1. Gebruik de `mediaPlayer.playbackRange` eigenschap om het tijdbereik van de virtuele tijdlijn op te halen.

      ```
      function get playbackRange():TimeRange;
      ```

   1. Het tijdbereik parseren met `mediacore.utils.TimeRange`.
   1. Als u de duur wilt bepalen, trekt u het begin af aan het einde van het bereik.

      Dit omvat de duur van extra inhoud die in de stream (advertenties) wordt ingevoegd.

      Bij VOD begint het bereik altijd met nul en is de eindwaarde gelijk aan de som van de duur van de hoofdinhoud en de duur van de extra inhoud die in de stream (advertenties) wordt ingevoegd.

      Voor een lineair/actief-element vertegenwoordigt het bereik van het afspeelvenster en verandert dit bereik tijdens het afspelen.

      TVSDK verzendt een `MediaPlayerItemEvent.ITEM_UPDATED` om aan te geven dat het media-item is vernieuwd en dat de kenmerken ervan (inclusief het afspeelbereik) zijn bijgewerkt.

1. Gebruik de methoden die beschikbaar zijn op de `MediaPlayer` en de `HSlider` -klasse die algemeen beschikbaar is in de SDK van Flex voor het instellen van de zoekbalkparameters.

1. Gebruik een tijdopnemer om de huidige tijd periodiek terug te winnen en update `SeekBar`.
