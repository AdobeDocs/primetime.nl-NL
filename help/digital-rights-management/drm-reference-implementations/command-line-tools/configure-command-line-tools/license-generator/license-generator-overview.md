---
title: Overzicht
description: Overzicht
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 0%

---


# DRM-licentiegenerator {#license-generator}

Gebruik [!DNL AdobeLicenseGenerator.jar] om licenties te genereren zonder dat de client een licentieaanvraag naar een server moet verzenden. Vervolgens kunt u een vooraf gegenereerde licentie insluiten in de inhoud of de licentie leveren aan de client via andere mechanismen, zoals een eenvoudige HTTP-webserver.

## Het bevel-lijn gebruik van de Generator van de vergunning {#license-generator-command-line-usage}

**Een licentie genereren:**

```
java -jar AdobeLicenseGenerator.jar -m 
<i class="+ topic ph hi-d="" i "="">
 metadata 
 <i class="+ topic ph hi-d="" i "="">
   [options]
 </i class="+ topic>
</i class="+ topic>
```

* `metadata` - Bevat de Adobe Primetime DRM-metagegevens.

   U kunt dit bestand ophalen van beveiligde inhoud met de `-d -m`-opties in Media Packager.

**Een eerder gegenereerde licentie weergeven:**

```
java -jar AdobeLicenseGenerator.jar -d 
<i class="+ topic ph hi-d="" i "="">
  license
</i class="+ topic>
```

* `license` - Bevat een Adobe Primetime DRM-licentie die is gegenereerd door de licentiegenerator.

**Tabel 6: Opties**

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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Hier geeft u de naam en locatie op van het configuratiebestand. </p> <p class="- topic/p ">Als u geen naam of locatie opgeeft, zoekt de DRM-licentiegenerator naar <span class="filepath"> flashaccess.properties</span> in de huidige werkmap. </p> <p>Opmerking:  Opties die u op de opdrachtregel opgeeft, hebben voorrang op de opties die u in het configuratiebestand opgeeft. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-d <i class="+ topic/ph hi-d/i "><span class="+ topic/ph pr-d/codeph codeph"> licentiebestand</span></i> </p> </td> 
   <td colname="2" class="- topic/entry "> Geeft informatie weer over een licentie die al is gegenereerd. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-leaf leaf-bestandsnaam</span> </td> 
   <td colname="2" class="- topic/entry "> Hiermee genereert u een bladlicentie en slaat u de uitvoer op in een opgegeven bestand. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-m metadata-filename</span> </td> 
   <td colname="2" class="- topic/entry "> Hier geeft u de metagegevens voor de inhoud op waarvoor u een licentie moet genereren. Deze optie is vereist om een licentie te genereren. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -noprompt</span> </td> 
   <td colname="2" class="- topic/entry ">Vraag niet of het doelbestand moet worden overschreven. Als het doelbestand al bestaat en <span class="codeph"> -o</span> niet is ingesteld, treedt een fout op. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -o</span> </td> 
   <td colname="2" class="- topic/entry "> Als het doelbestand al bestaat, kunt u het overschrijven zonder dat u hierom wordt gevraagd. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-policy policy-num</span> </td> 
   <td colname="2" class="- topic/entry "> <p>Als de metagegevens meerdere DRM-beleidsregels bevatten, kunt u het aantal DRM-beleidsregels opgeven dat u kunt gebruiken om een licentie te genereren. </p> <p>Als u het aantal DRM-beleidsregels niet opgeeft, wordt het eerste DRM-beleid automatisch toegepast. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-r ontvanger-cert</span> </td> 
   <td colname="2" class="- topic/entry ">Genereert een licentie voor een opgegeven ontvanger. U kunt een apparaat of domeincertificaat gebruiken, en u kunt veelvoudige <span class="+ topic/ph pr-d/codeph codeph"> - of </span>opties specificeren om een vergunning voor veelvoudige ontvangers tot stand te brengen. </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-root-root-filename</span> </td> 
   <td colname="2" class="- topic/entry "> Hiermee genereert u een hoofdlicentie en slaat u de uitvoer op in een bestand dat u opgeeft. </td> 
  </tr> 
 </tbody> 
