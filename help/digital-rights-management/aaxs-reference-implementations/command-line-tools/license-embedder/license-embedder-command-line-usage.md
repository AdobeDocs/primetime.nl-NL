---
title: Gebruik van opdrachtregels
description: Gebruik van opdrachtregels
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---

# Gebruik van opdrachtregels {#command-line-usage}

Als u een licentie wilt insluiten, gebruikt u de volgende syntaxis:

```
    java -jar AdobeLicenseEmbedder.jar  
<i class="+ topic ph hi-d="" i "="">
  sourcefile destfile [options] 
</i class="+ topic>
```

* `sourcefile` is een gecodeerd FLV- of F4V-bestand.
* `destfile` Hiermee geeft u aan waar de gecodeerde inhoud met de ingesloten licentie moet worden geschreven. Als een map wordt opgegeven, wordt het bestand in deze map opgeslagen met dezelfde bestandsnaam als het bronbestand, maar de map mag niet de map zijn die het bronbestand bevat.

In de volgende tabel worden de opdrachtregelopties beschreven die samen met de eerder vermelde syntaxis kunnen worden opgegeven:

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_hnl_2sy_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Optie opdrachtregel </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Beschrijving </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -l license-filename </span> </td> 
   <td colname="2" class="- topic/entry "> Naam van het bestand met de licentie die moet worden ingesloten. Meerdere <span class="codeph"> -l </span> U kunt opties opgeven om meerdere licenties in te sluiten. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -m metadata-filename </span> </td> 
   <td colname="2" class="- topic/entry "> Geef de metagegevens voor de inhoud op waarvoor u een licentie wilt genereren. (Vereist om licentie te genereren) </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -noprompt </span> </td> 
   <td colname="2" class="- topic/entry "> Vraag niet of het doelbestand moet worden overschreven. Als het doelbestand al bestaat en <span class="codeph"> -o </span> is niet ingesteld, wordt een fout geretourneerd. </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o </span> </td> 
   <td colname="2" class="- topic/entry "> Als het doelbestand al bestaat, overschrijft u dit zonder dat u daarom wordt gevraagd. </td> 
  </tr> 
 </tbody> 
</table>
