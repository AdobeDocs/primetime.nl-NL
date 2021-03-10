---
description: TVSDK bevat methoden, eigenschappen en gebeurtenissen om geldige snelheden, huidige snelheden, of het fel spelen wordt ondersteund en andere functionaliteit die verwant is aan snel vooruit spoelen en terugspoelen te bepalen.
title: API-elementen wijzigen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 3%

---


# Snelheid wijzigen van API-elementen {#rate-change-api-elements}

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
| -2.0, -4.0, -8.0, -16.0, -32.0, -64.0, -128.0 | Schakelt over op de modus Snel terugspoelen |
| 1,0 | Schakelt over naar de normale afspeelmodus (het aanroepen van `play` is hetzelfde als het instellen van de eigenschap rate op 1,0) |
| 0,0 | Pauzeren (het aanroepen van `pause` is hetzelfde als het instellen van de eigenschap rate op 0,0) |