</table>

## Eigenschappen van configuratiebestand {#configuration-file-properties}

Voordat u de licentiegenerator uitvoert, moet u waarden voor de eigenschappen van de licentiegenerator opgeven in het configuratiebestand.

>[!NOTE]
>
>Voor eigenschapsnamen die *n* omvatten, *n* vertegenwoordigt een geheel dat met 1 begint en voor elke instantie van het bezit stijgt.

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
   <td colname="2" class="- topic/entry "> <p>Hiermee stelt u de minimaal ondersteunde clientversie in. Als u deze eigenschap niet instelt, worden standaard alle versies automatisch ondersteund. </p> <p>U kunt deze waarde instellen om te bepalen hoe oudere clients reageren op de licentievereisten die ze niet ondersteunen. Geef <span class="codeph"> x</span> (voor Adobe Primetime DRM x.0) op waarbij <span class="codeph"> x</span> een primair releasenummer vertegenwoordigt. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licensegen.keyServerCert</span> </td> 
   <td colname="2" class="- topic/entry "> Het Zeer belangrijke Certificaat van de Server, dat een Adobe-uitgegeven certificaat van de Server van de Vergunning is dat door de Zeer belangrijke Server wordt gebruikt. Dit certificaat wordt alleen toegepast als het beleid voor metagegevens/DRM aangeeft dat een sleutelserver vereist is voor de levering van sleutels aan iOS-apparaten. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licensegen.sign.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> Het PKCS12-bestand met de referenties van de licentieserver voor het ondertekenen van licenties. Deze eigenschap moet verwijzen naar een .pfx-bestand dat een certificaat en een persoonlijke sleutel bevat. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licensegen.sign.certpass</span> </td> 
   <td colname="2" class="- topic/entry ">Het wachtwoord dat het dossier beschermt dat u met <span class="+ topic/ph pr-d/codeph codeph"> licentiegen.sign.certfile</span> optie hebt gespecificeerd. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">licensegen.domainca.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p>Als u domeingebonden vergunningen produceert, moet u één of meerdere certificaten van MAC van het Domein specificeren om op de domeinautoriteiten te wijzen die de vergunningverlener kan vertrouwen. </p> <p>Als de licentieontvanger een domeincertificaat is, dat niet is uitgegeven door een van de opgegeven Domein CA's, kan geen licentie worden gegenereerd. This property specifies a <span class="filepath"> .cer</span> file that includes the certificate in the PEM or the DER format. <span class="codeph">De </span> frequentie moet monotonisch stijgen, te beginnen met 1. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <code>licensegen.keys.asymmetric. licenseServerCredential.n</code>
   </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Optioneel PKCS12-bestand met extra licentieserverreferenties voor het decoderen van de CEK in de metagegevens en het DRM-beleid. U kunt extra geloofsbrieven vormen als de inhoud eerder met een certificaat van de Server van de Vergunning buiten die referentie is verpakt die met <span class="codeph"> licensegen.sign.certfile</span> zijn gespecificeerd. Deze eigenschap moet verwijzen naar een .pfx</span>-bestand <span class="filepath"> dat een certificaat en een persoonlijke sleutel bevat. <span class="codeph">De </span> frequentie moet monotonisch stijgen, te beginnen met 1. </span></p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <code>licensegen.keys.asymmetric. licenseServerCredential.n.password</code>
   </td> 
   <td colname="2" class="- topic/entry "> <p>Het wachtwoord wordt toegepast om het dossier te beschermen dat u met <span class="+ topic/ph pr-d/codeph codeph"> licentiegen.keys.asymmetric.licenseServerCredential.n</span> bezit hebt gespecificeerd. </p> </td> 
  </tr> 
 </tbody> 
</table>