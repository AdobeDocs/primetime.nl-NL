---
description: Er zijn enkele beperkingen en een aantal problemen in de manier waarop de truc-afspeelmodus zich gedraagt.
seo-description: Er zijn enkele beperkingen en een aantal problemen in de manier waarop de truc-afspeelmodus zich gedraagt.
seo-title: Beperkingen en gedrag voor het spelen van truc
title: Beperkingen en gedrag voor het spelen van truc
uuid: 0e84c9ef-fc18-4667-ad17-7f4777b552ba
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Beperkingen en gedrag voor het spelen van truc{#limitations-and-behavior-for-trick-play}

Er zijn enkele beperkingen en een aantal problemen in de manier waarop de truc-afspeelmodus zich gedraagt.

<!--<a id="section_8B88E281A0FA4661B4C2C70A0ABED57C"></a>-->

Hier volgen de beperkingen voor de modus voor het spelen van truc:

* De hoofdafspeellijst moet alleen I-frame-segmenten bevatten. Alleen de keyframes van de I-frame track worden op het scherm weergegeven.
* De audiotrack en gesloten bijschriften zijn uitgeschakeld.
* De logica voor de adaptieve bitsnelheid (ABR) is uitgeschakeld. TVSDK selecteert één beetjetarief tussen het laagste verstrekte tarief en 800 kbps en gebruikt dat tarief tijdens de volledige truc-spelzitting.
* Afspelen en pauzeren zijn ingeschakeld.
* Seek is niet toegestaan. Om te zoeken, roep `pause` om truc speelwijze weg te gaan en dan te roepen `seek`.

* U kunt van truc spelwijze in om het even welk toegestaan playbacktarief (spel of pauze) gaan.
* Wanneer advertenties in de stream worden opgenomen:

   * U kunt alleen truc spelen tijdens het afspelen van de hoofdinhoud. Er wordt een fout verzonden wanneer u probeert om het afspelen tijdens een advertentie-einde te truien.
   * Nadat de truc-afspeelmodus is gestart, worden add-einden genegeerd en worden er geen advertentiegebeurtenissen geactiveerd.
   * De tijdlijn die door TVSDK aan de spelertoepassing wordt blootgesteld, wordt niet gewijzigd, zelfs niet als ad-einden worden overgeslagen.
   * De huidige tijdwaarde springt vooruit (op snelle voorwaartse) of achteruit (op snelle terugspoeling) met de duur overgeslagen en onderbreking. Door dit spronggedrag voor de huidige tijd kan de streamduur ongewijzigd blijven tijdens het spelen van een truc. Uw spelertoepassing kan de lokale tijdwaarde krijgen om de tijd met betrekking tot slechts de belangrijkste inhoud te volgen. Er worden geen tijdsprongen uitgevoerd op de waarden die tijdens het overslaan van een advertentie worden geretourneerd.
   * De `MediaPlayerEvent.AD_BREAK_SKIPPED` gebeurtenis wordt verzonden vlak voordat een advertentieeinde wordt overgeslagen. De speler kan deze gebeurtenis gebruiken om aangepaste logica te implementeren met betrekking tot overgeslagen en verbroken bewerkingen.
   * Als u een truc afsluit, wordt hetzelfde ad-playbackbeleid aangeroepen als wanneer u een zoekopdracht afsluit.

      Daarom hangt het gedrag, net als bij het zoeken, af van het feit of het afspeelbeleid van uw toepassing afwijkt van het standaardbeleid. Standaard wordt het laatste overgeslagen en afgebroken geluid afgespeeld op het punt waar u de speelmodus hebt verlaten.

