---
description: Wanneer gebruikers snel vooruit of snel terugspoelen door de media, zijn zij in de truc spelwijze. Als u de speelmodus voor truc wilt inschakelen, moet u de afspeelsnelheid van MediaPlayer instellen op een andere waarde dan 1.
title: Snel vooruitspoelen en terugspoelen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---


# Snel vooruit en terugspoelen implementeren{#implement-fast-forward-and-rewind}

Wanneer gebruikers snel vooruit of snel terugspoelen door de media, zijn zij in de truc spelwijze. Als u de speelmodus voor truc wilt inschakelen, moet u de afspeelsnelheid van MediaPlayer instellen op een andere waarde dan 1.

>[!IMPORTANT]
>
>* De modus Steen afspelen wordt alleen ondersteund voor MPEG Dash- en HLS VOD-inhoud.
>* De modus Steen afspelen wordt niet ondersteund voor live streams of advertenties.
>* Bij het schakelen van hoofdinhoud naar een advertentie, laat Browser TVSDK de truc-afspeelmodus achter.

>



U moet één waarde instellen om van snelheid te wisselen.

1. Ga van normale spelwijze (1x) aan truc speelwijze door het tarief op `MediaPlayer` aan een toegestane waarde te plaatsen.

   * De klasse `MediaPlayerItem` definieert de toegestane afspeelsnelheden.
   * Browser TVSDK selecteert het dichtstbijzijnde toegestane tarief als het gespecificeerde tarief niet wordt toegestaan.

      De volgende voorbeeldfunctie stelt de snelheid in:

      ```js
      setTrickPlayRate = function (player, trickPlayRate) { 
                    player.rate = trickPlayRate; 
      }
      ```

      De volgende voorbeeldfunctie kan worden gebruikt om de beschikbare playbacktarieven te vragen:

      ```js
      getAvailableTrickPlayRates = function (player) { 
               var item = player.currentItem; 
               var availableRates = item. availablePlaybackRates; 
               return availableRates; 
      } 
      ```

1. U kunt naar keuze luisteren op snelheid-verandering gebeurtenissen, die u laten weten wanneer u om een tariefverandering vroeg en wanneer een snelheidsverandering eigenlijk gebeurt.

       Browser TVSDK verzendt de volgende gebeurtenissen met betrekking tot truc play:
   
   * `AdobePSDK.PSDKEventType.RATE_SELECTED` wanneer de  `rate` waarde in een andere waarde verandert.

   * `AdobePSDK.PSDKEventType.RATE_PLAYING` wanneer het afspelen wordt hervat met de geselecteerde frequentie.

      Browser TVSDK verzendt beide gebeurtenissen wanneer de speler van de truc-spelmodus naar de normale afspeelmodus terugkeert.

## Snelheid wijzigen van API-elementen {#rate-change-API-elements}

Browser TVSDK omvat methodes, eigenschappen, en gebeurtenissen om geldige tarieven, huidige tarieven te bepalen, of het kunstspel wordt gesteund, en andere functionaliteit met betrekking tot snel voorwaarts en terugspoelen.

Gebruik de volgende API-elementen om de afspeelsnelheden te wijzigen:

* `MediaPlayer.rate`
* `PlaybackRateEvent.rate`
* `MediaPlayerItem.istrickPlaySupported`
* `MediaPlayerItem.availablePlaybackRates` - geeft geldige tarieven op.

   | Waarde van waardering | Effect op afspelen |
   |---|---|
   | 2.0, 4.0, 8.0, 16.0, 32.0, 64.0 | Schakelt sneller over naar de modus Snel vooruit met de opgegeven vermenigvuldiger dan normaal (4 is bijvoorbeeld 4 keer sneller dan normaal) |
   | -2,0, -4,0, -8,0, -16,0, -32,0, -64,0 | Schakelt over op de modus Snel terugspoelen |
   | 1,0 | Schakelt over naar de normale afspeelmodus (het aanroepen van `play` is hetzelfde als het instellen van de eigenschap rate op 1,0) |
   | 0,0 | Pauzeren (het aanroepen van `pause` is hetzelfde als het instellen van de eigenschap rate op 0,0) |

## Beperkingen en gedrag voor het gebruik van truc {#limitations-and-behavior-trick-play}

Er zijn enkele beperkingen en een aantal problemen in de manier waarop de truc-afspeelmodus zich gedraagt.

Hier volgt een lijst met de beperkingen van de modus voor truc-afspelen:

* Als de stream geen &#39;truc play&#39;-aanpassing bevat, wordt snel terugspoelen uitgeschakeld en is de maximale afspeelsnelheid voor snel vooruitspoelen beperkt tot 8.
* Als truc-afspeelaanpassingen worden gebruikt om de truc-modus te bieden, wordt de audiotrack uitgeschakeld.
* In de truc-afspeelmodus is het schakelen tussen audio- en Closed Captions-tracks uitgeschakeld.
* Afspelen en pauzeren zijn ingeschakeld.
* Wanneer bij het zoeken wordt afgespeeld in de truc-afspeelmodus, wordt de afspeelsnelheid ingesteld op 1 en wordt het afspelen hervat.
* De logica voor adaptieve bitsnelheid (ABR) is ingeschakeld.

   Wanneer u normale aanpassingen gebruikt, zijn de profielen beperkt tussen `ABRControlParameters.minBitRate` en `ABRControlParameters.maxBitRate`. Wanneer u truc play-aanpassingen gebruikt, zijn de profielen beperkt tussen `ABRControlParameters.minTrickPlayBitRate` en `ABRControlParameters.maxTrickPlayBitRate`.