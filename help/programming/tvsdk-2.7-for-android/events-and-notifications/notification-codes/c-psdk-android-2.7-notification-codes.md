---
description: Het TVSDK-meldingssysteem produceert verschillende fouten, waarschuwingen en informatieve kennisgevingen die diagnostische metagegevens bieden.
seo-description: Het TVSDK-meldingssysteem produceert verschillende fouten, waarschuwingen en informatieve kennisgevingen die diagnostische metagegevens bieden.
seo-title: Meldingscodes
title: Meldingscodes
uuid: 24476204-5c35-4ff9-810d-77698ea18b53
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Overzicht {#notification-codes-overview}

Het TVSDK-meldingssysteem produceert verschillende fouten, waarschuwingen en informatieve kennisgevingen die diagnostische metagegevens bieden.

De voorwerpen van het bericht verstrekken informatie die met de status van de speler verwant is. TVSDK biedt een chronologisch gesorteerde lijst met berichtobjecten. Elke melding bevat de volgende metagegevens:

<table frame="all" colsep="1" rowsep="1" id="table_1A32EFFE1834438D8261886EC9D7250D"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Element </th> 
   <th colname="2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> type</span> </td> 
   <td colname="2"> <p>Het berichttype. </p> <p>Afhankelijk van het platform, is dit bezit een opgesomd type met mogelijke waarden van INFO, WARN, en FOUT. Dit is de groepering op hoofdniveau voor meldingen. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> code</span> </td> 
   <td colname="2"> <p>Aan de kennisgevingen worden de volgende numerieke weergaven toegewezen: 
     <ul id="ul_A86BF89D6B3B410E81FAD718D3C4A9F0"> 
      <li id="li_8180972D704C40098723734DD4B45643">Foutmeldingsgebeurtenissen, van 100000 tot 19999 </li> 
      <li id="li_0EC29EA5F0034E5EBFEF8E68A6498D39">Waarschuwingsmeldingsgebeurtenissen, van 200000 tot en met 299999 </li> 
      <li id="li_189A53D3D7EF4960A521AB04D00DCF70">Gebeurtenissen voor de kennisgeving van informatie, van 300000 tot 399999 </li> 
     </ul> </p> <p>Elk bereik op hoofdniveau, zoals fouten, wordt onderverdeeld in subbereiken, zoals 101000 tot en met 101999 die de afspeelfouten vertegenwoordigen. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> name</span> </td> 
   <td colname="2">Een tekenreeks die een leesbare beschrijving bevat van de meldingsgebeurtenis, zoals <span class="codeph"> SEEK_ERROR</span>. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> metagegevens</span> </td> 
   <td colname="2"> <p>Sleutel-waardeparen die extra relevante informatie over de kennisgeving bevatten. </p> <p>Een sleutel met de naam <span class="codeph"> URL</span> levert bijvoorbeeld een waarde op die gerelateerd is aan het bericht, zoals een ongeldige URL die een fout heeft veroorzaakt. </p> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><span class="codeph"> innerNotification</span> </td> 
   <td colname="2"> <p>Een verwijzing naar een ander <span class="codeph"> MediaPlayerNotification</span> -object dat rechtstreeks invloed heeft op deze melding. </p> <p>Een voorbeeld kan een melding zijn over een fout bij het invoegen van een invoegpositie die direct overeenkomt met een invoegconflict in een tijdlijn. Niet alle meldingen bevatten een binnenste melding. </p> </td> 
  </tr> 
 </tbody> 
</table>

