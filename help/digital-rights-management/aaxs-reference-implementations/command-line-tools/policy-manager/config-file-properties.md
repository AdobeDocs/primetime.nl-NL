---
seo-title: Eigenschappen van configuratiebestand
title: Eigenschappen van configuratiebestand
uuid: aec5fee7-4d77-4299-8d85-3e9042b2bbd1
translation-type: tm+mt
source-git-commit: 99d7eea63b18a97d2b99d0bb7aab5cdc50ae5ffc

---


# Eigenschappen van configuratiebestand {#configuration-file-properties}

In het configuratiebestand worden de volgende eigenschappen opgegeven. Voor eigenschapnamen die `n`deze eigenschap bevatten, `n` staat voor een geheel getal dat begint met 1 en toeneemt voor elke instantie van de eigenschap.

<table class="+ topic/table " id="table_p3x_54y_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> Optie Eigenschap/opdrachtregel </th> 
   <th colname="2" class="- topic/entry entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.name</span> <p class="- topic/p "><span class="codeph"> -n</span> <i class="+ topic/ph hi-d/i ">beleidsnaam</i> </p> </td> 
   <td colname="2" class="- topic/entry "> De voor mensen leesbare beleidsnaam. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.requireKeyServer</span> <p class="- topic/p "><span class="codeph"> -keyServer</span> <i class="+ topic/ph hi-d/i ">boolean</i> </p> </td> 
   <td colname="2" class="- topic/entry "> Indien waar (true), is een HTTPS Key Server vereist voor sleutellevering aan iOS. De standaardwaarde is false (indien niet opgegeven). </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.enfordJailbreak</span> <p class="- topic/p "><span class="codeph"> -enfordJailbreak</span> <i class="+ topic/ph hi-d/i ">boolean</i> </p> </td> 
   <td colname="2" class="- topic/entry "> Indien waar (true), staat u het afspelen niet toe voor apparaten die ondersteuning bieden voor jailbreak-detectie als jailbreak is gedetecteerd. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> beleid.kritiek</span> <p class="- topic/p "><span class="codeph"> -critical</span> <i class="+ topic/ph hi-d/i ">boolean</i> </p> </td> 
   <td colname="2" class="- topic/entry "> Beleidskritiek instellen. Indien waar (true), moet de server alle onderdelen van het beleid begrijpen (dit is het standaardgedrag). Indien onwaar, kan de server beleidsattributen negeren het niet begrijpt. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.chaining.asymmetrisch.certfile</span> </td> 
   <td colname="2" class="- topic/entry ">Certificaat van licentieserver waarvan de openbare sleutel wordt gebruikt om de hoofdcoderingssleutel voor de <a href="../../../aaxs-protecting-content/content-introduction/content-usage-rules/content-other-policy-options/content-enhanced-license-chaining.md" format="dita" scope="local"> Enhanced License Chaining te coderen </a>This property specifies a file that contains the certificate only (either PEM or DER format is acceptable). </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.chaining.rootKey</span> <p class="- topic/p "><span class="codeph"> -rootKey</span> <i class="+ topic/ph hi-d/i ">root-key</i> </p> </td> 
   <td colname="2" class="- topic/entry "> Geef de basiscoderingssleutel voor de uitgebreide licentietekening op. Als er geen sleutel is opgegeven en uitgebreide licentietekening is ingeschakeld, wordt een willekeurige sleutel gegenereerd. De sleutel moet 16 bytes lang zijn en als waarden van de Hexadecimale waarde worden gespecificeerd. Spaties tussen de hexadecimale waarden zijn optioneel. Voor updates is de opdrachtregeloptie niet toegestaan en wordt de eigenschap genegeerd. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> beleid.domain.url</span> <p class="- topic/p "><span class="codeph"> -domainURL</span> <i class="+ topic/ph hi-d/i ">url</i> </p> </td> 
   <td colname="2" class="- topic/entry "> URL van domeinserver, als domeinregistratie wordt vereist. Voor updates is de opdrachtregeloptie niet toegestaan en wordt de eigenschap genegeerd. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.domain.anoniem</span> <p class="- topic/p "><span class="codeph"> -domainAnon</span> </p> </td> 
   <td colname="2" class="- topic/entry "> Geeft aan of anonieme domeinregistratie is toegestaan. Stel de eigenschap in op true of neem deze opdrachtregeloptie op om anonieme toegang toe te staan. Deze optie kan niet worden gebruikt met -domainAuthNS. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.domain.autoNamespace</span> <p class="- topic/p "><span class="codeph"> -domainAuthNS</span> <i class="+ topic/ph hi-d/i ">namespace</i> </p> </td> 
   <td colname="2" class="- topic/entry "> De verificatienaamruimte voor domeinregistratie. Indien opgegeven, moet de client worden geverifieerd met een gebruikersnaam en wachtwoord die door de opgegeven instantie zijn uitgegeven. Voor updates is de opdrachtregeloptie niet toegestaan en wordt de eigenschap genegeerd. Deze optie kan niet worden gebruikt met -domainAnon. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.outputProtection.analog</span> <p class="- topic/p "><span class="codeph"> -opAnalog</span> <i class="+ topic/ph hi-d/i ">AnalogOption</i> </p> </td> 
   <td colname="2" class="- topic/entry ">Restricties op het gebied van analoge uitvoerbescherming. De volgende waarden worden ondersteund: 
    <ul class="- topic/ul " id="ul_h4x_54y_n4"> 
     <li class="- topic/li " id="li_5BC8F39B61894E83A7B27570FF848F09"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> NO_PROTECTION</span> </p> </li> 
     <li class="- topic/li " id="li_FF14594A0714480496793A82C3FA1610"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> USE_IF_AVAILABLE</span> </p> </li> 
     <li class="- topic/li " id="li_721FCC4DC1F34AE398EFAE4C0D3F50F5"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> USE_IF_AVAILABLE_ACP</span> </p> </li> 
     <li class="- topic/li " id="li_D588BB278BEE4CEAB034BD48550EBCDC"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> USE_IF_AVAILABLE_CGMSA</span> </p> </li> 
     <li class="- topic/li " id="li_7E5F006D2F114502BA6D0A9C4173004E"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> VEREIST</span> </p> </li> 
     <li class="- topic/li " id="li_9EBFAA4AACF249C2A94432D88E12C3B9"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> REQUIRED_ACP</span> </p> </li> 
     <li class="- topic/li " id="li_6720C6A085864BEB957C0BF2C38551C9"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> REQUIRED_CGMSA</span> </p> </li> 
     <li class="- topic/li " id="li_6FD98473ECDB4A66AC4B506FB9B3B360"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> NO_PLAYBACK</span> </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.drmVersionBlacklist.n</span> <p class="- topic/p "><span class="codeph"> -drmBlacklist</span> <i class="+ topic/ph hi-d/i ">name/value-pairs</i> </p> </td> 
   <td colname="2" class="- topic/entry ">DRM-clients hebben toegang tot beveiligde inhoud beperkt. Met deze optie geeft u een lijst op met versies van DRM-modules die niet mogen worden gebruikt (zwarte lijst). De waarde bestaat uit door komma's gescheiden naam=waarde paren met de volgende notatie: <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> os|release|arch|model|leverancier|env|screen=value</span> </p> <p class="- topic/p ">De extra naam/waardeparen moeten komma-gescheiden zijn. Bijvoorbeeld: <span class="codeph"> os=Win,release=2.0,arch=32</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.runtimeVersionBlacklist.n</span> <p class="- topic/p "><span class="codeph"> -runtimeBlacklsit</span> <i class="+ topic/ph hi-d/i ">naam/waarde-paren</i> </p> </td> 
   <td colname="2" class="- topic/entry ">Toepassingsruntimes hebben geen toegang tot beveiligde inhoud. Met deze optie geeft u een lijst op met versies van runtimemodules die niet mogen worden gebruikt (zwarte lijst). De waarde bestaat uit door komma's gescheiden naam=waarde paren met de volgende notatie: <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> os|release|toepassing|arch|model|leverancier|env|screen=value</span> </p> <p class="- topic/p ">De extra naam/waardeparen moeten komma-gescheiden zijn. Bijvoorbeeld <span class="codeph"> os=Win,application=AIR</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.v1DeviceCapabilities</span> <p class="- topic/p "><span class="codeph"> -devCapabilitiesV1</span> <i class="+ topic/ph hi-d/i ">naam/waarde-paren</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Geeft de apparaatmogelijkheden aan die vereist zijn voor toegang tot beveiligde inhoud. De waarde bestaat uit door komma's gescheiden naam=waarde paren met de volgende notatie: </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> nonUserAccessibleBus|hardwareRootOfTrust=true|false</span> </p> <p class="- topic/p ">Bijvoorbeeld, <span class="codeph"> nonUserAccessibleBus=false,hardwareRootOfTrust=true</span>. Gebruik tijdens de update <span class="codeph"> -devCapabilitiesV1</span> zonder de resterende argumenten om de beperking van de apparaatmogelijkheden te verwijderen. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.syncFrequency</span> <p class="- topic/p "><span class="codeph"> -sync</span> <i class="+ topic/ph hi-d/i ">naam/waarde-paren</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Geef op hoe vaak clients synchronisatieberichten naar de server moeten verzenden. Als deze optie niet is ingesteld, sturen clients geen synchronisatieberichten wanneer inhoud wordt afgespeeld die met dit beleid is beveiligd. De waarde bestaat uit door komma's gescheiden <span class="codeph"> name=value</span> paren met de volgende notatie: </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> start|force|hardStop=numberValue</span> </p> <p class="- topic/p "> 
     <ul id="ul_a5j_q4t_44"> 
      <li id="li_25CAF96C27F34848A95B2E3693847C71"><span class="codeph"> start</span> (vereist) - Begininterval geeft aan dat de client zoveel minuten na de laatste synchronisatie met de server moet beginnen te synchroniseren. </li> 
      <li id="li_CC9068CFE75645029C947C9E1B53351F"><span class="codeph"> force</span> (optioneel) - De waarschijnlijkheid van synchronisatie forceren is de waarschijnlijkheid (0-100) waarmee de client tijdens het afspelen een synchronisatiebericht moet afdwingen. </li> 
      <li id="li_C31A6250F19348FBB8B7569D00C6314E"><span class="codeph"> hardStop</span> (facultatief) - Het harde eindeinterval is de tijd in notulen waarna de cliënt playback zal ontbreken als niet kan synchroniseren. Indien ingesteld, moet deze groter zijn dan begininterval. </li> 
     </ul>Gebruik tijdens de update <span class="codeph"> -sync</span> zonder de resterende argumenten om de synchronisatievereisten te verwijderen. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.useRootLicense</span> </td> 
   <td colname="2" class="- topic/entry ">Geeft aan of dit beleid een hoofdlicentie heeft (zie <i class="+ topic/ph hi-d/i ">Enhanced License Chaining</i> in <i class="+ topic/ph hi-d/i ">Using Adobe Access for Protecting Content</i>). </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.startDate</span> </td> 
   <td colname="2" class="- topic/entry ">De datum waarna de inhoud geldig is. Gebruik de notatie <span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd</span> (bijvoorbeeld <span class="codeph"> 2009-01-31</span> staat voor 31 januari om 12:00 uur) of <span class="+ topic/ph pr-d/codeph codeph">jjjj-mm-dd-h24:min:sec</span> (bijvoorbeeld <span class="codeph"> 2009-01-31-14:4) 30:00</span> staat voor 31 januari om 2:30 uur). </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.expiration.endDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De datum waarop de inhoud geldig is. Zowel <span class="codeph"> policy.expiration.endDate</span> als policy.expiration.duration kunnen niet gelijktijdig worden gespecificeerd. Gebruik de notatie <span class="+ topic/ph pr-d/codeph codeph">jjjj-mm-dd</span> of <span class="+ topic/ph pr-d/codeph codeph">jjjj-mm-dd-h24:min:sec</span> (bijvoorbeeld 2009-01-31-14:30:00 staat voor 31 januari om 2:30 uur). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.expiration.duration</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De hoeveelheid tijd die de inhoud geldig is (in minuten), vanaf wanneer deze wordt verpakt. Zowel <span class="codeph"> policy.expiration.endDate</span> als <span class="codeph"> policy.expiration.duration</span> kunnen niet tezelfdertijd worden gespecificeerd. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> beleid.licenseCaching.duration</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De tijd dat een licentie in de cache op de client kan worden geplaatst (in minuten). Stel deze eigenschap in op 0 om het in cache plaatsen van licenties niet toe te staan. De waarde moet 0 of hoger zijn. Zowel <span class="codeph"> policy.licenseCaching.duration</span> als <span class="codeph"> policy.licenseCaching.endDate</span> kunnen niet gelijktijdig worden gebruikt. </p> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Opmerking</b>: Deze beleidsinstelling wordt alleen toegepast op de licentiecache op de schijf. De licentieduur van de geheugencache wordt niet geregeld. De licentie kan in het geheugen worden opgeslagen, zelfs als de door het beleid opgegeven duur nul is. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.licenseCaching.endDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De datum waarna de certificaten niet in de cache mogen worden opgeslagen. Zowel <span class="codeph"> policy.licenseCaching.duration</span> als <span class="codeph"> policy.licenseCaching.endDate</span> kunnen niet gelijktijdig worden gebruikt. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> beleid.anoniem</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Geeft aan of anonieme licentieaanschaf is toegestaan. De standaardwaarde is "false" (verificatie van gebruikersnaam en wachtwoord is vereist) als deze niet is opgegeven. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.authNamespace</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Als gebruikersnaam/wachtwoord-verificatie vereist is, geeft deze eigenschap een optionele naamkwalificatie voor gebruikersnamen op. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">beleid.customProp.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Aangepaste naam-/waardeparen die door de server worden gebruikt tijdens aanschaf van een licentie. Gebruik de volgende indeling voor het opgeven van eigenschappen: <span class="+ topic/ph pr-d/codeph codeph">policy.customProp.n</span>=<span class="+ topic/ph pr-d/codeph codeph">name</span>=<span class="+ topic/ph pr-d/codeph codeph">value</span> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> beleid.playbackWindow</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Geeft het afspeelvenster op (in minuten). Dit is de duur waarvoor de licentie geldig is na de eerste keer dat deze wordt gebruikt om beveiligde inhoud af te spelen. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> beleid.outputProtection.digital</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Beperkingen op het gebied van uitvoerbescherming. Waarden moeten een van de volgende waarden zijn: </p> <p class="- topic/p "><i class="+ topic/ph hi-d/i ">NO_PROTECTION, USE_IF_AVAILABLE, REQUIRED, NO_PLAYBACK</i> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> beleid.drmMinSecurityLevel</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De DRM-module moet het opgegeven minimale beveiligingsniveau (of hoger) hebben om toegang te krijgen tot beveiligde inhoud. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> beleid.runtimeMinSecurityLevel</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De runtime-module van de toepassing moet het opgegeven minimale beveiligingsniveau (of hoger) hebben om toegang te krijgen tot beveiligde inhoud. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.allowedAIRApplication.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Een witte lijst met Adobe AIR- of iOS-toepassingen die beveiligde inhoud mogen afspelen. De eigenschap moet de volgende notatie gebruiken: <span class="+ topic/ph pr-d/codeph codeph">pubId</span>[:<span class="+ topic/ph pr-d/codeph codeph">appId</span>[:[<span class="+ topic/ph pr-d/codeph codeph">min</span>]:[<span class="+ topic/ph pr-d/codeph codeph">max</span>]] </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.allowedSWFApplication.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Een witte lijst met SWF-toepassingen die beveiligde inhoud mogen afspelen. Gebruik de volgende indeling: </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph">URL</span> of file=<span class="+ topic/ph pr-d/codeph codeph">swf_file</span>,time=<i class="+ topic/ph hi-d/i ">max_time_to_verify</i> <i class="+ topic/ph hi-d/i ">swf_file</i> is het SWF-bestand waarvoor de hash moet worden berekend en <i class="+ topic/ph hi-d/i ">max_time_to_verify</i> is de maximale tijd die nodig is om het downloaden en de verificatie van het SWF-bestand te voltooien (in seconden). </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.license.customProp.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Aangepaste naam-/waardeparen die moeten worden opgenomen in licenties die aan gebruikers worden verleend. Gebruik de volgende indeling: </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph">policy.license.customProp.n</span>=<span class="+ topic/ph pr-d/codeph codeph">name</span>=<span class="+ topic/ph pr-d/codeph codeph">value</span> </p> <p class="- topic/p ">Deze optie kan meerdere keren worden gedefinieerd voor meerdere aangepaste eigenschappen. </p> </td> 
  </tr> 
 </tbody> 
</table>

