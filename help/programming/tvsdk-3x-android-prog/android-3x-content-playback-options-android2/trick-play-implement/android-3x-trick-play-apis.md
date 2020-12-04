---
description: TVSDK bevat methoden, eigenschappen en gebeurtenissen om geldige frequenties, huidige snelheden, of het kunstspel wordt gesteund, en andere functionaliteit te bepalen die met snel voorwaarts en terugspoelen verwant zijn.
seo-description: TVSDK bevat methoden, eigenschappen en gebeurtenissen om geldige frequenties, huidige snelheden, of het kunstspel wordt gesteund, en andere functionaliteit te bepalen die met snel voorwaarts en terugspoelen verwant zijn.
seo-title: API-elementen wijzigen
title: API-elementen wijzigen
uuid: c2bcd20c-0641-4d75-802c-08098786d572
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 2%

---


# Snelheid wijzigen van API-elementen {#rate-change-api-elements}

TVSDK bevat methoden, eigenschappen en gebeurtenissen om geldige frequenties, huidige snelheden, of het kunstspel wordt gesteund, en andere functionaliteit te bepalen die met snel voorwaarts en terugspoelen verwant zijn.

<!--<a id="section_E5D37C71323947E2AED8B866D9835E31"></a>-->

Gebruik de volgende API-elementen om de afspeelsnelheden te wijzigen:

* `PlaybackRateEvent.getRate`
* `MediaPlayerEvent.RATE_SELECTED`
* `MediaPlayerEvent.RATE_PLAYING`
* `MediaPlayerItem.isTrickPlaySupported`
* `MediaPlayerItem.getAvailablePlaybackRates`, die geldige tarieven aangeeft.

| **Waarde van waardering** | **Effect op afspelen** |
|---|---|
| 2.0, 4.0, 8.0, 16.0, 32.0, 64.0, 128.0 | Schakelt sneller over naar de modus Snel vooruit met de opgegeven vermenigvuldiger dan normaal (4 is bijvoorbeeld 4 keer sneller dan normaal) |
| -2.0, -4.0, -8.0, -16.0, -32.0, -64.0, -128.0 | Schakelt over op de modus Snel terugspoelen |
| 1,0 | Schakelt over naar de normale afspeelmodus (het aanroepen van `play` is hetzelfde als het instellen van de eigenschap rate op 1,0) |
| 0,0 | Pauzeren (het aanroepen van `pause` is hetzelfde als het instellen van de eigenschap rate op 0,0) |