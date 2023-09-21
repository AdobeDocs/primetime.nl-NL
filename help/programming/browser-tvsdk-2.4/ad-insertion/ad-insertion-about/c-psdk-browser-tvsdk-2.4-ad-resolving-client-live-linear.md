---
description: Voor live/lineaire inhoud vervangt Browser TVSDK een segment van de hoofdstreaminhoud door een ad-einde van dezelfde duur, zodat de tijdlijnduur ongewijzigd blijft.
title: Actief/lineair en omzetten en invoegen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# Actief/lineair en omzetten en invoegen{#live-linear-ad-resolving-and-insertion}

Voor live/lineaire inhoud vervangt Browser TVSDK een segment van de hoofdstreaminhoud door een ad-einde van dezelfde duur, zodat de tijdlijnduur ongewijzigd blijft.

Voor en tijdens het afspelen lost Browser-TVSDK bekende advertenties op, vervangt delen van de hoofdinhoud door add-einden van dezelfde duur en verwerkt zo nodig de virtuele tijdlijn opnieuw. De posities van de ad-einden worden bepaald door actiepunten die door het manifest worden gedefinieerd.

De browser TVSDK voegt advertenties op de volgende manieren in:

* **Pre-roll**, die aan het begin van de inhoud staat.

Browser-TVSDK accepteert het ad-einde, zelfs als de duur langer of korter is dan de vervangende duur van het actiepunt. Browser-TVSDK biedt standaard ondersteuning voor de `#EXT-X-CUE` activeer als een geldige advertentiemarkering bij het omzetten en plaatsen van advertenties. Deze markering vereist het metagegevensveld `DURATION` in seconden en de unieke id van de actielijn. Bijvoorbeeld:

```
#EXT-X-CUE:DURATION=27,ID="..."
```

U kunt extra cues (tags) definiëren en er een abonnement op nemen.

Nadat het afspelen is gestart, vernieuwt de video-engine het manifestbestand regelmatig. Browser-TVSDK verhelpt nieuwe advertenties en voegt de advertenties in wanneer een actiepunt wordt aangetroffen in de live of lineaire stream die in het manifest is gedefinieerd. Nadat de advertenties zijn opgelost en ingevoegd, berekent Browser TVSDK de virtuele tijdlijn opnieuw en verzendt een `AdobePSDK.PSDKEventType.TIMELINE_UPDATED` gebeurtenis.

>[!TIP]
>
>Voor live streams ondersteunt Browser-TVSDK alleen MP4- en HLS-pre- en mid-roll-advertenties.
