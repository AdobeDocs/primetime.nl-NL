---
seo-title: Eigenschappen van configuratiebestand
title: Eigenschappen van configuratiebestand
uuid: f0d36240-e5fa-4bf9-9a82-7e963d03cdd0
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---


# Eigenschappen van configuratiebestand {#configuration-file-properties}

Voordat u Media Packager uitvoert, geeft u waarden op voor de eigenschappen van Media Packager. In het configuratiebestand worden de volgende eigenschappen opgegeven. Voor eigenschapnamen die* n* bevatten, vertegenwoordigt *n* een geheel getal dat begint met 1 en toeneemt voor elke instantie van de eigenschap.

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
   <td colname="2" class="- topic/entry ">Geeft aan of scriptgegevens in FLV's moeten worden gecodeerd. <i class="+ topic/ph hi-d/i ">Gegevenstags </i> onMetaData en  <i class="+ topic/ph hi-d/i "></i> onXMPscript worden nooit gecodeerd, zelfs niet als deze optie is ingeschakeld. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.video.level</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Geeft het niveau van de videoversleuteling aan. De waarde high wordt gebruikt om alle video-inhoud te coderen, terwijl de waarden medium en low worden gebruikt om gedeelten van de video-inhoud te coderen voor F4V-bestanden die H.264-inhoud bevatten. </p> <p class="- topic/p ">value = <span class="codeph"> high | medium | laag</span> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.secondsUnencrypted</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Als de waarde groter is dan 0, wordt het opgegeven aantal seconden aan het begin van het bestand niet versleuteld. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.asymmetrisch.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Het certificaatbestand van de licentieserver waarmee de sleutel wordt versleuteld. Met de eigenschap <span class="codeph"> encrypt.keys.asymmetrisch.certfile</span> wordt een bestand opgegeven dat alleen het certificaat bevat (PEM- of DER-indeling is acceptabel). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">encrypt.keys.policyFile.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Deze eigenschap wordt herhaaldelijk gebruikt om een lijst met beleidsregels te maken die op de inhoud moeten worden toegepast. <span class="codeph"> </span> nis een geheel getal waarvan de waarde 1 of hoger is. De client gebruikt standaard de eerste instantie. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.serverurl</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De URL van de licentieserver. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.servercert</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Het transportcertificaat voor de licentieserver. This property specifies a <span class="filepath"> .cer</span> file that contains the certificate only (either PEM or DER format is acceptable). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.sign.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Het PKCS12-bestand met de pakketgegevens voor het ondertekenen van inhoud. <span class="codeph"> encrypt.sign.certfile</span> zou naar een <span class="filepath"> .pfx</span> dossier moeten verwijzen die een certificaat en een privé sleutel bevatten. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.sign.certpass</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Het wachtwoord dat wordt gebruikt om het bestand te beveiligen dat wordt opgegeven door <span class="codeph"> encrypt.sign.certfile</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.minServerVersion</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Hiermee stelt u de minimale serverversie in die vereist is voor het uitgeven van licenties voor de inhoud die wordt verpakt. Geef x (Adobe Access x.0) op waarbij x = het hoofdreleasenummer. Servers vóór Adobe Access 3.0 ondersteunen deze instelling niet. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">encrypt.keys.policyFile.n.domain.transportcert</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Als een beleid <span class="+ topic/ph pr-d/codeph codeph"> encrypt.keys.policyFile.n</span> domeinregistratie met een server vereist die een verschillend vervoercertificaat dan gespecificeerd in <span class="+ topic/ph pr-d/codeph codeph"> encrypt.license.server</span> gebruikt, moet het certificaat van het domeinvervoer worden verstrekt. </p> <p class="- topic/p ">This property specifies a file that contains the certificate only (either PEM or DER format is acceptable). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.licenseKey</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Geef een licentiecode op. Als er geen sleutel is opgegeven, wordt de sleutel willekeurig gegenereerd. Wanneer sleutelrotatie niet is ingeschakeld, is dit de sleutel die wordt gebruikt om de inhoud te coderen. </p> <p class="- topic/p ">Wanneer de sleutelomwenteling wordt toegelaten, wordt deze sleutel gebruikt om de omwentelingssleutels te beschermen. De sleutel moet 16 bytes lang zijn en als waarden van de Hexadecimale waarde worden gespecificeerd. Spaties tussen de hexadecimale waarden zijn optioneel. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.rotation.enable</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Geeft aan of toetsrotatie is ingeschakeld. Indien ingesteld op false (standaard), wordt sleutelrotatie uitgeschakeld en wordt de master CEK gebruikt om alle samples in de inhoud te coderen. </p> <p class="- topic/p ">Indien ingesteld op true, wordt het roteren van toetsen ingeschakeld en kunnen verschillende toetsen worden gebruikt om delen van de inhoud te coderen. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">encrypt.keys.rotation.key.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Volgorde van geroteerde sleutels die worden gebruikt om inhoud te coderen wanneer de sleutelomwenteling wordt toegelaten. Als er geen toetsen zijn opgegeven, worden de toetsen willekeurig gegenereerd. De sleutels moeten 16 bytes in lengte zijn en als waarden van de Hexadecimale waarde worden gespecificeerd. </p> <p class="- topic/p ">Spaties tussen de hexadecimale waarden zijn optioneel. <i class="+ topic/ph hi-d/i "></i> Dit mag niet monotonisch toenemen vanaf 1. Wanneer meerdere toetsen worden opgegeven, worden de toetsen doorlopen in de aangegeven volgorde. </p> </td> 
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

