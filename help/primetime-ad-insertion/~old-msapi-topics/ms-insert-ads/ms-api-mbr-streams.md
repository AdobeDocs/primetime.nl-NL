---
description: Clientverzoeken om invoeging van een advertentie geven doorgaans meer dan één bitsnelheid op in de afspeellijst met versies die zijn opgemaakt voor de variant M3U8. De manifestserver genereert en retourneert een nieuw M3U8-bestand met een aparte M3U8-koppeling voor elke bitsnelheid. Er wordt ook een unieke groep-id gegenereerd om deze M3U8s aan elkaar te koppelen.
seo-description: Clientverzoeken om invoeging van een advertentie geven doorgaans meer dan één bitsnelheid op in de afspeellijst met versies die zijn opgemaakt voor de variant M3U8. De manifestserver genereert en retourneert een nieuw M3U8-bestand met een aparte M3U8-koppeling voor elke bitsnelheid. Er wordt ook een unieke groep-id gegenereerd om deze M3U8s aan elkaar te koppelen.
seo-title: Streams met meerdere bitsnelheden
title: Streams met meerdere bitsnelheden
uuid: f59cb765-e000-43e0-8d3a-8149a3c5b96e
translation-type: tm+mt
source-git-commit: e437f4143fb939f46d106c64efc391137c33fe17
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---


# Meerdere bitsnelheidstreams {#multiple-bit-rate-streams}

Clientverzoeken om invoeging van een advertentie geven doorgaans meer dan één bitsnelheid op in de afspeellijst met versies die zijn opgemaakt voor de variant M3U8. De manifestserver genereert en retourneert een nieuw M3U8-bestand met een aparte M3U8-koppeling voor elke bitsnelheid. Er wordt ook een unieke groep-id gegenereerd om deze M3U8s aan elkaar te koppelen.

De manifestserver gebruikt de informatie in het Bootstrap URL-verzoek van de cliënt om de inhoudvariant playlist terug te winnen. Het produceert een nieuwe variant playlist die duidelijke serververbindingen met de stroom-vlakke inhoud bevat. De client gebruikt deze voor het samenstellen en invoegen van aanvragen. De inhoudskoppelingen op streamniveau van de manifestserver hebben de volgende indeling:

```
https://manifest.auditude.com/auditude/{live/vod}/{publisherAssetID}/{rendition}/
  {groupID}/{base64-encoded url of the bit rate stream}.[m3u8]?{Query parameters}
```

* **`live/vod`** De manifestserver plaatst deze waarde die op het playlist type van de inhoud wordt gebaseerd: Live/lineair (#EXT-X-PLAYLIST-TYPE:EVENT) of VOD (#EXT-X-PLAYLIST-TYPE:VOD)

* **`publisherAssetID`** De unieke id van de uitgever voor de specifieke inhoud die in het URL-verzoek van de Bootstrap wordt opgegeven.

* **`rendition`** De manifestserver plaatst dit gebaseerd op de waarde BANDWIDTH van de inhoudsstroom, en gebruikt het om het te gebruiken om het beetjetarief van de advertentie aan het beetjetarief van de inhoud aan te passen. De bitsnelheid van de advertentie kan de bitsnelheid van de inhoud alleen overschrijden als de advertentie-uitvoering met de laagste bitsnelheid dit doet.

* **`groupID`** De manifestserver genereert deze waarde en gebruikt deze om ervoor te zorgen dat advertenties consistent worden geplaatst, ongeacht de bitsnelheidsuitvoering die de client vraagt voor advertenties.

* **`base64-encoded url of the bit rate stream`** De duidelijke server URL-safe base64 codeert de absolute URL van de inhoudsstroom. Elke stream heeft een eigen URL.

* **`Query parameters`** De parameters van de vraag die in het Bootstrap URL- verzoek worden verstrekt.

