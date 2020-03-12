---
description: 'null'
seo-description: 'null'
seo-title: Overzicht
title: Overzicht
uuid: f4474837-9460-479d-89c2-dd697e0fb997
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc

---


# DRM Media Packager {#media-packager}

Gebruik Media Packager ( [!DNL AdobePackager.jar]) om een DRM-beleid op te geven dat op uw inhoud moet worden toegepast en om op te geven welk deel van de inhoud moet worden gecodeerd. U kunt bijvoorbeeld opgeven dat de videogegevens moeten worden gecodeerd door de pakketsoftware, maar niet door de audiogegevens.

Voordat u gaat werken [!DNL AdobePackager.jar], moet u eigenschappen instellen in het gedeelte Eigenschappen van Media Packager van het configuratiebestand.

>[!NOTE]
>
>U kunt ook alle eigenschappen van Media Packager opgeven via de opdrachtregel.

## Gebruik van de opdrachtregel van Media Packager {#media-packager-command-line-usage}

**Eén bestand verpakken:**

```
java -jar AdobePackager.jar  
<i class="+ topic ph hi-d="" i "="">
  source  
 <i class="+ topic ph hi-d="" i "="">
   dest [ 
  <i class="+ topic ph hi-d="" i "="">
    options] 
  </i class="+ topic> 
 </i class="+ topic> 
</i class="+ topic>
```

* `source` - De naam van het bestand dat u wilt versleutelen.
* `dest` - De naam van het resulterende gecodeerde bestand.

   Als u een map opgeeft, wordt het gecodeerde bestand automatisch opgeslagen in de opgegeven map met dezelfde bestandsnaam als het bronbestand. U kunt echter geen doelmap opgeven die het bronbestand bevat.

**Meerdere bestanden met dezelfde sleutel** verpakken (voor ondersteuning van meerdere bitsnelheden):

```
java -jar AdobePackager.jar  
<i class="+ topic ph hi-d="" i "="">
  sourcefiles  
 <i class="+ topic ph hi-d="" i "="">
   dest-directory [ 
  <i class="+ topic ph hi-d="" i "="">
    options] 
  </i class="+ topic> 
 </i class="+ topic> 
</i class="+ topic>
```

* `sourcefiles` - Een reeks bronitems met als scheidingsteken een witruimte voor de bestanden die u wilt versleutelen.
* `dest-directory` - De doelmap waarin u gecodeerde inhoud wilt schrijven. De gecodeerde bestanden worden automatisch in deze map opgeslagen met dezelfde bestandsnamen als de bronbestanden. De doelmap mag echter geen bronbestanden bevatten.

**Informatie weergeven over een versleuteld bestand:**

```
java -jar AdobePackager.jar -d  
<i class="+ topic ph hi-d="" i "="">
  encryptedfile [-e] [-m] 
</i class="+ topic>
```

**Informatie weergeven over een metagegevensbestand:**

```
java -jar AdobePackager.jar -dm <metadatafile> [-e]
```

* `metadatafile` is een [!DNL .metadata] bestand dat DRM-metagegevens bevat.

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>Tijdens het verpakken, kan Media Packager niet meer een [!DNL .header] dossier door gebrek produceren. Als u een [!DNL .header] bestand wilt genereren, gebruikt u de `-h` optie tijdens het verpakken.

