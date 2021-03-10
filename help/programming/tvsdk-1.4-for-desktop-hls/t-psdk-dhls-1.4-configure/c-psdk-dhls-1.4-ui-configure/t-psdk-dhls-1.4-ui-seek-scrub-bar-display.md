---
description: TVSDK ondersteunt het zoeken naar een specifieke positie (tijd) waar de stream een afspeellijst met schuifvensters is, zowel in video op aanvraag (VOD) als in live streams.
title: Een zoekbalk weergeven met de huidige afspeelpositie
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 0%

---


# Een zoekscrubbalk weergeven met de huidige afspeelpositie{#display-a-seek-scrub-bar-with-the-current-playback-position}

TVSDK ondersteunt het zoeken naar een specifieke positie (tijd) waar de stream een afspeellijst met schuifvensters is, zowel in video op aanvraag (VOD) als in live streams.

>[!IMPORTANT]
>
>Zoeken in een live stream is alleen toegestaan voor DVR.

1. Stel callbacks in voor zoeken.

       Zoeken is asynchroon, dus verzendt TVSDK de volgende gebeurtenissen met betrekking tot zoeken:
   
   * `SeekEvent.SEEK_BEGIN` - De zoekactie begint.
   * `SeekEvent.SEEK_END` - Zoek succesvol.
   * `SeekEvent.SEEK_POSITION_ADJUSTED` - de door de gebruiker opgegeven zoekpositie heeft aangepast.

1. Wacht tot de speler een geldige zoekstatus heeft.

   Geldige statussen worden voorbereid, voltooid, gepauzeerd en AFGESPEELD.

1. Luister naar de juiste gebeurtenis om te zien wanneer de gebruiker scrubt.
1. Geef de gewenste zoekpositie (milliseconden) door aan de methode `MediaPlayer.seek`.

   ```
   function seek(position:Number):void;
   ```

   U kunt alleen zoeken in de doorzoekbare duur van het element. Voor video op verzoek is de duur 0 tot en met de duur van het element.

   >[!TIP]
   >
   >Hierdoor wordt de afspeelkop naar een nieuwe positie in de stream verplaatst, maar de uiteindelijke berekende positie kan afwijken van de opgegeven zoekpositie.

1. Wacht tot TVSDK de gebeurtenis `SeekEvent.SEEK_END` verzendt.
1. Haal de uiteindelijk aangepaste afspeelpositie op met event.actualPosition.

       Dit is belangrijk omdat de werkelijke startpositie na de zoekactie kan verschillen van de gewenste positie. Verschillende regels kunnen van toepassing zijn, waaronder:
   
   * Het afspeelgedrag wordt beïnvloed als een zoekopdracht of een andere verplaatsing in het midden van een advertentiesleutel eindigt of als een zoekactie of andere verplaatsing wordt overgeslagen en afgebroken.
   * Als u bij een segmentgrens zoekt, wordt de zoekpositie aangepast aan het begin van het segment.

1. Gebruik de positiegegevens wanneer u een zoekbalk weergeeft.
