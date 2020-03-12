---
description: TVSDK biedt klassen en methoden waarmee u het afspeelgedrag kunt aanpassen van inhoud die reclame bevat.
seo-description: TVSDK biedt klassen en methoden waarmee u het afspeelgedrag kunt aanpassen van inhoud die reclame bevat.
seo-title: API-elementen voor het afspelen van advertenties
title: API-elementen voor het afspelen van advertenties
uuid: 5e21e709-8446-4fed-8711-aa4f629f1147
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# API-elementen voor het afspelen van advertenties {#api-elements-for-ad-playback}

TVSDK biedt klassen en methoden waarmee u het afspeelgedrag kunt aanpassen van inhoud die reclame bevat.

De volgende API-elementen zijn handig voor het aanpassen van het afspelen:

<table id="table_B07E373B9D2B425AB36466B1D42411AD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> API-element </th> 
   <th colname="col2" class="entry"> Inhoud die reclame ondersteunt </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="apiname"> AdvertisingMetadata </span> </td> 
   <td colname="col2">Bepaal of een advertentieeinde moet worden gemarkeerd als gevolgd door een viewer en zo ja, wanneer om het te markeren. Stel het gevolgde beleid in en krijg het via <span class="codeph"> setAdBreakAsWatched</span> en <span class="codeph"> getAdBreakAsWatched</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="apiname"> AdBreakPolicy</span> </td> 
   <td colname="col2"> Hiermee worden mogelijke afspeelbeleidsregels voor ad-hocafbrekingen opgesomd. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="apiname"> Advertentiebeleid</span> </td> 
   <td colname="col2"> Hiermee geeft u een overzicht van het mogelijke afspeelbeleid voor advertenties. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="apiname"> AdPolicySelector </span> </td> 
   <td colname="col2"> Interface die aanpassing van TVSDK en gedrag toestaat. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="apiname"> DefaultAdPolicySelector </span> </td> 
   <td colname="col2"> Klasse die het standaardgedrag van TVSDK uitvoert. Uw toepassing kan deze klasse overschrijven om het standaardgedrag aan te passen zonder de volledige interface te implementeren. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="apiname"> MediaPlayer</span> </td> 
   <td colname="col2"> 
    <ul id="ul_37700A741403448A8760FDDA68B099AA"> 
     <li id="li_B465170D449E49489C5924572BEEB4A5"><span class="codeph"> getLocalTime</span> <p>Dit is de lokale tijd van het afspelen, exclusief de geplaatste en afgebroken foto's. </p> </li> 
     <li id="li_D9D68CF428904BB2B84E1BCE828A90DC"><span class="codeph"> seekToLocal</span>. <p>Hier wordt gezocht ten opzichte van een lokale tijd in de stream. </p> </li> 
     <li id="li_9DBCA75537DC4824AA66B53A3FA28812"><span class="codeph"> getTimeline.convertToLocalTime</span>. <p>De virtuele positie op de tijdlijn wordt geconverteerd naar de lokale positie. </p> </li> 
    </ul> <p>Belangrijk:  <span class="codeph"> getLocalTime</span> in <span class="codeph"> MediaPlayer</span> retourneert de huidige tijd ten opzichte van de oorspronkelijke inhoud, zonder dynamisch gesplitste advertenties. <span class="codeph"> getLocalTime</span> in <span class="codeph"> AdBreak</span> retourneert de begintijd van het einde ten opzichte van de oorspronkelijke inhoud. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="apiname"> AdBreak</span> </td> 
   <td colname="col2"><span class="codeph"> isWatched</span> , eigenschap. Geeft aan of de viewer de advertentie heeft gecontroleerd. </td> 
  </tr> 
 </tbody> 
</table>

