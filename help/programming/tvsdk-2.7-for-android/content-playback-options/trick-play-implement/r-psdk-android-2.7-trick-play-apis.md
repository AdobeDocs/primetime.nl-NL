---
description: TVSDK bevat methoden, eigenschappen en gebeurtenissen om geldige snelheden, huidige snelheden, of het fel spelen wordt ondersteund en andere functionaliteit die verwant is aan snel vooruit spoelen en terugspoelen te bepalen.
seo-description: TVSDK bevat methoden, eigenschappen en gebeurtenissen om geldige snelheden, huidige snelheden, of het fel spelen wordt ondersteund en andere functionaliteit die verwant is aan snel vooruit spoelen en terugspoelen te bepalen.
seo-title: API-elementen wijzigen
title: API-elementen wijzigen
uuid: 3554bf45-9419-4740-8a0e-484fc14c7436
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# API-elementen wijzigen {#rate-change-api-elements}

TVSDK bevat methoden, eigenschappen en gebeurtenissen om geldige snelheden, huidige snelheden, of het fel spelen wordt ondersteund en andere functionaliteit die verwant is aan snel vooruit spoelen en terugspoelen te bepalen.

<!--<a id="section_E5D37C71323947E2AED8B866D9835E31"></a>-->

Gebruik de volgende API-elementen om de afspeelsnelheden te wijzigen:

* `PlaybackRateEvent.getRate`
* `MediaPlayerEvent.RATE_SELECTED`
* `MediaPlayerEvent.RATE_PLAYING`
* `MediaPlayerItem.isTrickPlaySupported`
* `MediaPlayerItem.getAvailablePlaybackRates`, die geldige tarieven aangeeft.

| Waarde van waardering | Effect op afspelen |
|---|---|
| 2.0, 4.0, 8.0, 16.0, 32.0, 64.0, 128.0 | Schakelt sneller over naar de modus Snel vooruit met de opgegeven vermenigvuldiger dan normaal (4 is bijvoorbeeld 4 keer sneller dan normaal) |
| -2.0, -4.0, -8.0, -16.0, -32.0, -64.0 , -128.0 | Schakelt over op de modus Snel terugspoelen |
| 1.0 | De schakelaars aan normale spelwijze (het roepen `play` is het zelfde als het plaatsen van het tariefbezit aan 1.0) |
| 0.0 | Pauzeren (aanroepen `pause` is hetzelfde als het instellen van de eigenschap rate op 0,0) |

