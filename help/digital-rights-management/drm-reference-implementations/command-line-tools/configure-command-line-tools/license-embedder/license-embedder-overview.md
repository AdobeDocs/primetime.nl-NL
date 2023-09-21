---
title: Overzicht
description: Overzicht
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# DRM-licentie insluiten {#license-embedder}

Gebruiken [!DNL AdobeLicenseEmbedder.jar] om vooraf gegenereerde licenties in te sluiten in inhoud die door Media Packager wordt beveiligd.

## Gebruik van de opdrachtregel Licentie insluiten {#license-embedder-command-line-usage}

```
java -jar AdobeLicenseEmbedder.jar sourcefile destfile [options]
```

* `sourcefile` vertegenwoordigt een gecodeerd bestand.
* `destfile` geeft de naam aan van het bestand waarin de gecodeerde inhoud met de ingesloten licentie wordt opgeslagen.

  Als u een map opgeeft, wordt het bestand opgeslagen in de doelmap. De naam van het bronbestand wordt ook de naam van het bestand dat in de doelmap is opgeslagen.

In de volgende tabel worden de opdrachtregelopties beschreven die u kunt opgeven:

**Tabel 7: Opties**

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
   <td colname="2" class="- topic/entry "> Naam van het bestand dat de licentie bevat die u wilt insluiten. U kunt meerdere <span class="codeph"> -l </span> opties voor het insluiten van meerdere licenties. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -m metadata-filename </span> </td> 
   <td colname="2" class="- topic/entry "> Hier geeft u de metagegevens voor de inhoud op waarvoor u een licentie kunt genereren. Deze optie is vereist om een licentie te genereren. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -noprompt </span> </td> 
   <td colname="2" class="- topic/entry "> Vraag niet of het doelbestand moet worden overschreven. Als het doelbestand al bestaat en <span class="codeph"> -o </span> is niet toegepast, treedt een fout op. </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o </span> </td> 
   <td colname="2" class="- topic/entry "> Als het doelbestand al bestaat, kunt u het overschrijven zonder dat u hierom wordt gevraagd. </td> 
  </tr> 
 </tbody> 
</table>
