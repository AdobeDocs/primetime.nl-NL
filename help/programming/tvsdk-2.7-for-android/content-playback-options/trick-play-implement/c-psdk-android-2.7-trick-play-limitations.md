---
description: 'null'
seo-description: 'null'
seo-title: Beperkingen en gedrag voor het spelen van truc
title: Beperkingen en gedrag voor het spelen van truc
uuid: 5b947075-eba0-45de-82d0-50b193f1ac83
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Beperkingen en gedrag voor het spelen van truc {#limitations-and-behavior-for-trick-play}

<!--<a id="section_2BC43539C5C142E085D06A7E35C76726"></a>-->

Beperkingen voor de speelmodus van een truc:

* De hoofdafspeellijst moet alleen Iframe-segmenten bevatten.

   Alleen de keyframes van de Iframe-track worden op het scherm weergegeven.
* De audiotrack en gesloten bijschriften zijn uitgeschakeld.
* Afspelen en pauzeren zijn ingeschakeld.
* U kunt de modus voor het afspelen van truc&#39;s afsluiten in elke toegestane afspeelsnelheid (afspelen of pauzeren).
* Wanneer advertenties in de stream worden opgenomen:

   * U kunt alleen truc spelen tijdens het afspelen van de hoofdinhoud. Er wordt een fout verzonden wanneer u probeert om het afspelen tijdens een advertentie-einde te truien.
   * Na het starten van de truc-afspeelmodus worden ad-einden genegeerd en worden er geen ad-hocgebeurtenissen geactiveerd.
   * De tijdlijn die door TVSDK aan de speler wordt weergegeven, wordt niet gewijzigd, zelfs niet wanneer ad-einden worden overgeslagen.
   * De huidige tijdwaarde springt vooruit (op snelle voorwaartse) of achteruit (op snelle terugspoeling) met de duur overgeslagen en onderbreking.

      Door dit spronggedrag voor de huidige tijd kan de streamduur ongewijzigd blijven tijdens het spelen van een truc. De speler kan de tijd alleen bijhouden ten opzichte van de hoofdinhoud. Er worden geen tijdsprongen uitgevoerd op de waarden die tijdens het overslaan van een advertentie worden geretourneerd.
   * De `MediaPlayerEvent.AD_BREAK_SKIPPED` gebeurtenis wordt verzonden vlak voordat een advertentieeinde wordt overgeslagen.

      De speler kan deze gebeurtenis gebruiken om aangepaste logica te implementeren met betrekking tot overgeslagen en verbroken bewerkingen.

   * Als u een truc afsluit, wordt hetzelfde ad-playbackbeleid aangeroepen als wanneer u een zoekopdracht afsluit.

      Net als bij zoeken hangt het gedrag af van het feit of het afspeelbeleid van uw toepassing afwijkt van het standaardbeleid. Standaard wordt het laatste overgeslagen en afgebroken geluid afgespeeld op het punt waar je uit de truc komt.

