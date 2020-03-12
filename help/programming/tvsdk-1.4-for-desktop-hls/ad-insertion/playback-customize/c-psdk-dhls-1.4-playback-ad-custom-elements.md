---
description: TVSDK biedt klassen en methoden waarmee u het afspeelgedrag kunt aanpassen van inhoud die reclame bevat.
seo-description: TVSDK biedt klassen en methoden waarmee u het afspeelgedrag kunt aanpassen van inhoud die reclame bevat.
seo-title: API-elementen voor het afspelen van advertenties
title: API-elementen voor het afspelen van advertenties
uuid: 61ebbfd7-696c-4a5b-8dbb-682770cd5840
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# API-elementen voor het afspelen van advertenties{#api-elements-for-ad-playback}

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
   <td colname="col1"><span class="codeph"> AdvertisingMetadata</span> </td> 
   <td colname="col2">Bepaal of een advertentieeinde moet worden gemarkeerd als gevolgd door een viewer en zo ja, wanneer om het te markeren. Het gevolgde beleid instellen en ophalen met 
    <ph>
     de <span class="codeph"> eigenschap adBreakAsWatched</span> .
    </ph> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AdBreakPolicy</span> </td> 
   <td colname="col2"> Hiermee worden mogelijke afspeelbeleidsregels voor ad-hocafbrekingen opgesomd. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> Advertentiebeleid</span> </td> 
   <td colname="col2"> Hiermee geeft u een overzicht van het mogelijke afspeelbeleid voor advertenties. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AdPolicySelector</span> </td> 
   <td colname="col2"> Interface die aanpassing van TVSDK en gedrag toestaat. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> DefaultAdPolicySelector</span> </td> 
   <td colname="col2"> Klasse die het standaardgedrag van TVSDK uitvoert. Uw toepassing kan deze klasse overschrijven om het standaardgedrag aan te passen zonder de volledige interface te implementeren. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> MediaPlayer</span> </td> 
   <td colname="col2"> 
    <ul id="ul_37700A741403448A8760FDDA68B099AA"> 
     <li id="li_B465170D449E49489C5924572BEEB4A5"><span class="codeph"> localTime</span>. <p>Dit is de lokale tijd van het afspelen, exclusief de geplaatste en afgebroken foto's. </p> </li> 
     <li id="li_D9D68CF428904BB2B84E1BCE828A90DC"> <span class="codeph"> seekToLocal</span>. <p>Hier wordt gezocht ten opzichte van een lokale tijd in de stream. </p> </li> 
     <li id="li_9DBCA75537DC4824AA66B53A3FA28812"><span class="codeph"> getTimeline.convertToLocalTime</span>. <p>De virtuele positie op de tijdlijn wordt geconverteerd naar de lokale positie. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> TimelineItem</span> </td> 
   <td colname="col2"> 
    <ul id="ul_99AD34F823DB4F10937EE39DAD0C0B72"> 
     <li id="li_87E2DA15ECE74CFE9C9FBBE8F4B62440"><span class="codeph"> gecontroleerd</span>. <p>Geeft aan of de viewer de advertentie heeft gecontroleerd. </p> </li> 
     <li id="li_A9E5A9CF701C48BC94C93F28C114778D"><span class="codeph"> localRange</span>. <p>De startpositie en de duur van een advertentie-einde of advertentie ten opzichte van de oorspronkelijke inhoud. </p> </li> 
     <li id="li_070BDA0BF4184863AF44652BD5A0CCEC"><span class="codeph"> virtualRange</span>. <p>De startpositie en de duur van een advertentie-einde of advertentie op de virtuele tijdlijn na afweging van alle geplaatste en afbrekingen. </p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

