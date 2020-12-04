---
description: TVSDK bevat methoden, eigenschappen en gebeurtenissen om geldige frequenties, huidige snelheden, of het kunstspel wordt gesteund, en andere functionaliteit met betrekking tot snel voorwaarts en terugspoelen te bepalen.
seo-description: TVSDK bevat methoden, eigenschappen en gebeurtenissen om geldige frequenties, huidige snelheden, of het kunstspel wordt gesteund, en andere functionaliteit met betrekking tot snel voorwaarts en terugspoelen te bepalen.
seo-title: API-elementen wijzigen
title: API-elementen wijzigen
uuid: 0040d35c-f9cb-4066-9bee-828ed5541194
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 2%

---


# Snelheid wijzigen van API-elementen{#rate-change-api-elements}

TVSDK bevat methoden, eigenschappen en gebeurtenissen om geldige frequenties, huidige snelheden, of het kunstspel wordt gesteund, en andere functionaliteit met betrekking tot snel voorwaarts en terugspoelen te bepalen.

<!--<a id="section_36576E92DE6343AEBD0BBD662502365D"></a>-->

Gebruik de volgende API-elementen om de afspeelsnelheden te wijzigen:

* `PlaybackRateEvent.getRate`
* `MediaPlayer.getLocalTime`
* `MediaPlayerEvent.RATE_SELECTED`
* `MediaPlayerEvent.RATE_PLAYING`
* `MediaPlayerItem.istrickPlaySupported`
* `MediaPlayerEvent.AD_BREAK_SKIPPED`
* `MediaPlayerItem.getAvailablePlaybackRates` - geeft geldige tarieven op.

| Waarde van waardering | Effect op afspelen |
|---|---|
| 2.0, 4.0, 8.0, 16.0, 32.0, 64.0, 128.0 | Schakelt sneller over naar de modus Snel vooruit met de opgegeven vermenigvuldiger dan normaal (4 is bijvoorbeeld 4 keer sneller dan normaal) |
| -2.0, -4.0, -8.0, -16.0, -32.0, -64.0, -128.0 | Schakelt over op de modus Snel terugspoelen |
| 1,0 | Schakelt over naar de normale afspeelmodus (het aanroepen van `play` is hetzelfde als het instellen van de eigenschap rate op 1,0) |
| 0,0 | Pauzeren (het aanroepen van `pause` is hetzelfde als het instellen van de eigenschap rate op 0,0) |

