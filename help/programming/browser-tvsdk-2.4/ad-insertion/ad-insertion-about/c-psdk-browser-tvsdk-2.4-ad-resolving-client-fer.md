---
description: 'FER-inhoud (Full Event Replay) is een live stream die wordt omgezet in VOD door de tag #EXT-X-ENDLIST toe te voegen aan het einde van het manifestbestand. De stream behoudt de advertentiemarkeringen.'
seo-description: 'FER-inhoud (Full Event Replay) is een live stream die wordt omgezet in VOD door de tag #EXT-X-ENDLIST toe te voegen aan het einde van het manifestbestand. De stream behoudt de advertentiemarkeringen.'
seo-title: SNELLER EN OPLOSSEN EN INVOEGEN
title: SNELLER EN OPLOSSEN EN INVOEGEN
uuid: 85da0e92-17fe-4001-a53c-085dadd09756
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# SNELLER EN OPLOSSEN EN INVOEGEN{#fer-ad-resolving-and-insertion}

FER-inhoud (Full Event Replay) is een live stream die wordt omgezet in VOD door de tag #EXT-X-ENDLIST toe te voegen aan het einde van het manifestbestand. De stream behoudt de advertentiemarkeringen.

Browser TVSDK behandelt een FER stroom als VOD, zodat door gebrek is de advertentie signalerende wijze `SERVER_MAP`. Omdat de stream echter zijn advertentiemarkeringen behoudt, kunt u de advertentiemodus instellen op `MANIFEST_CUES`, zodat u de advertentiemarkeringen kunt gebruiken voor het invoegen van advertenties.

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