**Tabel 3: Opties**

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_wgz_spy_n4">  
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Optie voor opdrachtregel </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Beschrijving </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-c <span class="+ topic/ph pr-d/codeph codeph"> configfile </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Hier geeft u de naam en locatie op van het configuratiebestand. </p> <p class="- topic/p ">Als u geen naam of locatie opgeeft, zoekt DRM Media Packager naar <span class="filepath"> flashaccessTools.properties </span> in de huidige werkmap. </p> <p>Opmerking:  Opties die u op de opdrachtregel opgeeft, hebben voorrang op de opties die u in het configuratiebestand opgeeft. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-d <span class="+ topic/ph pr-d/codeph codeph"> versleuteld bestand </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Hiermee kunt u informatie weergeven over een bestand dat al is verpakt. </p> <p class="- topic/p ">De bron- en doelbestanden zijn niet vereist. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-dm <span class="+ topic/ph pr-d/codeph codeph"> metadatafile </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Hiermee kunt u informatie over bestaande metagegevens weergeven. </p> <p class="- topic/p ">De bron- en doelbestanden zijn niet vereist. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-e </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Extraheert DRM-beleid uit een pakketbestand wanneer u deze optie in combinatie met de <span class="codeph"> -d- </span> optie toepast. </p> <p class="- topic/p ">Er wordt automatisch een bestand gemaakt in dezelfde map als waarin het gecodeerde bestand zich bevindt, met een bestandsnaam en DRM-beleidsidentificatie. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-h </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Extraheert de DRM-header uit een pakketbestand wanneer u deze optie samen met de <span class="codeph"> -d- </span> optie toepast. </p> <p class="- topic/p ">Er wordt automatisch een bestand gemaakt in dezelfde map als waarin het gecodeerde bestand zich bevindt met de bestandsnaam en de extensie <span class="filepath"> .header </span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-i <span class="+ topic/ph pr-d/codeph codeph"> contentID </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Hiermee geeft u een unieke id op voor dit inhoudssegment. </p> <p class="- topic/p ">Als u geen id opgeeft, wordt de bestandsnaam van het doelbestand automatisch toegepast. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-k <span class="+ topic/ph pr-d/codeph codeph"> key </span>= <span class="+ topic/ph pr-d/codeph codeph"> value </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Geeft een aangepaste sleutel/waarde op die aan de metagegevens van de inhoud moet worden toegevoegd. </p> <p class="- topic/p ">U kunt meerdere <span class="codeph"> -k- </span> opties opgeven. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-m </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Metagegevens uit een pakketbestand extraheren wanneer u deze optie samen met de <span class="codeph"> -d- </span> optie toepast. </p> <p class="- topic/p ">Er wordt automatisch een bestand gemaakt in dezelfde map als het gecodeerde bestand met een bestandsnaam en de extensie <span class="codeph"> .metadata </span> . </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-noprompt </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Vraag niet of het doelbestand moet worden overschreven. </p> <p class="- topic/p ">Als het doelbestand al bestaat en <span class="codeph"> -o </span> niet is ingesteld, treedt een fout op. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-o </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Hiermee overschrijft u het doelbestand zonder dat u hierom wordt gevraagd, tenzij het al bestaat. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-p <span class="+ topic/ph pr-d/codeph codeph"> bestandsnaam [domain-transport-cert] </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Hier geeft u de naam op van het bestand dat het DRM-beleid bevat. </p> <p class="- topic/p ">Als voor het DRM-beleid domeinregistratie is vereist bij een server die een ander transportcertificaat gebruikt dan het certificaat dat u in het eigenschappenbestand hebt opgegeven, moet u het certificaat voor het domeinvervoer opgeven. </p> <p class="- topic/p ">U kunt meerdere <span class="codeph"> -p- </span> opties opgeven. De client past standaard de eerste optie toe. De waarden die u op de bevellijn hebt gespecificeerd nemen belangrijkheid over die die u in het configuratiedossier hebt gespecificeerd. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Configuratieeigenschappen {#configuration-properties}

<!--<a id="section_3081C60BE54D47569FD1E3793513A2D9"></a>-->

>[!NOTE]
>
>Voor eigenschapsnamen die* n* bevatten, vertegenwoordigt *n* een geheel getal dat begint met 1 en wordt verhoogd voor elke instantie van de eigenschap.

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_dx4_mpy_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Eigenschap </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Beschrijving </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.video</span> </td> 
   <td colname="2" class="- topic/entry "> Geeft aan of video-inhoud moet worden gecodeerd. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.audio</span> </td> 
   <td colname="2" class="- topic/entry "> Geeft aan of audio moet worden gecodeerd. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.script</span> </td> 
   <td colname="2" class="- topic/entry "> <p>Geeft aan of scriptgegevens in mp4s moeten worden gecodeerd. </p> <p><i class="+ topic/ph hi-d/i ">onMetaData</i> - en <i class="+ topic/ph hi-d/i ">onXMP</i> -scripttags worden nooit gecodeerd, zelfs niet als u deze optie inschakelt. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.video.level</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Geeft het niveau van de videoversleuteling aan. </p> <p class="- topic/p ">De waarde <span class="codeph"> high</span> wordt gebruikt om alle video-inhoud te coderen, terwijl de waarden <span class="codeph"> medium</span> en <span class="codeph"> low</span> worden gebruikt om delen van de video-inhoud te coderen voor MP4-bestanden die H.264-inhoud bevatten. </p> <p class="- topic/p ">value = <span class="codeph"> high| medium| laag</span> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.secondsUnencrypted</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Als een waarde groter is dan 0, wordt het opgegeven aantal seconden aan het begin van het bestand niet versleuteld. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.asymmetrisch.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Het certificaatbestand van de licentieserver waarmee de sleutel wordt versleuteld. </p> <p class="- topic/p ">Met de eigenschap <span class="codeph"> encrypt.keys.asymmetrisch.certfile</span> wordt een bestand opgegeven dat alleen het certificaat bevat (de indeling PEM of DER is acceptabel). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">encrypt.keys.policyFile.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Deze eigenschap wordt herhaaldelijk gebruikt om een lijst met DRM-beleidsregels te maken die op de inhoud moeten worden toegepast. <span class="codeph"> n</span> staat voor een geheel getal waarvan de waarde 1 of hoger is. De client gebruikt standaard de eerste instantie. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.serverurl</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De licentieserver-URL </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.servercert</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Het transportcertificaat voor de licentieserver. </p> <p class="- topic/p ">This property specifies a <span class="filepath"> .cer</span> file that includes the certificate only (either PEM or DER format is acceptable). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.sign.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Het PKCS12-bestand met de gegevens van de verpakker voor het ondertekenen van inhoud. </p> <p class="- topic/p ">Het bestand <span class="codeph"> encrypt.sign.certfile</span> moet verwijzen naar een <span class="filepath"> .pfx</span> -bestand dat een certificaat en een persoonlijke sleutel bevat. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.sign.certpass</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Het wachtwoord dat u kunt toepassen om het bestand te beveiligen dat is opgegeven door <span class="codeph"> encrypt.sign.certfile</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.minServerVersion</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Hiermee stelt u de minimale serverversie in die vereist is voor het afgeven van licenties voor de inhoud die wordt verpakt. </p> <p class="- topic/p ">Geef x (voor Primetime DRM x.0) op waarbij x een hoofdreleasenummer vertegenwoordigt. Deze instelling wordt niet ondersteund door versies van servers die voorafgaan aan Adobe Primetime versie 3.0. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">encrypt.keys.policyFile.n.domain.transportcert </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Als een DRM-beleid <span class="+ topic/ph pr-d/codeph codeph"> encrypt.keys.policyFile.n</span> domeinregistratie vereist met een server die een ander transportcertificaat ondersteunt dan het certificaat dat u in <span class="+ topic/ph pr-d/codeph codeph"> encrypt.license.servercert</span>hebt opgegeven, moet u de certificaatbehoeften voor het domeinvervoer opgeven. </p> <p class="- topic/p ">This property specifies a file that includes the certificate only (either PEM or DER format is acceptable). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.licenseKey</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Geeft een licentiecode aan. </p> <p class="- topic/p ">Als u geen sleutel opgeeft, wordt de sleutel willekeurig gegenereerd. Wanneer u sleutelrotatie niet inschakelt, kunt u deze sleutel gebruiken om inhoud te versleutelen. </p> <p class="- topic/p ">Wanneer u sleutelrotatie inschakelt, kunt u deze toets gebruiken om de rotatietoetsen te beveiligen. De sleutel moet 16 bytes lang zijn en als waarden van de Hexadecimale waarde worden gespecificeerd. Spaties tussen de hexadecimale waarden zijn optioneel. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.rotation.enable</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Geeft aan of toetsrotatie is ingeschakeld. </p> <p class="- topic/p ">Indien ingesteld op false (de standaardinstelling), wordt sleutelrotatie uitgeschakeld en wordt de hoofd-CEK gebruikt om alle samples in de inhoud te coderen. </p> <p class="- topic/p ">Indien ingesteld op true, wordt sleutelrotatie ingeschakeld en kunnen verschillende toetsen worden gebruikt om segmenten van elke inhoud te coderen. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">encrypt.keys.rotation.key.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Volgorde van geroteerde sleutels die u kunt opgeven om inhoud te coderen wanneer sleutelrotatie is ingeschakeld. </p> <p class="- topic/p ">Als u geen toetsen opgeeft, worden de toetsen willekeurig gegenereerd. De sleutels moeten 16 bytes in lengte zijn en als waarden van de Hexadecimale waarde worden gespecificeerd. </p> <p class="- topic/p ">Spaties tussen de hexadecimale waarden zijn optioneel. <i class="+ topic/ph hi-d/i ">n</i> moet monotonisch toenemen, beginnend bij 1. Wanneer u meerdere toetsen opgeeft, worden de toetsen doorlopen in de volgorde die u hebt aangegeven. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.rotation.interval</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Hiermee geeft u het tijdsinterval in seconden op waarin u een rotatiesleutel kunt toepassen om inhoudsvoorbeelden te coderen. </p> <p class="- topic/p ">Nadat het tijdsinterval is verstreken waarin de inhoud is gecodeerd, wordt de volgende rotatietoets toegepast. Als u sleutelrotatie hebt ingeschakeld maar geen tijdsinterval hebt opgegeven, worden de toetsen automatisch om de 15 minuten geroteerd. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.serverless</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Als deze optie is ingesteld op true, is er geen licentieserver beschikbaar waarop licenties kunnen worden verkregen. </p> <p class="- topic/p ">Licenties moeten zijn ingesloten of offline zijn verkregen. De standaardwaarde is ingesteld op false, tenzij u een andere waarde opgeeft. Deze optie wordt alleen ondersteund in Primetime DRM Professional. </p> </td> 
  </tr> 
 </tbody> 
</table>