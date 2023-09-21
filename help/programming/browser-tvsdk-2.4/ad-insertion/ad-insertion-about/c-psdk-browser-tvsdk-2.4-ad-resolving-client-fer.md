---
description: FER-inhoud (Full Event Replay) is een live stream die wordt omgezet in VOD door de tag
title: SNELLER EN OPLOSSEN EN invoegen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---

# SNELLER EN OPLOSSEN EN invoegen{#fer-ad-resolving-and-insertion}

FER-inhoud (Full Event Replay) is een live stream die wordt omgezet in VOD door de tag #EXT-X-ENDLIST toe te voegen aan het einde van het manifestbestand. De stream behoudt de advertentiemarkeringen.

Browser TVSDK behandelt een FER-stream als VOD, zodat de advertentie-signaalmodus standaard `SERVER_MAP`. Aangezien de advertentiemarkeringen echter behouden blijven, kunt u de advertentiemodus instellen op `MANIFEST_CUES`, waarmee u actiemarkeringen voor advertenties kunt gebruiken om invoegingen toe te voegen.

Een invoeging voor een FER-stream inschakelen met actiemarkeringen:

```js
var config = new AdobePSDK.MediaPlayerItemConfig(); 
config.adSignalingMode = AdobePSDK.AdSignalingMode.MANIFEST_CUES; 
player.replaceCurrentResource(mediaResource, config);
```

FER-gedrag voor opheffen en invoegen is vergelijkbaar met live opheffen en invoegen. Browser TVSDK doet het volgende:

1. Voegt pre-roladvertenties aan het begin van de inhoud in.
1. Hiermee worden advertenties opgelost die zijn opgegeven door de actiepunten die in het manifest zijn gedefinieerd.
1. Hiermee vervangt u delen van de hoofdinhoud door extra einden van dezelfde duur
1. Berekent indien nodig de virtuele tijdlijn opnieuw.

**Beperking:** Browser-TVSDK ondersteunt alleen het afspelen van HLS FER-streams. Bovendien worden MP4-advertenties in het midden niet ondersteund met FER-streams.
