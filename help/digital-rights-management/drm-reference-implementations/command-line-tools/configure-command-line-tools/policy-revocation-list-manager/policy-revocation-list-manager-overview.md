---
title: DRM Intrekkingslijstbeheer
description: DRM Intrekkingslijstbeheer
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# DRM Intrekkingslijstbeheer {#policy-revocation-list-manager}

Het opdrachtregelprogramma Primetime DRM Revocation List Manager gebruiken ( [!DNL AdobeRevocationListManager.jar]) om intrekkingslijsten te maken en te beheren en om te controleren of het beleid is ingetrokken.

Voordat u gaat werken [!DNL AdobeRevocationListManager.jar]moet u eigenschappen instellen in het dialoogvenster *Lijstbeheer voor beleidsupdates en eigenschappen van beheer van intrekkingslijsten* van het configuratiebestand.

>[!NOTE]
>
>U kunt ook alle eigenschappen van de Manager van de Lijst van de Intrekking van de Lijn specificeren.

## Gebruik van de opdrachtregel van Revocation List Manager {#revocation-list-manager-command-line-usage}

```
java -jar AdobeRevocationListManager.jar 
<i class="+ topic ph hi-d="" i "="">
 destfile 
 <i class="+ topic ph hi-d="" i "="">
  crlNumber [
  <i class="+ topic ph hi-d="" i "="">
   options] 
       java -jar AdobeRevocationListManager.jar -d 
   <i class="+ topic ph hi-d="" i "="">
     filename
   </i class="+ topic>
  </i class="+ topic>
 </i class="+ topic>
</i class="+ topic>
```

* `destfile` geeft de naam aan van het bestand waarin de eigenschappen van de intrekkingslijst zijn opgeslagen.
* `crlNumber` staat voor een niet-negatief versienummer van de certificaatintrekkingslijst (CRL). U moet dit aantal verhogen telkens als CRL wordt bijgewerkt.

**Tabel 5: Opdrachtregelopties**

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_a3y_wqy_n4">  
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> Opdrachtregeloptie </th> 
   <th colname="2" class="- topic/entry entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-c configfile</span> </td> 
   <td colname="2" class="- topic/entry "><p class="- topic/p ">Hier geeft u de naam en locatie op van het configuratiebestand. </p><p class="- topic/p ">Als u geen naam of locatie opgeeft, zoekt DRM Revocation List Manager naar <span class="filepath"> flashaccessstools.properties</span> in de huidige werkmap. </p><p>Opmerking: de opties die u op de opdrachtregel opgeeft, hebben voorrang op de opties die u in het configuratiebestand opgeeft. </p>Hier geeft u de locatie van het configuratiebestand op. Als u deze optie niet toepast, zoekt de Manager van de Lijst van de Intrekking naar <span class="filepath"> flashaccessstools.properties</span> in de werkmap. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-d bestandsnaam</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Geeft informatie weer over de intrekkingslijst. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-e-datum</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">(Optioneel) De vervaldatum van de intrekkingslijst. Gebruik een van de volgende indelingen: 
     <ul id="ul_2C89F8183C3647C593CB67576D9DED07"> 
      <li id="li_A866F6CBCB464193A119A6609C8F3B2A"><span class="+ topic/ph pr-d/codeph codeph">jjjj-mm-dd</span> </li> 
      <li id="li_B5F9F6C995E64464838DDE447848F707"><span class="+ topic/ph pr-d/codeph codeph">jjjj-mm-dd-h24:min:sec</span> </li> 
     </ul>Bijvoorbeeld, 2009-01-31-14:30:00 staat voor 31 januari om 2:30 uur. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">-f bestandsnaam[certificaatbestand]</span> </td> 
   <td colname="2" class="- topic/entry "> <p>Hiermee voegt u alle items uit de bestaande intrekkingslijst toe. U kunt slechts één bestaand bestand opgeven. </p> <p class="- topic/p ">Als de bestaande lijst is ondertekend met een andere referentie dan de referentie die u hebt gebruikt om de nieuwe lijst te ondertekenen, moet u het bijbehorende certificaatbestand opgeven naast de handtekening. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -noprompt</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Vraag niet of het doelbestand moet worden overschreven. Als het doelbestand al bestaat en <span class="codeph"> -o</span> niet is ingesteld, treedt een fout op. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -o</span> </td> 
   <td colname="2" class="- topic/entry "> Als het doelbestand al bestaat, kunt u het overschrijven zonder dat u hierom wordt gevraagd. </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">-r publisherName serialNumber revocationDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Hiermee wordt het certificaat ingetrokken dat is geïdentificeerd door <span class="codeph"> emittentName</span> en <span class="codeph"> serialNumber</span> op de opgegeven datum. De <span class="codeph"> emittentName</span> moet de naamnotatie 509 gebruiken. Bijvoorbeeld: <span class="codeph"> CN=12345,O=Adobe Systems Incorporated,C=US</span>. </p> <p>U moet de serienummers opgeven in een hexadecimale notatie. U moet ook de intrekkingsdatum in een van de volgende notaties opgeven: 
     <ul id="ul_1524FBC6818248F3A2B271243E649400"> 
      <li id="li_BC618EA2332D42A59B1B5434CAFFD2AF"><span class="+ topic/ph pr-d/codeph codeph">jjjj-mm-dd</span> </li> 
      <li id="li_97F77810D20C4CF2944EFCFF5DFAE467"><span class="+ topic/ph pr-d/codeph codeph">jjjj-mm-dd-h24:min:sec</span> </li> 
     </ul>Bijvoorbeeld 2008-12-1 of 2008-12-1-00:00:00 voor middernacht op 1 december 2008. Als u de intrekkingsdatum niet opgeeft, wordt de huidige datum automatisch toegepast. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Configuratieeigenschappen {#configuration-properties}

U moet referenties toepassen om intrekkingslijsten te ondertekenen. De volgende eigenschappen van de Manager van de Lijst van de Intrekking specificeren een PKCS12- dossier dat geloofsbrieven voor het ondertekenen van intrekkingslijsten (het Certificaat van de Server van de Vergunning), samen met het wachtwoord voor de cert omvat:

* `revocation.sign.certfile=license-server-credentials.pfx`
* `revocation.sign.certpass=password`
