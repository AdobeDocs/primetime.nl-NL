---
description: Wanneer gebruikers snel vooruit of snel terugspoelen door de media, zijn zij in de truc spelwijze. Als u de speelmodus voor truc wilt inschakelen, moet u de afspeelsnelheid van MediaPlayer instellen op een andere waarde dan 1.
title: Snel vooruitspoelen en terugspoelen
exl-id: c1d70d46-449b-494b-9b89-5553e9bcdbc3
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '775'
ht-degree: 0%

---

# Snel vooruitspoelen en terugspoelen {#implement-fast-forward-and-rewind}

Wanneer gebruikers snel vooruit of snel terugspoelen door de media, zijn zij in de truc spelwijze. Als u de speelmodus voor truc wilt inschakelen, moet u de afspeelsnelheid van MediaPlayer instellen op een andere waarde dan 1.

U moet één waarde instellen om van snelheid te wisselen.

1. Ga van normale playmode (1x) naar truc playmode door te plaatsen `rate` eigenschap op de `MediaPlayer` op een toegestane waarde.

   * De `MediaPlayerItem` -klasse definieert de toegestane afspeelsnelheden.
   * TVSDK selecteert de dichtstbijzijnde toegestane snelheid als de opgegeven snelheid niet is toegestaan.

      Wanneer de afspeelsnelheid wordt gewijzigd van 0 (pauzeren) of 1 (normaal afspelen) in een snelheid groter dan 1 of kleiner dan -1, worden alle advertenties op de tijdlijn verwijderd. Er is slechts één periode op de gehele tijdlijn die een &#39;trickplay&#39;-handeling vergemakkelijkt, zodat de inhoud snel kan worden doorgestuurd en teruggespoeld zonder op een willekeurige positie te stoppen. Deze handeling wordt ingeschakeld door een handeling voor het ontkoppelen van een tijdlijn op TVSDK om alle opgeloste adBreaks te verwijderen. Wanneer het trickplay bij 0 of 1 hervat, wordt addBreaks eerst hersteld door de actie van de chronologiegehechtheid.

      De volgende informatie onthouden:

   * Als de handeling &#39;trickplay&#39; de inhoud terugspoelt, wordt het afspelen hervat wanneer de snelheid wordt gewijzigd in 1.
   * Als de truckplay actie de inhoud door:sturen is, speelt laatste overgeslagen adBreak bij de hervattingspositie.

   In dit voorbeeld wordt de interne afspeelsnelheid van de speler ingesteld op de gewenste snelheid.

   ```
   private function onPlaybackRateChange(event:IndexChangeEvent):void { 
       var newRateIndex:int = event.newIndex; 
       var newRate:Number = _playbackRates[newRateIndex]; 
   
       _player.rate = newRate; 
   } 
   ```

1. U kunt naar keuze luisteren op snelheid-verandering gebeurtenissen, die u laten weten wanneer u om een tariefverandering vroeg en wanneer een snelheidsverandering eigenlijk gebeurt.

   TVSDK verzendt de volgende gebeurtenissen met betrekking tot truc-play:

   * `mediacore.events.PlaybackRateEvent.RATE_SELECTED` wanneer de `rate` De waarde verandert in een andere waarde.

   * `mediacore.events.PlaybackRateEvent.RATE_PLAYING` wanneer het afspelen wordt hervat met de geselecteerde frequentie.

   TVSDK verzendt beide gebeurtenissen wanneer de speler van de truc-spelmodus naar de normale afspeelmodus terugkeert.

## API-elementen wijzigen {#rate-change-api}

TVSDK bevat methoden, eigenschappen en gebeurtenissen om geldige frequenties, huidige snelheden, of het kunstspel wordt gesteund, en andere functionaliteit met betrekking tot snel voorwaarts en terugspoelen te bepalen.

Gebruik de volgende API-elementen om de afspeelsnelheden te wijzigen:

