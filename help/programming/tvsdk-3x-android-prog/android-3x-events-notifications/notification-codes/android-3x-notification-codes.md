---
description: Het TVSDK-meldingssysteem produceert verschillende fouten, waarschuwingen en informatieve kennisgevingen die diagnostische metagegevens bieden.
title: Meldingscodes
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# Meldingscodes {#notification-codes}

Het TVSDK-meldingssysteem produceert verschillende fouten, waarschuwingen en informatieve kennisgevingen die diagnostische metagegevens bieden.

De voorwerpen van het bericht verstrekken informatie die met de status van de speler verwant is. TVSDK biedt een chronologisch gesorteerde lijst met berichtobjecten. Elke melding bevat de volgende metagegevens:

<table frame="all" colsep="1" rowsep="1" id="table_1A32EFFE1834438D8261886EC9D7250D"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"><b> Element</b></th> 
   <th colname="2" class="entry"><b> Beschrijving</b></th> 
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
      <li id="li_0EC29EA5F0034E5EBFEF8E68A6498D39">Waarschuwingsmeldingsgebeurtenissen, van 200000 tot 299999 </li> 
      <li id="li_189A53D3D7EF4960A521AB04D00DCF70">Gebeurtenissen voor de kennisgeving van informatie, van 300000 tot 399999 </li> 
     </ul> </p> <p>Elk bereik op hoofdniveau, zoals fouten, wordt onderverdeeld in subbereiken, zoals 101000 tot en met 101999 die de afspeelfouten vertegenwoordigen. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> name</span> </td> 
   <td colname="2">Een tekenreeks die een leesbare beschrijving van de meldingsgebeurtenis bevat, zoals <span class="codeph"> ZOEKEN_FOUT</span>. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> metagegevens</span> </td> 
   <td colname="2"> <p>Sleutel-waardeparen die extra relevante informatie over de kennisgeving bevatten. </p> <p>Bijvoorbeeld een toets met de naam <span class="codeph"> URL</span> zou een waarde opgeven die een URL is die gerelateerd is aan het bericht, zoals een ongeldige URL die een fout heeft veroorzaakt. </p> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><span class="codeph"> innerNotification</span> </td> 
   <td colname="2"> <p>Een verwijzing naar een andere <span class="codeph"> MediaPlayerNotification</span> object dat rechtstreeks invloed heeft op deze melding. </p> <p>Een voorbeeld kan een melding zijn over een fout bij het invoegen van een invoegpositie die direct overeenkomt met een invoegconflict in een tijdlijn. Niet alle meldingen bevatten een binnenste melding. </p> </td> 
  </tr> 
 </tbody> 
</table>
