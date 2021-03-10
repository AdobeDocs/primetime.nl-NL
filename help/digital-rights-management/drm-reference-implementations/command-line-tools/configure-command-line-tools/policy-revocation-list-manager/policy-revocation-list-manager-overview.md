---
title: DRM Intrekkingslijstbeheer
description: DRM Intrekkingslijstbeheer
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---


# DRM Beheer intrekkingslijst {#policy-revocation-list-manager}

Gebruik het bevel-lijn hulpmiddel van de Manager van de Lijst van de Intrekking van DRM Primetime ( [!DNL AdobeRevocationListManager.jar]) om intrekkingslijsten tot stand te brengen en te beheren, en te controleren of het beleid is ingetrokken.

Alvorens u [!DNL AdobeRevocationListManager.jar] in werking stelt, moet u eigenschappen in *de Manager van de Lijst van de Update van het Beleid en de Eigenschappen van de Manager van de Lijst van de Intrekking* van uw configuratiedossier plaatsen.

>[!NOTE]
>
>U kunt ook alle eigenschappen van de Manager van de Lijst van de Intrekking van de Lijn specificeren.

## Opdrachtregelgebruik van de manager van de intrekkingslijst {#revocation-list-manager-command-line-usage}

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
* `crlNumber` vertegenwoordigt een niet-negatief versienummer van de certificaatintrekkingslijst (CRL). U moet dit aantal verhogen telkens als CRL wordt bijgewerkt.

**Tabel 5: Opties voor opdrachtregel**

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
   <td colname="2" class="- topic/entry "><p class="- topic/p ">Hier geeft u de naam en locatie op van het configuratiebestand. </p><p class="- topic/p ">Als u geen naam of een plaats specificeert, zoekt de Manager van de Lijst van de Intrekking DRM naar <span class="filepath"> flashaccess.properties</span> in de huidige het werk folder. </p><p>Opmerking:  Opties die u op de opdrachtregel opgeeft, hebben voorrang op de opties die u in het configuratiebestand opgeeft. </p>Hier geeft u de locatie van het configuratiebestand op. Als u deze optie niet toepast, zoekt de Manager van de Lijst van de Intrekking naar <span class="filepath"> flashaccess.properties</span> in de het werk folder. </td> 
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
     </ul>2009-01-31-14:30:00 staat bijvoorbeeld voor 31 januari om 2:30 uur. </p> </td> 
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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Hiermee wordt het certificaat ingetrokken dat op de opgegeven datum is geïdentificeerd door <span class="codeph"> publisherName</span> en <span class="codeph"> serialNumber</span>. De <span class="codeph"> uitgeversnaam</span> moet het naamformaat van 509 gebruiken. Bijvoorbeeld <span class="codeph"> CN=12345,O=Adobe Systems Incorporated,C=US</span>. </p> <p>U moet de serienummers opgeven in een hexadecimale notatie. U moet ook de intrekkingsdatum in een van de volgende notaties opgeven: 
     <ul id="ul_1524FBC6818248F3A2B271243E649400"> 
      <li id="li_BC618EA2332D42A59B1B5434CAFFD2AF"><span class="+ topic/ph pr-d/codeph codeph">jjjj-mm-dd</span> </li> 
      <li id="li_97F77810D20C4CF2944EFCFF5DFAE467"><span class="+ topic/ph pr-d/codeph codeph">jjjj-mm-dd-h24:min:sec</span> </li> 
     </ul>Bijvoorbeeld 2008-12-1 of 2008-12-1-00:00:00 voor middernacht op 1 December 2008. Als u de intrekkingsdatum niet opgeeft, wordt de huidige datum automatisch toegepast. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Configuratieeigenschappen {#configuration-properties}

U moet referenties toepassen om intrekkingslijsten te ondertekenen. De volgende eigenschappen van de Manager van de Lijst van de Intrekking specificeren een PKCS12- dossier dat geloofsbrieven voor het ondertekenen van intrekkingslijsten (het Certificaat van de Server van de Vergunning), samen met het wachtwoord voor de cert omvat:

* `revocation.sign.certfile=license-server-credentials.pfx`
* `revocation.sign.certpass=password`