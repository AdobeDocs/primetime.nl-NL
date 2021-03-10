---
description: Het TVSDK-meldingssysteem produceert verschillende fouten, waarschuwingen en informatieve kennisgevingen die diagnostische metagegevens bieden.
title: Meldingscodes
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---


# TVSDK-meldingssysteem {#tvsdk-notification-system}

Het TVSDK-meldingssysteem produceert verschillende fouten, waarschuwingen en informatieve kennisgevingen die diagnostische metagegevens bieden.

Meldingsobjecten bevatten informatie over de status van de speler. TVSDK biedt een chronologisch gesorteerde lijst met berichtobjecten en elk bericht bevat de volgende metagegevens:

<table frame="all" colsep="1" rowsep="1" id="table_DBA8CACF02DB4AF2B053E560850B49CE"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Element </th> 
   <th colname="2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> type</span></td> 
   <td colname="2">Het berichttype. Afhankelijk van het platform verwijst deze eigenschap naar een opgesomd type met mogelijke waarden van 
    <pre>
      INFORMATIE, WAARSCHUWING of FOUT. Dit is de groepering op hoofdniveau voor meldingen.
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> code</span></td> 
   <td colname="2">De numerieke representatie die aan het bericht is toegewezen. 
    <ul id="ul_31AB497C6FFA452496DD09B0D78687B9"> 
     <li id="li_53E75022C50246E0982E315D04EFD8B3">Foutmeldingsgebeurtenissen, van 100000 tot 19999 </li> 
     <li id="li_11AE91D1325E4F718228E662C9C55F9A">Waarschuwingsmeldingsgebeurtenissen, van 200000 tot en met 299999 </li> 
     <li id="li_6D3EA03845294DC2BAD1ACF507639E51">Gebeurtenissen voor de kennisgeving van informatie, van 300000 tot 399999 </li> 
    </ul> <p>Elk bereik op hoofdniveau, zoals fouten, wordt onderverdeeld in subbereiken, zoals 101000 tot en met 101999 die de afspeelfouten vertegenwoordigen. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> name</span></td> 
   <td colname="2">Een tekenreeks die een door de mens leesbare beschrijving van de code bevat, zoals <span class="codeph"> SEEK_ERROR</span>. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> metagegevens</span> </td> 
   <td colname="2">Sleutel-waardeparen die extra relevante informatie over de kennisgeving bevatten. Een sleutel met de naam <span class="codeph"> URL</span> zou bijvoorbeeld worden gekoppeld aan een waarde die een URL is die gerelateerd is aan het bericht, zoals een ongeldige URL die een fout heeft veroorzaakt. </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><span class="codeph"> innerNotification</span></td> 
   <td colname="2">Een verwijzing naar een ander <span class="codeph"> PTNotification</span>-object dat deze melding rechtstreeks heeft beïnvloed. Een voorbeeld kan een melding zijn over een fout bij het invoegen van een invoegpositie die direct overeenkomt met een invoegconflict in een tijdlijn. Niet alle meldingen bevatten een binnenste melding. </td> 
  </tr> 
 </tbody> 
</table>

