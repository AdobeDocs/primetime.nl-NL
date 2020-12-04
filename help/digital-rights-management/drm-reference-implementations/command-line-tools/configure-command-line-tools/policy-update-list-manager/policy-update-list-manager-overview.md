---
seo-title: Overzicht
title: Overzicht
uuid: 19d05867-c210-4cd0-bc2f-5dd75f5774e5
translation-type: tm+mt
source-git-commit: a33e1f290fcf78e6f131910f6037f4803f7be98d
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---


# DRM Policy Update List Manager {#policy-update-list-manager}

Gebruik het bevel-lijn hulpmiddel van de Manager van de Lijst van de Update van het Beleid Primetime DRM ( [!DNL AdobePolicyUpdateListManager.jar]) om lijsten van beleidsupdate tot stand te brengen en te beheren DRM, en om te controleren of het beleid is bijgewerkt of ingetrokken.

Alvorens u het bevel-lijn hulpmiddel van de Manager van de Lijst van de Update van het Beleid in werking stelt, moet u eigenschappen in *de Manager van de Lijst van de Update van het Beleid en de Eigenschappen van de Manager van de Lijst van de Intrekking* van uw configuratiedossier plaatsen.

>[!NOTE]
>
>U kunt ook alle eigenschappen van de Manager van de Lijst van de Update van het Beleid van de bevellijn specificeren.

## Het bevel-lijn gebruik van de Manager van de Lijst van de Update van het beleid {#policy-update-list-manager-command-line-usage}

**Een lijst met beleidsupdates maken:**

```
java -jar AdobePolicyUpdateListManager.jar  
<i class="+ topic ph hi-d="" i "="">
  destfile [ 
 <i class="+ topic ph hi-d="" i "="">
   options]  
 </i class="+ topic> 
</i class="+ topic>
```

* `destfile` Hiermee wordt de naam aangegeven van het bestand waarin de lijst met DRM-beleidsupdates is geschreven.

**Een bestaande lijst met beleidsupdates weergeven:**

```
java -jar AdobePolicyUpdateListManager.jar -d  
<i class="+ topic ph hi-d="" i "="">
  filename 
</i class="+ topic>
```

* `filename` De naam van het bestand met de lijst met beleidsupdates.

**Tabel 4: Opties voor opdrachtregel**

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_ghb_jqy_n4">  
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Opdrachtregeloptie </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Beschrijving </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -c configfile  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Hier geeft u de naam en locatie op van het configuratiebestand. </p> <p class="- topic/p ">Als u geen naam of een plaats specificeert, zoekt de Manager van de Lijst van de Update van het Beleid DRM naar <span class="filepath"> flashaccess.properties </span> in de huidige werkende folder. </p> <p>Opmerking:  Opties die u op de opdrachtregel opgeeft, hebben voorrang op de opties die u in het configuratiebestand opgeeft. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -d bestandsnaam  </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Hiermee geeft u informatie weer over de updatelijst voor DRM-beleid. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -e-datum  </span> </td> 
   <td colname="2" class="- topic/entry "> <p>(Optioneel) De vervaldatum van de updatelijst voor DRM-beleid. </p> <p>Gebruik de notatie <span class="+ topic/ph pr-d/codeph codeph"> jjjj-mm-dd </span> of <span class="+ topic/ph pr-d/codeph codeph"> jjjj-mm-dd-h24:min:sec </span> (bijvoorbeeld 2009-01-31-14:30:00 staat voor januari 31 om 2:30 PM). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -f bestandsnaam [certfile]  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Voegt alle ingangen van de bestaande DRM lijst van de beleidsupdate toe. U kunt slechts één bestaand bestand opgeven. </p> <p class="- topic/p ">Als de bestaande lijst is ondertekend met een andere referentie dan de referentie die wordt gebruikt om de nieuwe lijst te ondertekenen, moet u het certificaatbestand ervan opgeven om de handtekening te verifiëren. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -noprompt  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Vraag niet of het doelbestand moet worden overschreven. Als het doelbestand al bestaat en <span class="codeph"> -o </span> niet is ingesteld, treedt een fout op. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Als het doelbestand al bestaat, overschrijft u dit zonder dat u daarom wordt gevraagd. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -r  </span> <span class="+ topic/ph pr-d/codeph codeph"> Datum beleidsID  </span> "  <span class="+ topic/ph pr-d/codeph codeph"> reasonCode  </span>" "  <span class="+ topic/ph pr-d/codeph codeph"> reasonText  </span>" "  <span class="+ topic/ph pr-d/codeph codeph"> reasonURL  </span>" </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">(Optioneel) Hiermee wordt de DRM-beleidsidentiteitskaart op de opgegeven datum ingetrokken. U kunt een optionele redencode, redentekst en redenURL opgeven. U moet een lege tekenreeks "" opgeven om aan te geven dat er geen waarde is opgegeven voor de optionele parameters. U kunt de datum in <span class="+ topic/ph pr-d/codeph codeph"> jjjj-mm-dd </span> of <span class="+ topic/ph pr-d/codeph codeph"> jjjj-mm-dd-h24:min:sec </span> in deze notaties specificeren. 2008-12-1 of 2008-12-1-00:00:00 staat bijvoorbeeld voor middernacht op 1 december 2008). Als u geen datum opgeeft, wordt de huidige datum automatisch toegepast. Daarom moet de redencode groter zijn dan of gelijk aan 0. U kunt ook opties voor meerdere rijen opgeven. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-rf <span class="+ topic/ph pr-d/codeph codeph"> policyFilename </span> <span class="+ topic/ph pr-d/codeph codeph"> datum </span> " <span class="+ topic/ph pr-d/codeph codeph"> reasonCode </span>" " <span class="+ topic/ph pr-d/codeph codeph"> reasonText </span>" " <span class="+ topic/ph pr-d/codeph codeph"> reasonURL </span>" </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Voert dezelfde handeling uit als de optie <span class="codeph"> -r </span>. De DRM-beleidsidentificatie wordt echter uit een opgegeven bestand geëxtraheerd. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -u policyFilename " reasonCode" " reasonText" " reasonURL"  </span> </td> 
   <td colname="2" class="- topic/entry "> <p>Vervangt om het even welk passend DRM beleid in een vergunningsverzoek met dit beleid DRM door de bepaalde redencode (facultatief), redentekst (facultatief), en redenURL (facultatief) te gebruiken. </p> <p>Een lege tekenreeks '' geeft aan dat u geen waarde hebt opgegeven voor de optionele parameters. </p> <p>De redencode moet groter dan of gelijk aan <span class="codeph"> 0 </span> zijn. U kunt meerdere <span class="codeph"> -u </span> opties specificeren. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Configuratieeigenschappen {#configuration-properties}

De volgende eigenschappen van de Manager van de Lijst van de Update van het Beleid van Primetime DRM specificeren een PKCS12 dossier dat geloofsbrieven voor het ondertekenen van intrekkingslijsten (het Certificaat van de Server van de Vergunning), samen met een wachtwoord omvat.

* `revocation.sign.certfile=license-server-credentials.pfx`
* `revocation.sign.certpass=password`