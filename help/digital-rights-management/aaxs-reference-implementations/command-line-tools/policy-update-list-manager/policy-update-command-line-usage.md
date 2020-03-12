---
seo-title: Gebruik van opdrachtregels
title: Gebruik van opdrachtregels
uuid: 1c3a450d-5d9c-4437-89dd-1bd8719268b7
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Gebruik van opdrachtregels {#command-line-usage}

De Manager van de Lijst van de Update van het beleid is in de \ van de Implementatie \ van de Referentie de folder van Hulpmiddelen van de Lijn van het Bevel op DVD. Gebruik de volgende syntaxis om een lijst met beleidsupdates te maken:

```
    java -jar AdobePolicyUpdateListManager.jar  
<i class="+ topic ph hi-d="" i "="">
  destfile [ 
 <i class="+ topic ph hi-d="" i "="">
   options]  
 </i class="+ topic> 
</i class="+ topic>
```

* `destfile` Hiermee wordt aangegeven waar de lijst met beleidsupdates wordt geschreven.

Gebruik de volgende syntaxis om een bestaande lijst met beleidsupdates weer te geven:

```
    java -jar AdobePolicyUpdateListManager.jar -d  
<i class="+ topic ph hi-d="" i "="">
  filename 
</i class="+ topic>
```

De volgende tabel bevat beschrijvingen van de opties voor de opdrachtregel die in de bovenstaande syntaxis worden getoond:

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_ghb_jqy_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Optie voor opdrachtregel </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Beschrijving </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -c configfile </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Hier geeft u de locatie van het configuratiebestand op. Als deze optie niet wordt gebruikt, zal de Manager van de Lijst van de Update van het Beleid <span class="filepath"> flashaccess.properties </span> in de het werk folder zoeken. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -d bestandsnaam </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Geeft informatie weer over de lijst met beleidsupdates. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -e-datum </span> </td> 
   <td colname="2" class="- topic/entry "> (Optioneel) De vervaldatum van de lijst met beleidsupdates. Gebruik de notatie <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd </span> of <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:sec </span> (bijvoorbeeld 2009-01-31-14:30:00 staat voor 31 januari om 2:30 uur). </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -f bestandsnaam [certfile] </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Voegt alle ingangen van de bestaande lijst van de beleidsupdate toe. Er kan slechts één bestaand bestand worden opgegeven. </p> <p class="- topic/p ">Als deze bestaande lijst is ondertekend met een andere referentie dan die waarmee de nieuwe lijst wordt ondertekend, geeft u het certificaatbestand op, zodat de handtekening kan worden geverifieerd. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -noprompt </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Vraag niet of het doelbestand moet worden overschreven. Als het doelbestand al bestaat en <span class="codeph"> -o </span> niet is ingesteld, wordt een fout geretourneerd. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Als het doelbestand al bestaat, overschrijft u dit zonder dat u daarom wordt gevraagd. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -r </span> beleidsID <span class="+ topic/ph pr-d/codeph codeph"> datum </span> " <span class="+ topic/ph pr-d/codeph codeph"> reasonCode </span>" <span class="+ topic/ph pr-d/codeph codeph"> reasonText </span>" <span class="+ topic/ph pr-d/codeph codeph"> reasonURL </span>" </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">(Optioneel) Hiermee wordt de beleids-id op de opgegeven datum ingetrokken. Er kan ook een optionele redencode, redentekst en redenURL worden opgegeven. Geef een lege tekenreeks op "" om aan te geven dat er geen waarde is opgegeven voor de optionele parameters. Geef de datum op als <span class="+ topic/ph pr-d/codeph codeph"> jjjj-mm-dd </span> of <span class="+ topic/ph pr-d/codeph codeph"> jjjj-mm-dd-h24:min:sec </span> (bijvoorbeeld 2008-12-1 of 2008-12-1-00:00:00 voor middernacht op 1 december 2008). Als er geen datum is opgegeven, wordt de huidige datum gebruikt. De redencode moet groter zijn dan of gelijk zijn aan 0. U kunt meerdere -r-opties opgeven. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-rf <span class="+ topic/ph pr-d/codeph codeph"> policyFilename </span> <span class="+ topic/ph pr-d/codeph codeph"> date </span> " <span class="+ topic/ph pr-d/codeph codeph"> reasonCode </span>" <span class="+ topic/ph pr-d/codeph codeph"> reasonText </span>" <span class="+ topic/ph pr-d/codeph codeph"> reasonURL </span>" </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Voert de zelfde actie uit zoals - r vlag, maar haalt beleidsidentificatie uit het bepaalde dossier. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -u policyFilename " reasonCode" " reasonText" " reasonURL" </span> </td> 
   <td colname="2" class="- topic/entry "> <p>Vervangt om het even welk passend beleid in een vergunningsverzoek met dit beleid gebruikend de bepaalde redencode (facultatief), redentekst (facultatief), en redenURL (facultatief). </p> <p>Geef een lege tekenreeks op "" om aan te geven dat er geen waarde is opgegeven voor de optionele parameters. </p> <p>De redencode moet groter zijn dan of gelijk zijn aan <span class="codeph"> 0 </span>. U kunt meerdere <span class="codeph"> -u </span> opties opgeven. </p> </td> 
  </tr> 
 </tbody> 
</table>

