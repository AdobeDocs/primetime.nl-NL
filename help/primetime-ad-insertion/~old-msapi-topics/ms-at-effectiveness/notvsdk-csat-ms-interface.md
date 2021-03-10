---
description: Gebruik de optionele trackingmode, trackingversion en trackingposition queryparameters om URL's te verkrijgen waarnaar gegevens over de huidige video worden verzonden en bijgehouden. De antwoorden variëren met de volgende versie en of de videostroom of op bestelling (VOD) levend is.
title: API voor spelers om te communiceren met de manifestserver
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---


# API voor spelers voor interactie met de manifestserver {#api-for-players-to-interact-with-the-manifest-server}

Gebruik de optionele `pttrackingmode`-, `pttrackingversion`- en `pttrackingposition`-queryparameters om URL&#39;s te verkrijgen waarnaar gegevens over de huidige video moeten worden verzonden en bijgehouden. De antwoorden variëren met de volgende versie en of de videostroom of op bestelling (VOD) levend is.

## Zoekparameters {#query-parameters}

**trackingmodus**

Voorbeeld: `pttrackingmode=simple`
Het specificeren van eenvoudig vertelt de manifestserver dat u het volgen informatie wilt.
Specificeer het op een verzoek om M3U8 te halen alvorens u het volgen informatie verzoekt.Wanneer u het niet specificeert, keert de duidelijke server volgende informatie in de markeringen #EXT-X-MARKER terug.
Of als u een andere geldige waarde dan simple opgeeft, wordt het bijhouden van de server aangeroepen.

**trackingversie**

Voorbeeld: `pttrackingversion=v2`
Deze parameter vertelt de manifestserver welke indeling moet worden gebruikt om volgende informatie te retourneren (zie [Bestandsindelingen](/help/primetime-ad-insertion/~old-msapi-topics/ms-list-file-formats/ms-api-file-formats.md)).
Geef het bestand op op een verzoek om de M3U8 op te halen voordat u trackinggegevens aanvraagt. Wanneer u het niet opgeeft of een ongeldige waarde opgeeft, gebruikt de manifestserver v1.

**trackingpositie**

Voorbeeld: `pttrackingposition`
Deze parameter vertelt de manifestserver om het volgen informatie van de video als JSON of VMAP voorwerp in het M3U8 dossier terug te keren.De manifestserver negeert de gespecificeerde waarde en verzendt alle het volgen informatie het voor die zitting heeft. Als er geen waarde wordt doorgegeven, retourneert de manifestserver het gevraagde M3U8-bestand.
