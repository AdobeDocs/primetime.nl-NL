---
description: Voor live/lineaire inhoud vervangt TVSDK een segment van de inhoud van de hoofdstream door een ad-einde van dezelfde duur, zodat de tijdlijnduur ongewijzigd blijft.
seo-description: Voor live/lineaire inhoud vervangt TVSDK een segment van de inhoud van de hoofdstream door een ad-einde van dezelfde duur, zodat de tijdlijnduur ongewijzigd blijft.
seo-title: Actief/lineair en omzetten en invoegen
title: Actief/lineair en omzetten en invoegen
uuid: 69f287aa-b707-442b-8e07-16f81b242c4b
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---


# Live/lineair en opheffen en invoegen{#live-linear-ad-resolving-and-insertion}

Voor live/lineaire inhoud vervangt TVSDK een segment van de inhoud van de hoofdstream door een ad-einde van dezelfde duur, zodat de tijdlijnduur ongewijzigd blijft.

Vóór en tijdens het afspelen lost TVSDK bekende advertenties op, vervangt delen van de hoofdinhoud door add-einden van dezelfde duur en verwerkt zo nodig de virtuele tijdlijn opnieuw. De posities van de ad-einden worden bepaald door actiepunten die door het manifest worden gedefinieerd.

TVSDK voegt advertenties op de volgende manieren in:

* **Pre-roll**, dat aan het begin van de inhoud is.
* **Halftoonraster**, midden in de inhoud.

TVSDK accepteert het ad-einde, zelfs als de duur langer of korter is dan de vervangende duur van het actiepunt. Standaard ondersteunt TVSDK het `#EXT-X-CUE`-actiepunt als een geldige advertentiemarkering bij het omzetten en plaatsen van advertenties. Deze markering vereist het metagegevensveld `DURATION` in seconden en de unieke id van de actielijn. Bijvoorbeeld:

```
#EXT-X-CUE:DURATION=27,ID="..."
```

>[!IMPORTANT]
>
>Bij de implementatie van een gebruikelijke `AdPolicySelector` kan een ander beleid worden gegeven aan pre-rol, midden-rol, en post-rol `AdBreakTimelineItem`s in `AdPolicyInfo`, die op het type van `AdBreakTimelineItem`s gebaseerd is. U kunt bijvoorbeeld inhoud halverwege de rol behouden nadat deze is afgespeeld, maar de inhoud vóór de rol verwijderen nadat deze is afgespeeld.

Nadat het afspelen is gestart, vernieuwt de video-engine het manifestbestand regelmatig. TVSDK lost nieuwe advertenties op en voegt de advertenties in wanneer een richtsnoerpunt in de levende of lineaire stroom wordt ontmoet die in manifest werd bepaald. Nadat de advertenties zijn opgelost en ingevoegd, berekent TVSDK de virtuele tijdlijn opnieuw en verzendt een gebeurtenis `TimelineEvent.TIMELINE_UPDATED`.
