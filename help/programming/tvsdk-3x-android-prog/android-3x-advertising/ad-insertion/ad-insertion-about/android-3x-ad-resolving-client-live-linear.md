---
description: Voor live/lineaire inhoud vervangt TVSDK een segment van de inhoud van de hoofdstream door een ad-einde van dezelfde duur, zodat de tijdlijnduur ongewijzigd blijft.
title: Live/lineaire advertentie oplossen en invoegen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---


# Live/lineaire advertenties {#resolve-and-insert-live-linear-ad} omzetten en invoegen

Voor live/lineaire inhoud vervangt TVSDK een segment van de inhoud van de hoofdstream door een ad-einde van dezelfde duur, zodat de tijdlijnduur ongewijzigd blijft.

Vóór en tijdens het afspelen lost TVSDK bekende advertenties op, vervangt delen van de hoofdinhoud door add-einden van dezelfde duur en verwerkt zo nodig de virtuele tijdlijn opnieuw. De posities van de ad-einden worden bepaald door actiepunten die door het manifest worden gedefinieerd.

TVSDK voegt advertenties op de volgende manieren in:

* **Pre-roll**, die vóór de inhoud wordt geplaatst.
* **Halve rol**, die in het midden van de inhoud wordt geplaatst.

TVSDK accepteert het ad-einde, zelfs als de duur langer of korter is dan de vervangende duur van het actiepunt. Standaard ondersteunt TVSDK het `#EXT-X-CUE`-actiepunt als een geldige advertentiemarkering bij het omzetten en plaatsen van advertenties. Deze markering vereist dat het metagegevensveld `DURATION` wordt uitgedrukt in seconden en de unieke id van de actielijn. Bijvoorbeeld:

```
#EXT-X-CUE:DURATION=27,ID="..."
```

U kunt extra cues (tags) definiëren en er een abonnement op nemen.

Nadat het afspelen is gestart, vernieuwt de video-engine het manifestbestand regelmatig. TVSDK lost nieuwe advertenties op en voegt de advertenties in wanneer een richtsnoerpunt in de levende of lineaire stroom wordt ontmoet die in manifest werd bepaald. Nadat de advertenties zijn opgelost en ingevoegd, berekent TVSDK de virtuele tijdlijn opnieuw en verzendt een gebeurtenis `TimelineItemsUpdatedEventListener.onTimelineUpdated`.