* `MediaPlayer.rate` eigenschap met functies setter en getter
* `MediaPlayer.localTime property` met functie getter
* `mediacore.events.PlaybackRateEvent.RATE_SELECTED`
* `mediacore.events.PlaybackRateEvent.RATE_PLAYING`
* `MediaPlayerItem.IsTrickPlaySupported` eigenschap met functie getter
* `AdBreakPlaybackEvent.AD_BREAK_SKIPPED`
* `MediaPlayerItem.availablePlaybackRates` eigenschap met getter functie - geeft geldige snelheden op.

| Waarde van waardering | Effect op afspelen |
|---|---|
| 2.0, 4.0, 8.0, 16.0, 32.0, 64.0  , 128.0 | Schakelt sneller over naar de modus Snel vooruit met de opgegeven vermenigvuldiger dan normaal (4 is bijvoorbeeld 4 keer sneller dan normaal) |
| -2.0, -4.0, -8.0, -16.0, -32.0, -64.0  , -128.0 | Schakelt over op de modus Snel terugspoelen |
| 1.0 | Schakelt over op de normale afspeelmodus (aanroepen `play` is hetzelfde als het instellen van de eigenschap rate op 1,0) |
| 0.0 | Pauzeren (aanroepen) `pause` is het zelfde als het plaatsen van het tariefbezit aan 0.0) |

## Beperkingen en gedrag voor het spelen van truc {#limitations-behavior-trick-play}

Hier volgen de beperkingen voor de modus voor het spelen van truc:

* De master afspeellijst moet alleen I-frame-segmenten bevatten. Alleen de keyframes van de I-frame track worden op het scherm weergegeven.
* De audiotrack en gesloten bijschriften zijn uitgeschakeld.
* De logica voor de adaptieve bitsnelheid (ABR) is uitgeschakeld. TVSDK selecteert één beetjetarief tussen het laagste verstrekte tarief en 800 kbps en gebruikt dat tarief tijdens de volledige truc-spelzitting.
* Afspelen en pauzeren zijn ingeschakeld.
* Seek is niet toegestaan. Om te zoeken, roep `pause` om de speelwijze van de truc weg te gaan en dan te roepen `seek`.

* U kunt de modus voor het afspelen van truc&#39;s afsluiten in elke toegestane afspeelsnelheid (afspelen of pauzeren).
* Wanneer advertenties in de stream worden opgenomen:

   * U kunt alleen truc spelen tijdens het afspelen van de hoofdinhoud. Er wordt een fout verzonden wanneer u probeert om het afspelen tijdens een advertentie-einde te truien.
   * Nadat de truc-afspeelmodus is gestart, worden add-einden genegeerd en worden er geen advertentiegebeurtenissen geactiveerd.
   * De tijdlijn die door TVSDK aan de spelertoepassing wordt blootgesteld, wordt niet gewijzigd, zelfs niet als ad-einden worden overgeslagen.
   * De `MediaPlayer.currentTime` eigenschap springt voorwaarts (bij snel terugspoelen) of achteruit (bij snel terugspoelen) met de duur van de overgeslagen ad-onderbreking. Door dit spronggedrag voor de huidige tijd kan de streamduur ongewijzigd blijven tijdens het spelen van een truc. Uw spelertoepassing kan de `localTime` eigenschap om de tijd alleen te volgen ten opzichte van de hoofdinhoud. Er worden geen tijdsprongen uitgevoerd op de waarden die tijdens het overslaan van een advertentie worden geretourneerd.

   * De `AdBreakPlaybackEvent.AD_BREAK_SKIPPED` -gebeurtenis wordt verzonden vlak voordat een advertentieeinde wordt overgeslagen. De speler kan deze gebeurtenis gebruiken om aangepaste logica te implementeren met betrekking tot overgeslagen en verbroken bewerkingen.
   * Als u een truc afsluit, wordt hetzelfde ad-playbackbeleid aangeroepen als wanneer u een zoekopdracht afsluit.

      Daarom hangt het gedrag, net als bij het zoeken, af van het feit of het afspeelbeleid van uw toepassing afwijkt van het standaardbeleid. Standaard wordt het laatste overgeslagen en afgebroken geluid afgespeeld op het punt waar je uit de truc komt.
