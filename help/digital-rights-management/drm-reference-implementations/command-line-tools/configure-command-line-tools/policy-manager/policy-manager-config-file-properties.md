---
keywords: hard stop
title: Configuratieeigenschappen
description: Configuratieeigenschappen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '1218'
ht-degree: 0%

---


# Configuratieeigenschappen {#configuration-properties}

<!--<a id="section_20A96CDCC5C340DEAF455C6E300E5712"></a>-->

>[!NOTE]
>
>Voor eigenschapnamen die `.n` omvatten, `n` vertegenwoordigt een geheel dat met 1 begint en voor elke instantie van het bezit stijgt. Bijvoorbeeld: `policy.license.customProp.n`.

<table class="+ topic/table " id="table_p3x_54y_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> Optie Eigenschap/opdrachtregel </th> 
   <th colname="2" class="- topic/entry entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.name</span> <p class="- topic/p "><span class="codeph"> -</span> <i class="+ topic/ph hi-d/i ">npolicyName</i> </p> </td> 
   <td colname="2" class="- topic/entry "> De voor mensen leesbare DRM-beleidsnaam. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.requireKeyServer</span> <p class="- topic/p "><span class="codeph"> -</span> <i class="+ topic/ph hi-d/i ">keyServerboolean</i> </p> </td> 
   <td colname="2" class="- topic/entry ">De volgende voorwaarden zijn van toepassing: 
    <ul id="ul_AF4EBD6C19DC4DFAAB4756EF24BAC57D"> 
     <li id="li_6CC48ABF78EC426E9FC51458BD946BC9">Indien waar (true), is een HTTPS Key Server vereist voor sleutellevering aan iOS. </li> 
     <li id="li_63046A4ED7354C1E9E823B475E4AEFF7">Indien niet opgegeven, is de standaardwaarde false. </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.enfordJailbreak</span> <p class="- topic/p "><span class="codeph"> -</span> <i class="+ topic/ph hi-d/i ">enfordJailbreakboolean</i> </p> </td> 
   <td colname="2" class="- topic/entry "> Als de waarde true is, is het voor apparaten die ondersteuning bieden voor jailbreak-detectie niet toegestaan om af te spelen wanneer jailbreak wordt gedetecteerd. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> beleid.kritiek</span> <p class="- topic/p "><span class="codeph"> -</span> <i class="+ topic/ph hi-d/i ">krialboolean</i> </p> </td> 
   <td colname="2" class="- topic/entry ">Hiermee stelt u de kritieke punten van het DRM-beleid in: 
    <ul id="ul_63F1994798894233A67AC4F8220AB642"> 
     <li id="li_D05DD9AD70464D6B9DB9DFF95846E589">Indien waar (true), moet de server alle onderdelen van het DRM-beleid begrijpen, dat het standaardgedrag vertegenwoordigt. </li> 
     <li id="li_0211473DAF1F426787CC4A68F47643C6">Indien onwaar, kan de server DRM beleidsattributen negeren die het niet erkent. </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.chaining.asymmetrisch.certfile</span> </td> 
   <td colname="2" class="- topic/entry ">Certificaat van licentieserver waarvan de openbare sleutel wordt gebruikt voor het versleutelen van de hoofdcoderingssleutel voor <a href="https://help.adobe.com/en_US/primetime/drm/5.3/protecting_content/index.html#DRM-concept-Enhanced_License_Chaining" class="- topic/xref " format="http" scope="external"> Enhanced License Chaining</a>. This property specifies a file that only the certificate. <p>Opmerking:  Zowel PEM- als DER-indelingen worden ondersteund. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.chaining.rootKey</span> <p class="- topic/p "><span class="codeph"> -</span> <i class="+ topic/ph hi-d/i ">rootKeyroot-key</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p>Specificeert de wortelencryptiesleutel voor <a href="https://help.adobe.com/en_US/primetime/drm/5.3/protecting_content/index.html#DRM-concept-Enhanced_License_Chaining" class="- topic/xref " format="http" scope="external"> Verbeterde Vergunning het Ketsen</a>. Als er geen sleutel is opgegeven en uitgebreide licentietekening is ingeschakeld, wordt automatisch een willekeurige sleutel gegenereerd. </p> <p>De sleutel moet 16 bytes lang zijn en als hexwaarden worden gespecificeerd. Whitespace tussen de hexadecimale waarden is optioneel. Voor updates is de opdrachtregeloptie niet beschikbaar en wordt de eigenschap genegeerd. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> beleid.domain.url</span> <p class="- topic/p "><span class="codeph"> -</span> <i class="+ topic/ph hi-d/i ">domainURLurl</i> </p> </td> 
   <td colname="2" class="- topic/entry ">Als domeinregistratie wordt vereist, <i>url</i> specificeert URL van een domeinserver. Voor updates is de opdrachtregeloptie niet beschikbaar en wordt de eigenschap genegeerd. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.domain.anoniem</span> <p class="- topic/p "><span class="codeph"> -domainAnon</span> </p> </td> 
   <td colname="2" class="- topic/entry ">Geeft aan of anonieme domeinregistratie is toegestaan. Plaatst het bezit aan waar of omvat deze bevel-lijn optie om anonieme toegang toe te staan. <p>Opmerking: Deze optie kan niet worden gebruikt met <span class="codeph"> -domainAuthNS</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.domain.autoNamespace</span> <p class="- topic/p "><span class="codeph"> -</span> <i class="+ topic/ph hi-d/i ">domainAuthNSnamespace</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p>De verificatienaamruimte voor domeinregistratie. Indien opgegeven, moet de client worden geverifieerd met een gebruikersnaam en wachtwoord die door de opgegeven instantie zijn uitgegeven. </p> <p>Voor updates is de opdrachtregeloptie niet beschikbaar en wordt de eigenschap genegeerd. </p> <p>Opmerking: Deze optie kan niet worden gebruikt met <span class="codeph"> -domainAnon</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.outputProtection.analog</span> <p class="- topic/p "><span class="codeph"> -</span> <i class="+ topic/ph hi-d/i ">opAnalogAnalogOption</i> </p> </td> 
   <td colname="2" class="- topic/entry ">De analoge beperkingen van de outputbescherming, en de volgende waarden worden gesteund: 
    <ul class="- topic/ul " id="ul_h4x_54y_n4"> 
     <li class="- topic/li " id="li_F920EC01159C4231AFBE579D487C8770"><span class="+ topic/ph pr-d/codeph codeph"> NO_PROTECTION</span> </li> 
     <li class="- topic/li " id="li_2DE0494AF8C446EB9E4567915F5E97C3"><span class="+ topic/ph pr-d/codeph codeph"> USE_IF_AVAILABLE</span> </li> 
     <li class="- topic/li " id="li_207D2D6256D6423FBDABA7A8627A9B7D"><span class="+ topic/ph pr-d/codeph codeph"> USE_IF_AVAILABLE_ACP</span> </li> 
     <li class="- topic/li " id="li_E17D944BED5F403FAE94708EE6AE4BBE"><span class="+ topic/ph pr-d/codeph codeph"> USE_IF_AVAILABLE_CGMSA</span> </li> 
     <li class="- topic/li " id="li_66D5A0C8FE154445A522D91EFB05B7ED"><span class="+ topic/ph pr-d/codeph codeph"> VEREIST</span> </li> 
     <li class="- topic/li " id="li_AF2024F212A249ED99AEECCF3E844A11"><span class="+ topic/ph pr-d/codeph codeph"> REQUIRED_ACP</span> </li> 
     <li class="- topic/li " id="li_FFF9B7DAE77740EE895EC35D1606A527"><span class="+ topic/ph pr-d/codeph codeph"> REQUIRED_CGMSA</span> </li> 
     <li class="- topic/li " id="li_52DED572F3AE495EB6A6450C611B440E"><span class="+ topic/ph pr-d/codeph codeph"> NO_PLAYBACK</span> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.drmVersionBlacklist.n</span> <p class="- topic/p "><span class="codeph"> -</span> <i class="+ topic/ph hi-d/i ">drmBlacklistname/value-pairs</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p>DRM-clients die geen toegang hebben tot beveiligde inhoud. Met deze optie geeft u een lijst op met versies van DRM-modules die niet mogen worden gebruikt (lijst van gewezen personen). </p> <p>De waarde bestaat uit komma's gescheiden <span class="codeph"> naam=value</span> paren in de volgende indeling: </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> os|release|arch|model|leverancier|env|screen=value</span> </p> <p class="- topic/p ">De extra naam/waardeparen moeten komma-gescheiden zijn. Bijvoorbeeld <span class="codeph"> os=Win,release=2.0,arch=32</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.runtimeVersionBlacklist.n</span> <p class="- topic/p "><span class="codeph"> -</span> <i class="+ topic/ph hi-d/i ">runtimeBlacklsitname/value-pairs</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p>Toepassingsruntimes hebben geen toegang tot beveiligde inhoud. Met deze optie geeft u een lijst op met versies van runtimemodules die mogelijk niet worden gebruikt (lijst van gewezen personen). </p> <p>De waarde bestaat uit komma-gescheiden <span class="codeph"> naam=value</span> paren in het volgende formaat: </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> os|release|toepassing|arch|model|leverancier|env|screen=value</span> </p> <p class="- topic/p ">De extra naam/waardeparen moeten komma-gescheiden zijn. Bijvoorbeeld <span class="codeph"> os=Win,application=AIR</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.v1DeviceCapabilities</span> <p class="- topic/p "><span class="codeph"> -devCapabilitiesV1</span> <i class="+ topic/ph hi-d/i ">naam/waarde-paren</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Hiermee geeft u de apparaatmogelijkheden op die vereist zijn voor toegang tot beveiligde inhoud. De waarde bestaat uit komma's gescheiden <span class="codeph"> naam=value</span> paren in de volgende indeling: </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> nonUserAccessibleBus|hardwareRootOfTrust=true|false</span> </p> <p class="- topic/p ">Bijvoorbeeld <span class="codeph"> nonUserAccessibleBus=false,hardwareRootOfTrust=true</span>. </p> <p>Tijdens een update, moet u <span class="codeph"> -devCapabilitiesV1</span> zonder de resterende argumenten toepassen die de beperking van de apparatenmogelijkheden verwijderen. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.syncFrequency</span> <p class="- topic/p "><span class="codeph"> -</span> <i class="+ topic/ph hi-d/i ">syncname/value-pairs</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Geeft aan hoe vaak clients synchronisatieberichten naar de server moeten verzenden. </p> <p>Als het bezit niet wordt geplaatst, zullen de cliënten geen synchronisatieberichten verzenden wanneer zij inhoud spelen die met een beleid DRM wordt beschermd. De waarde bestaat uit komma-gescheiden <span class="codeph"> naam=value</span> paren in het volgende formaat: </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> start|force=numberValue</span> </p> <p class="- topic/p ">De volgende lijst bevat aanvullende informatie over de opties: 
     <ul id="ul_a5j_q4t_44"> 
      <li id="li_FD2C0C6DA19E455AA1917A56E09A7F84">(vereist) <span class="codeph"> start</span> geeft aan dat de client binnen een paar minuten na de laatste synchronisatie moet beginnen met synchroniseren met de server. </li> 
      <li id="li_9DEBC57385A442C3929AE3D0E3FA8992">(optioneel) <span class="codeph"> force</span> is de waarschijnlijkheid (0-100) waarmee de client tijdens het afspelen een synchronisatiebericht moet afdwingen. </li> 
     </ul>Tijdens update, gebruik <span class="codeph"> - sync</span> zonder de resterende argumenten om de synchronisatievereisten te verwijderen. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.useRootLicense</span> </td> 
   <td colname="2" class="- topic/entry ">Geeft aan of dit DRM-beleid een hoofdlicentie heeft. <p>Zie <a href="https://help.adobe.com/en_US/primetime/drm/5.3/protecting_content/index.html#DRM-concept-Enhanced_License_Chaining" class="- topic/xref " format="http" scope="external"> Enhanced License Chaining</a> voor meer informatie. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.startDate</span> </td> 
   <td colname="2" class="- topic/entry ">De datum waarna de inhoud geldig wordt. U kunt een van de volgende indelingen toepassen: 
    <ul id="ul_6610B44D0C16485098F6F45DE3F151D7"> 
     <li id="li_986707D4C6164C44B3CCBE2EEB4C09B6"><span class="+ topic/ph pr-d/codeph codeph">jjjj-mm-dd</span> <p><span class="codeph"> 2009-01-31</span> betekent bijvoorbeeld 31 januari om 12:00 uur. </p> </li> 
     <li id="li_E15B782716124F6EAEFB04D16E5280DB"><span class="+ topic/ph pr-d/codeph codeph">jjjj-mm-dd-h24:min:sec</span> <p><span class="codeph"> 2009-01-31-14:30:00</span> betekent bijvoorbeeld 31 januari om 2:30 uur. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.expiration.endDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De datum voordat de inhoud ongeldig wordt. </p> <p>Opmerking: U kunt <span class="codeph"> policy.expiration.endDate</span> en <span class="codeph"> policy.expiration.duration</span> niet gelijktijdig specificeren. </p> <p>2009-01-31-14:30:00 betekent bijvoorbeeld dat de inhoud op 31 januari om 2:30 uur vervalt. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.expiration.duration</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De tijd in minuten waarin de inhoud ongeldig wordt. De tijd begint wanneer u inhoud verpakt. </p> <p>Opmerking: U kunt <span class="codeph"> policy.expiration.endDate</span> en <span class="codeph"> policy.expiration.duration</span> niet gelijktijdig specificeren. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> beleid.licenseCaching.duration</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De tijd in minuten waarin een licentie in de cache op de client kan worden geplaatst. U kunt deze eigenschap instellen op 0 om te voorkomen dat de licentie in cache wordt geplaatst. De waarde moet 0 of hoger zijn. </p> <p>Opmerking: U kunt <span class="codeph"> policy.licenseCaching.duration</span> en <span class="codeph"> policy.licenseCaching.endDate</span> niet gelijktijdig specificeren. </p> <p class="- topic/p ">Deze DRM-beleidsinstelling wordt alleen toegepast op de licentiecache op de schijf en heeft geen invloed op de licentieduur in de cache. De licentie kan in het geheugen worden opgeslagen, zelfs als u geen DRM-beleid met een duur van nul opgeeft. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.licenseCaching.endDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De datum waarna u licenties niet meer in cache kunt plaatsen. </p> <p>Opmerking: U kunt <span class="codeph"> policy.licenseCaching.duration</span> en <span class="codeph"> policy.licenseCaching.endDate</span> niet gelijktijdig specificeren. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> beleid.anoniem</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Geeft aan of anonieme licentieaanschaf is toegestaan. De standaardwaarde wordt ingesteld op <span class="codeph"> false</span>, wat betekent dat een gebruikersnaam en wachtwoord vereist zijn. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.authNamespace</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Als een gebruikersnaam en wachtwoord vereist zijn, geeft deze eigenschap een optionele naamkwalificatie voor gebruikersnamen op. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">beleid.customProp.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Aangepaste naam-/waardeparen die door de server worden gebruikt tijdens aanschaf van een licentie. U kunt de volgende indeling toepassen om eigenschappen op te geven: <span class="+ topic/ph pr-d/codeph codeph">policy.customProp.n</span>=<span class="+ topic/ph pr-d/codeph codeph">name</span>=<span class="+ topic/ph pr-d/codeph codeph">value</span> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> beleid.playbackWindow  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Geeft het afspeelvenster op in minuten. Deze waarde geeft aan hoe lang de licentie geldig is nadat de beveiligde inhoud voor het eerst is afgespeeld. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> beleid.outputProtection.digital</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Beperkingen op het gebied van uitvoerbescherming, die een van de volgende waarden moeten zijn: 
     <ul id="ul_wsb_kfp_fs"> 
      <li id="li_FE012306F22F4F3FB981FE167C7A8B94"><span class="codeph"> NO_PROTECTION</span> </li> 
      <li id="li_A5591DC8983848FE9823C2A261BF7713"><span class="codeph"> USE_IF_AVAILABLE</span> </li> 
      <li id="li_74102C36ADE841C4B9ED71156E0A4C2C"><span class="codeph"> VEREIST</span> </li> 
      <li id="li_769E15C85B4E4DD48213DBD019D60BA7"><span class="codeph"> NO_PLAYBACK</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.outputProtection.ota</span> </td> 
   <td colname="2" class="- topic/entry ">Geeft de verbindingstypen over de air (OTA) aan die vermeld moeten worden toegestaan. Geldige verbindingstypen zijn: 
    <ul id="ul_iz5_4fp_fs"> 
     <li id="li_FB07519EFEFE4B95B3B1F5BFD4DE6591"><span class="codeph"> MIRACAST</span> </li> 
     <li id="li_51E7DE83679F4630B01264407DAD0E84"><span class="codeph"> LUCHTVAARTUIG</span> </li> 
     <li id="li_D499A0487AAC409CB2CEA6164265D3CF"><span class="codeph"> DLNA</span> </li> 
     <li id="li_4FCC0EC4A0FC48F99A13EC8A1B78D6A1"><span class="codeph"> WIDI</span> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.outputProtection.resolution</span> </td> 
   <td colname="2" class="- topic/entry "> Geeft het configuratiebestand op waarin de op resolutie gebaseerde beperkingen zijn gedefinieerd. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> beleid.drmMinSecurityLevel</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Hiermee geeft u het minimale beveiligingsniveau op waarmee de DRM-module toegang heeft tot beveiligde inhoud. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> beleid.runtimeMinSecurityLevel</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De runtimemodule van de toepassing moet ten minste het opgegeven minimale beveiligingsniveau hebben om toegang te krijgen tot beveiligde inhoud. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.allowedAIRApplication.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Een lijst van gewenste personen van toepassingen die geen Flash zijn (Adobe AIR, iOS, Android, enz.) die beveiligde inhoud mogen afspelen. De eigenschap moet de volgende notatie gebruiken: <span class="+ topic/ph pr-d/codeph codeph">pubId</span>[:<span class="+ topic/ph pr-d/codeph codeph">appId</span>[:[<span class="+ topic/ph pr-d/codeph codeph">min</span>]:[<span class="+ topic/ph pr-d/codeph codeph">max</span>]]] </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.allowedSWFApplication.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Een lijst van gewenste personen van SWF-toepassingen die beveiligde inhoud mogen afspelen. De eigenschap moet de volgende notatie gebruiken: </p> <p class="- topic/p "> 
     <ul id="ul_EC20F52AD95C4BE3B7F703048A43CDF0"> 
      <li id="li_3E4A47D925C24834A2C25BC5943279D4"><span class="+ topic/ph pr-d/codeph codeph">URL</span> </li> 
      <li id="li_9A7CAF081C5F488FB5CDA6D38C5552F6"><span class="+ topic/ph pr-d/codeph codeph">file=swf_file</span> </li> 
      <li id="li_E10EA4223137489CBE4015DE999F7154"><span class="codeph">time=max_time_to_verify</span> </li> 
     </ul> <i class="+ topic/ph hi-d/i ">swf_file </i> is het SWF-bestand dat wordt gebruikt om de hash te berekenen, en  <i class="+ topic/ph hi-d/i ">max_time_to_</i> verify is the maximum time in seconds that is allowed for download and verify the SWF to complete. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.license.customProp.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Aangepaste naam-/waardeparen die u in licenties moet opnemen wanneer de licenties aan gebruikers worden uitgegeven. U moet de volgende indeling opgeven: </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph">policy.license.customProp.n=name</span> </p> <p class="- topic/p ">U kunt deze optie meerdere keren definiëren voor meerdere aangepaste eigenschappen. </p> </td> 
  </tr> 
 </tbody> 
</table>
