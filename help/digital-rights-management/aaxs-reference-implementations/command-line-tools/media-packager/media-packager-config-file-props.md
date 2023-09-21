---
title: Eigenschappen van configuratiebestand
description: Eigenschappen van configuratiebestand
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---

# Eigenschappen van configuratiebestand {#configuration-file-properties}

Voordat u Media Packager uitvoert, geeft u waarden op voor de eigenschappen van Media Packager. In het configuratiebestand worden de volgende eigenschappen opgegeven. Voor eigenschapsnamen die* n* bevatten, *n* vertegenwoordigt een geheel dat met 1 begint en voor elke instantie van het bezit stijgt.

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
   <td colname="2" class="- topic/entry ">Geeft aan of scriptgegevens in FLV's moeten worden gecodeerd. <i class="+ topic/ph hi-d/i ">onMetaData</i> en <i class="+ topic/ph hi-d/i ">onXMP</i> scriptgegevenstags worden nooit gecodeerd, zelfs niet als deze optie is ingeschakeld. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.video.level</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Hiermee wordt het niveau van de videocodering aangegeven. De waarde high wordt gebruikt om alle video-inhoud te coderen, terwijl de waarden medium en low worden gebruikt om gedeelten van de video-inhoud te coderen voor F4V-bestanden die H.264-inhoud bevatten. </p> <p class="- topic/p ">value = <span class="codeph"> hoog | medium | laag</span> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.secondsUnencrypted</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Als de waarde groter is dan 0, wordt het opgegeven aantal seconden aan het begin van het bestand niet versleuteld. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.asymmetrisch.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Het certificaatbestand van de licentieserver waarmee de sleutel wordt versleuteld. De <span class="codeph"> encrypt.keys.asymmetrisch.certfile</span> eigenschap geeft een bestand aan dat alleen het certificaat bevat (PEM- of DER-indeling is acceptabel). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">encrypt.keys.policyFile.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Deze eigenschap wordt herhaaldelijk gebruikt om een lijst met beleidsregels te maken die op de inhoud moeten worden toegepast. <span class="codeph"> n</span> is een geheel getal waarvan de waarde 1 of hoger is. De client gebruikt standaard de eerste instantie. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.serverurl</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De URL van de licentieserver. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.servercert</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Het transportcertificaat voor de licentieserver. This property specifies a <span class="filepath"> .cer</span> bestand dat alleen het certificaat bevat (PEM- of DER-indeling is acceptabel). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.sign.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Het PKCS12-bestand met de gegevens van de verpakker voor het ondertekenen van inhoud. De <span class="codeph"> encrypt.sign.certfile</span> verwijst naar een <span class="filepath"> .pfx</span> bestand met een certificaat en een persoonlijke sleutel. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.sign.certpass</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Het wachtwoord dat wordt gebruikt om het bestand te beveiligen dat is opgegeven door <span class="codeph"> encrypt.sign.certfile</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.minServerVersion</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Hiermee stelt u de minimale serverversie in die vereist is voor het uitgeven van licenties voor de inhoud die wordt verpakt. Geef x (Adobe Access x.0) op waarbij x = het hoofdreleasenummer. Servers vóór Adobe Access 3.0 ondersteunen deze instelling niet. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">encrypt.keys.policyFile.n.domain.transportcert</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Als een beleid <span class="+ topic/ph pr-d/codeph codeph"> encrypt.keys.policyFile.n</span> domeinregistratie is vereist bij een server die een ander transportcertificaat gebruikt dan opgegeven in <span class="+ topic/ph pr-d/codeph codeph"> encrypt.license.servercert</span>, moet het domeinvervoercertificaat worden verstrekt. </p> <p class="- topic/p ">This property specifies a file that contains the certificate only (either PEM or DER format is acceptable). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.licenseKey</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Geef een licentiecode op. Als er geen sleutel is opgegeven, wordt de sleutel willekeurig gegenereerd. Wanneer sleutelrotatie niet is ingeschakeld, is dit de sleutel die wordt gebruikt om de inhoud te coderen. </p> <p class="- topic/p ">Wanneer de sleutelomwenteling wordt toegelaten, wordt deze sleutel gebruikt om de omwentelingssleutels te beschermen. De sleutel moet 16 bytes lang zijn en als waarden van de Hexadecimale waarde worden gespecificeerd. Spaties tussen de hexadecimale waarden zijn optioneel. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.rotation.enable</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Geeft aan of toetsrotatie is ingeschakeld. Indien ingesteld op false (standaard), wordt sleutelrotatie uitgeschakeld en wordt de hoofd-CEK gebruikt om alle samples in de inhoud te coderen. </p> <p class="- topic/p ">Indien ingesteld op true, wordt het roteren van toetsen ingeschakeld en kunnen verschillende toetsen worden gebruikt om delen van de inhoud te coderen. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">encrypt.keys.rotation.key.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Volgorde van geroteerde sleutels die worden gebruikt om inhoud te coderen wanneer de sleutelomwenteling wordt toegelaten. Als er geen toetsen zijn opgegeven, worden de toetsen willekeurig gegenereerd. De sleutels moeten 16 bytes in lengte zijn en als waarden van de Hexadecimale waarde worden gespecificeerd. </p> <p class="- topic/p ">Spaties tussen de hexadecimale waarden zijn optioneel. <i class="+ topic/ph hi-d/i ">n</i> moet monotonisch toenemen, te beginnen met 1. Wanneer meerdere toetsen worden opgegeven, worden de toetsen doorlopen in de aangegeven volgorde. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.rotation.interval</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Hiermee geeft u het interval (in seconden) op waarin een rotatietoets wordt gebruikt voor het versleutelen van inhoudsvoorbeelden. </p> <p class="- topic/p ">Nadat deze hoeveelheid tijd in de inhoud is gecodeerd, wordt de volgende rotatietoets gebruikt. Als de sleutelomwenteling wordt toegelaten en geen interval wordt gespecificeerd, zullen de sleutels om de 15 minuten worden geroteerd. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.serverless</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indien waar (true), is er geen licentieserver waarop de licenties kunnen worden verkregen. Licenties moeten zijn ingesloten of offline zijn verkregen. De standaardwaarde is false als deze niet wordt opgegeven. Alleen ondersteund in Adobe Access Professional. </p> </td> 
  </tr> 
 </tbody> 
</table>
