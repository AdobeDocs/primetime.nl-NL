---
title: Gebruik van opdrachtregels
description: Gebruik van opdrachtregels
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Gebruik van opdrachtregels {#command-line-usage}

Manager voor intrekkingslijsten bevindt zich in de map \Reference Implementation\Command Line Tools op de dvd. Gebruik een van de volgende syntaxis om het gereedschap uit te voeren:

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

* `destfile` Hiermee wordt aangegeven waar de intrekkingslijst wordt geschreven.
* `crlNumber` is een niet-negatief versienummer van de certificaatintrekkingslijst (CRL). Dit aantal zou moeten worden verhoogd telkens als CRL wordt bijgewerkt.

De volgende tabel bevat beschrijvingen van de opties voor de opdrachtregel die in de bovenstaande syntaxis worden getoond:

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
   <td colname="2" class="- topic/entry ">Hier geeft u de locatie van het configuratiebestand op. Als deze optie niet wordt gebruikt, zoekt de Manager van de Lijst van de Intrekking naar <span class="filepath"> flashaccessstools.properties</span> in de werkmap. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-d bestandsnaam</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Geeft informatie weer over de intrekkingslijst. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-e-datum</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">(Optioneel) De vervaldatum van de intrekkingslijst. De indeling gebruiken <span class="+ topic/ph pr-d/codeph codeph">jjjj-mm-dd</span> of <span class="+ topic/ph pr-d/codeph codeph">jjjj-mm-dd-h24:min:sec</span> (bijvoorbeeld 2009-01-31-14):30:00 staat voor 31 januari om 2:30 uur). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">-f bestandsnaam[certificaatbestand]</span> </td> 
   <td colname="2" class="- topic/entry ">Hiermee voegt u alle items uit de bestaande intrekkingslijst toe. Er kan slechts één bestaand bestand worden opgegeven. <p class="- topic/p ">Als deze bestaande lijst met een andere referentie is ondertekend dan de lijst die wordt gebruikt om de nieuwe lijst te ondertekenen, geeft u het certificaatbestand ervan op, zodat de handtekening kan worden geverifieerd. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -noprompt</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Vraag niet of het doelbestand moet worden overschreven. Als het doelbestand al bestaat en -o niet is ingesteld, wordt een fout geretourneerd. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -o</span> </td> 
   <td colname="2" class="- topic/entry "> Als het doelbestand al bestaat, overschrijft u dit zonder dat u daarom wordt gevraagd. </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">-r publisherName serialNumber revocationDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Hiermee wordt het certificaat ingetrokken dat is geïdentificeerd door <span class="codeph"> emittentName</span> en <span class="codeph"> serialNumber</span> op de gegeven datum. De <span class="codeph"> emittentName</span> moet de naamnotatie 509 volgen (bijvoorbeeld <span class="codeph"> CN=12345,O=Adobe Systems Incorporated,C=US</span>). Geef serienummers op in hexadecimale vorm. Intrekkingsdatum opgeven als <span class="+ topic/ph pr-d/codeph codeph">jjjj-mm-dd</span> of <span class="+ topic/ph pr-d/codeph codeph">jjjj-mm-dd-h24:min:sec</span>, bijvoorbeeld 2008-12-1 of 2008-12-1-00:00:00 voor middernacht op 1 december 2008. Als de intrekkingsdatum niet is opgegeven, wordt de huidige datum gebruikt. </p> </td> 
  </tr> 
 </tbody> 
</table>
