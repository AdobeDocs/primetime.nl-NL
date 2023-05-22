---
description: TVSDK bevat methoden, eigenschappen en gebeurtenissen om geldige frequenties, huidige snelheden, of het kunstspel wordt gesteund, en andere functionaliteit met betrekking tot snel voorwaarts en terugspoelen te bepalen.
title: API-elementen wijzigen
exl-id: 9c366645-5ce5-485c-8423-cb0ed4bd2677
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 3%

---

# API-elementen wijzigen{#rate-change-api-elements}

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
| -2.0, -4.0, -8.0, -16.0, -32.0, -64.0 , -128.0 | Schakelt over op de modus Snel terugspoelen |
| 1.0 | Schakelt over op de normale afspeelmodus (aanroepen `play` is hetzelfde als het instellen van de eigenschap rate op 1,0) |
| 0.0 | Pauzeren (aanroepen) `pause` is het zelfde als het plaatsen van het tariefbezit aan 0.0) |
