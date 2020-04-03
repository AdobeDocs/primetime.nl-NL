---
description: Gebruik de optionele trackingmode, trackingversion en trackingposition queryparameters om URL's te verkrijgen waarnaar gegevens over de huidige video worden verzonden en bijgehouden. De antwoorden variëren met de volgende versie en of de videostroom of op bestelling (VOD) levend is.
seo-description: Gebruik de optionele trackingmode, trackingversion en trackingposition queryparameters om URL's te verkrijgen waarnaar gegevens over de huidige video worden verzonden en bijgehouden. De antwoorden variëren met de volgende versie en of de videostroom of op bestelling (VOD) levend is.
seo-title: API voor spelers om te communiceren met de manifestserver
title: API voor spelers om te communiceren met de manifestserver
uuid: ab7a19e7-6c28-4960-a56b-3b33c525e6b3
translation-type: tm+mt
source-git-commit: a33e1f290fcf78e6f131910f6037f4803f7be98d

---


# API voor spelers om te communiceren met de manifestserver {#api-for-players-to-interact-with-the-manifest-server}

Gebruik de optionele parameters `pttrackingmode`, `pttrackingversion`en `pttrackingposition` queryparameters om URL&#39;s te verkrijgen waarnaar gegevens over de huidige video worden verzonden en bijgehouden. De antwoorden variëren met de volgende versie en of de videostroom of op bestelling (VOD) levend is.

## Zoekparameters {#query-parameters}

|**trackingmodus**|
Voorbeeld: pttrackingmode=simpleSpecifying vertelt eenvoudig de manifestserver dat u het volgen informatie wilt.
Specificeer het op een verzoek om M3U8 te halen alvorens u het volgen informatie verzoekt.Wanneer u het niet specificeert, keert de duidelijke server volgende informatie in de markeringen #EXT-X-MARKER terug.
Of als u een andere geldige waarde dan simple opgeeft, wordt het bijhouden van de server aangeroepen.

|**trackingversie**|
Voorbeeld: trackingversion=v2This parameter vertelt de manifestserver welke indeling moet worden gebruikt om trackinginformatie te retourneren (zie [Bestandsindelingen](../../msapi-topics/ms-list-file-formats/ms-api-file-formats.md)).
Geef het bestand op op een verzoek om de M3U8 op te halen voordat u trackinggegevens aanvraagt. Wanneer u het niet opgeeft of een ongeldige waarde opgeeft, gebruikt de manifestserver v1.

|**trackingpositie**|
Voorbeeld: trackingpositionDeze parameter vertelt de manifestserver om volgende informatie van de video als JSON of VMAP voorwerp in het M3U8 dossier terug te keren.De manifestserver negeert de gespecificeerde waarde en verzendt alle volgende informatie het voor die zitting heeft. Als er geen waarde wordt doorgegeven, retourneert de manifestserver het gevraagde M3U8-bestand.
