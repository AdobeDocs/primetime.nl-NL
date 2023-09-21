---
description: Voor live/lineaire inhoud vervangt TVSDK een segment van de inhoud van de hoofdstream door een ad-einde van dezelfde duur, zodat de tijdlijnduur ongewijzigd blijft.
title: Actief/lineair en omzetten en invoegen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 0%

---

# Actief/lineair en omzetten en invoegen{#live-linear-ad-resolving-and-insertion}

Voor live/lineaire inhoud vervangt TVSDK een segment van de inhoud van de hoofdstream door een ad-einde van dezelfde duur, zodat de tijdlijnduur ongewijzigd blijft.

Vóór en tijdens het afspelen lost TVSDK bekende advertenties op, vervangt delen van de hoofdinhoud door add-einden van dezelfde duur en verwerkt zo nodig de virtuele tijdlijn opnieuw. De posities van de ad-einden worden bepaald door actiepunten die door het manifest worden gedefinieerd.

TVSDK voegt advertenties op de volgende manieren in:

* **Pre-roll**, die aan het begin van de inhoud staat.
* **Midden rol**, die midden in de inhoud ligt.

TVSDK accepteert het ad-einde, zelfs als de duur langer of korter is dan de vervangende duur van het actiepunt. TVSDK biedt standaard ondersteuning voor de `#EXT-X-CUE` activeer als een geldige advertentiemarkering bij het omzetten en plaatsen van advertenties. Deze markering vereist het metagegevensveld `DURATION` in seconden en de unieke id van de actielijn. Bijvoorbeeld:

```
#EXT-X-CUE:DURATION=27,ID="..."
```

>[!IMPORTANT]
>
>Bij het implementeren van een `AdPolicySelector`, kan een ander beleid worden gevoerd voor pre-roll, mid-roll en post-roll `AdBreakTimelineItem`s in `AdPolicyInfo`, die gebaseerd is op het type `AdBreakTimelineItem`s. U kunt bijvoorbeeld de inhoud halverwege de rol behouden nadat deze is afgespeeld, maar de inhoud vóór de rol verwijderen nadat deze is afgespeeld.

Nadat het afspelen is gestart, vernieuwt de video-engine het manifestbestand regelmatig. TVSDK lost nieuwe advertenties op en voegt de advertenties in wanneer een richtsnoerpunt in de levende of lineaire stroom wordt ontmoet die in manifest werd bepaald. Nadat de advertenties zijn opgelost en ingevoegd, berekent TVSDK de virtuele tijdlijn opnieuw en wordt een `TimelineEvent.TIMELINE_UPDATED` gebeurtenis.
