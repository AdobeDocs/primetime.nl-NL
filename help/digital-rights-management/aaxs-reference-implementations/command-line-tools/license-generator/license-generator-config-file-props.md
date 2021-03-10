---
title: Eigenschappen van configuratiebestand
description: Eigenschappen van configuratiebestand
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---


# Eigenschappen van configuratiebestand {#configuration-file-properties}

Voordat u de licentiegenerator uitvoert, geeft u waarden op voor de eigenschappen van de licentiegenerator. In het configuratiebestand worden de volgende eigenschappen opgegeven. Voor eigenschapsnamen die *n* omvatten, *n* vertegenwoordigt een geheel dat met 1 begint en voor elke instantie van het bezit stijgt.

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_qk1_rry_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> Eigenschap </th> 
   <th colname="2" class="- topic/entry entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licensegen.minClientVersion</span> </td> 
   <td colname="2" class="- topic/entry "> Stel de minimaal ondersteunde clientversie in. Als deze optie niet is ingesteld, worden standaard alle versies ondersteund. Stel deze waarde in om te bepalen hoe oudere clients reageren op licentievereisten die ze niet ondersteunen. Geef x (voor Adobe Access x.0) op, waarbij x het hoofdreleasenummer is. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licensegen.keyServerCert</span> </td> 
   <td colname="2" class="- topic/entry "> Sleutelservercertificaat (een door Adobe uitgegeven certificaat van de Server van de Vergunning dat door de Zeer belangrijke Server wordt gebruikt). Dit certificaat wordt alleen gebruikt als uit de metagegevens/het beleid blijkt dat een sleutelserver is vereist voor de levering van sleutelbestanden aan iOS-apparaten. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licensegen.sign.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> Het PKCS12-bestand met de referenties van de licentieserver voor het ondertekenen van licenties. Deze eigenschap moet verwijzen naar een .pfx-bestand dat een certificaat en een persoonlijke sleutel bevat. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licensegen.sign.certpass</span> </td> 
   <td colname="2" class="- topic/entry ">Het wachtwoord dat wordt gebruikt om het bestand te beveiligen dat wordt opgegeven door <span class="+ topic/ph pr-d/codeph codeph"> licensegen.sign.certfile.</span> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">licensegen.domainca.n</span> </td> 
   <td colname="2" class="- topic/entry "> Als het produceren van domein-gebonden vergunningen, moeten één of meerdere certificaten van MAC van het Domein worden gespecificeerd om op de domeinautoriteiten te wijzen die door deze vergunningsuitgever worden vertrouwd. Als de licentieontvanger een domeincertificaat is, dat niet is uitgegeven door een van de opgegeven Domein CA's, kan geen licentie worden gegenereerd. This property specifies a .cer file that contains the certificate only (either PEM or DER format is acceptable). n moet monotonisch toenemen, beginnend bij 1. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">licensegen.keys.asymmetric.licenseServerCredential.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Optioneel PKCS12-bestand met aanvullende licentieserverreferenties voor het decoderen van de CEK in de metagegevens en het beleid. Aanvullende referenties kunnen worden geconfigureerd als inhoud eerder is verpakt met een ander licentieservercertificaat dan is opgegeven door <span class="codeph"> licensegen.sign.certfile</span>. Deze eigenschap moet verwijzen naar een .pfx</span>-bestand met een certificaat en een persoonlijke sleutel. <span class="filepath"> n moet monotonisch toenemen, beginnend bij 1. </span></p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">licensegen.keys.asymmetric.licenseServerCredential.n.password</span> </td> 
   <td colname="2" class="- topic/entry ">Het wachtwoord dat wordt gebruikt om het bestand te beveiligen dat wordt opgegeven door: <p><span class="+ topic/ph pr-d/codeph codeph"> licensegen.keys.asymmetric.licenseServerCredential.n</span> </p> </td> 
  </tr> 
 </tbody> 
</table>

