---
seo-title: Gebruik van opdrachtregels
title: Gebruik van opdrachtregels
uuid: b3a995de-653e-491a-9262-86dc56b9ce31
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---


# Gebruik van opdrachtregel {#command-line-usage}

Gebruik de volgende syntaxis om een licentie te genereren:

```
    java -jar AdobeLicenseGenerator.jar -m 
<i class="+ topic ph hi-d="" i "="">
 metadata 
 <i class="+ topic ph hi-d="" i "="">
   [options]
 </i class="+ topic>
</i class="+ topic>
```

`metadata` is een .metadata bestand dat de Adobe Access DRM-metagegevens bevat. Dit bestand kan worden verkregen van beveiligde inhoud met de optie `-d -m` van Media Packager.

Als u een eerder gegenereerde licentie wilt weergeven, gebruikt u de volgende syntaxis:

```
    java -jar AdobeLicenseGenerator.jar -d 
<i class="+ topic ph hi-d="" i "="">
  license
</i class="+ topic>
```

`license` is een bestand met een Adobe Access-licentie die door de licentiegenerator is gegenereerd.

In de volgende tabel worden de opdrachtregelopties beschreven die samen met de eerder vermelde syntaxis kunnen worden opgegeven:

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_skr_vry_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Optie opdrachtregel </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Beschrijving </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-c configfile</span> </td> 
   <td colname="2" class="- topic/entry "> Geef de locatie van het configuratiebestand op. Als deze optie niet wordt gebruikt, zoekt de licentiegenerator naar flashaccess.properties in de werkmap. De opties die op de bevellijn worden gespecificeerd hebben belangrijkheid over die aanwezig in het configuratiedossier. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-d <i class="+ topic/ph hi-d/i "><span class="+ topic/ph pr-d/codeph codeph"> licentiebestand</span></i> </p> </td> 
   <td colname="2" class="- topic/entry "> Informatie weergeven over een licentie die al is gegenereerd. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-leaf leaf-bestandsnaam</span> </td> 
   <td colname="2" class="- topic/entry "> Genereer een bladlicentie en schrijf de uitvoer naar een opgegeven bestand. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-m metadata-filename</span> </td> 
   <td colname="2" class="- topic/entry "> Geef de metagegevens voor de inhoud op waarvoor u een licentie wilt genereren. (Vereist om licentie te genereren) </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -noprompt</span> </td> 
   <td colname="2" class="- topic/entry ">Vraag niet of het doelbestand moet worden overschreven. Als het doelbestand al bestaat en <span class="codeph"> -o</span> niet is ingesteld, wordt een fout geretourneerd. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -o</span> </td> 
   <td colname="2" class="- topic/entry "> Als het doelbestand al bestaat, overschrijft u dit zonder dat u daarom wordt gevraagd. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-policy policy-num</span> </td> 
   <td colname="2" class="- topic/entry "> Als de metagegevens meerdere beleidsregels bevatten, geeft u het nummer op van het beleid dat u wilt gebruiken (te beginnen bij 1) om de licentie te genereren. Indien niet opgegeven, wordt het eerste beleid gebruikt. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-r ontvanger-cert</span> </td> 
   <td colname="2" class="- topic/entry ">Genereer een licentie voor de opgegeven ontvanger. Een apparaat of domeincertificaat kan worden gebruikt. Er kunnen meerdere <span class="+ topic/ph pr-d/codeph codeph"> -r </span>opties worden opgegeven om een licentie voor meerdere ontvangers te maken. </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-root-root-filename</span> </td> 
   <td colname="2" class="- topic/entry "> Genereer een hoofdlicentie en schrijf de uitvoer naar het opgegeven bestand. </td> 
  </tr> 
 </tbody> 
</table>

