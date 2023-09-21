---
title: Gebruik van de opdrachtregel voor beleidsbeheer
description: Gebruik van de opdrachtregel voor beleidsbeheer
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1223'
ht-degree: 0%

---

# Gebruik van de opdrachtregel voor beleidsbeheer {#policy-manager-command-line-usage}

```
java -jar AdobePolicyManager.jar  
<i class="+ topic ph hi-d="" i "="">
  command filename [options] 
</i class="+ topic>
```

**Tabel 1: opdrachten**

| Opdracht | Beschrijving |
|---|---|
| `new` | Maakt een nieuw DRM-beleid |
| `detail` | Beschrijft een bestaand beleid DRM |
| `update` | Een bestaand DRM-beleid bijwerken |

**Tabel 2: Opties**

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_q5h_cpy_n4">  
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Optie voor opdrachtregel </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Beschrijving </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -c configfile </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Hier geeft u de naam en locatie op van het configuratiebestand. </p> <p class="- topic/p ">Als u geen naam of locatie opgeeft, zoekt DRM Policy Manager naar <span class="filepath"> flashaccessstools.properties </span> in de huidige werkmap. </p> <p>Opmerking: de opties die u op de opdrachtregel opgeeft, hebben voorrang op de opties die u in het configuratiebestand opgeeft. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Als het doelbestand bestaat, kunt u het bestand overschrijven zonder dat u hierom wordt gevraagd. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -noprompt </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Vraag niet of het doelbestand moet worden overschreven. Als het doelbestand bestaat en <span class="codeph"> -o </span> niet is ingesteld, treedt een fout op. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -root </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Geeft aan dat het DRM-beleid een hoofdlicentie heeft. </p> <p class="- topic/p ">Deze optie is niet beschikbaar voor updates. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -e-datum </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De datum voordat de licenties geldig worden. </p> <p>U kunt de datum opgeven in <span class="+ topic/ph pr-d/codeph codeph"> jjjj-mm-dd </span> of <span class="+ topic/ph pr-d/codeph codeph"> jjjj-mm-dd-h24:min:sec </span> gebruiken. Bijvoorbeeld 2008-12-1 of 2008-12-1-00:00:00 voor middernacht op 1 december 2008. </p> <p> 
     <ul id="ul_D5DB5044756D4BD6A734813971598425"> 
      <li id="li_B6BD62A524384060A9DDA14FF50936FA">De waarde moet groter zijn dan de waarde van <span class="codeph"> -s </span> indien aanwezig. </li> 
      <li id="li_C3C5AD0231A240EC9AC57685B9206E8D">U kunt deze optie niet toepassen met <span class="codeph"> -r </span>. </li> 
      <li id="li_3790E2F829A149979BF44E0914CFF431">Als u de einddatum wilt verwijderen wanneer u een DRM-beleid bijwerkt, past u <span class="codeph"> -e </span> zonder een datum op te geven. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -r minuten </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De duur in minuten dat de beveiligde inhoud geldig is. </p> <p class="- topic/p ">Het DRM-beleid wordt geldig wanneer de inhoud wordt beveiligd met de verpakker. </p> <p> 
     <ul id="ul_4690A0E4677A4DF6A006B7FCBD46F1BE"> 
      <li id="li_D1F098D44B494EE7A8647C0B62D5ACFA">De waarde moet niet-negatief zijn. </li> 
      <li id="li_ADFDCB01EEE04B37AFA42886AAEF47EB">U kunt deze optie niet toepassen samen met <span class="codeph"> -e </span>. </li> 
      <li id="li_E80563E68BEB43FC9E29A694594CAE01">Als u de duur wilt verwijderen of verwijderen wanneer u een DRM-beleid bijwerkt, past u <span class="codeph"> -r </span> zonder minuten op te geven. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -s date </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De datum waarop de vergunningen geldig worden. </p> <p>U kunt de datum opgeven in het dialoogvenster <span class="+ topic/ph pr-d/codeph codeph"> jjjj-mm-dd </span> of <span class="+ topic/ph pr-d/codeph codeph"> jjjj-mm-dd-h24:min:sec </span> gebruiken. Bijvoorbeeld: <span class="codeph"> 2008-12-1 </span> of <span class="codeph"> 2008-12-1-00:00:00 </span> voor middernacht op 1 december 2008. </p> <p> 
     <ul id="ul_D52B337F547F4E7AB87FE025236CA930"> 
      <li id="li_DBAE380972434DB1A4EF20D399038AB8">De waarde moet kleiner zijn dan de waarde van <span class="codeph"> -e </span>, indien aanwezig. </li> 
      <li id="li_2899EC5559CF44319A4AC4ECD90A5B9A">U kunt deze optie niet toepassen samen met <span class="codeph"> -r </span>. </li> 
      <li id="li_19861B1A64E44B95B649948EAB3E4085">Als u de begindatum wilt verwijderen wanneer u een DRM-beleid bijwerkt, gebruikt u <span class="codeph"> -s </span> zonder een datum op te geven. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -w [&lt;minutes&gt;[,enableHS|disableHS]] </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Het afspeelvenster is het aantal minuten dat de inhoud kan worden weergegeven vanaf het eerste afspelen. </p> <p>Indien niet gespecificeerd, of indien <span class="codeph"> -w </span> wordt gebruikt zonder een aantal minuten op te geven, is er geen beperking voor het afspeelvenster. De waarde moet niet-negatief zijn. </p> <p>De optionele <span class="codeph"> enableHS </span> of <span class="codeph"> disableHS </span> de vlagsignalen of om harde stop toe te laten of onbruikbaar te maken. De markering geeft aan of de decoderingscontext aan het einde van het afspeelvenster (ingeschakeld) is verwijderd of niet (uitgeschakeld). </p> <p>Als u bijvoorbeeld wilt opgeven dat de inhoud alleen gedurende 60 minuten mag worden weergegeven en een vaste stop vereist: 
     <codeblock>
       -w&amp;nbsp;60,enableHS 
     </codeblock> </p> <p>Opmerking:  <i>Harde stop</i> wordt momenteel niet ondersteund in Flash Player, Android en iOS. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -l minuten </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De duur van het in cache plaatsen van licenties is de tijd in minuten dat een licentie in de Licentieopslag van de client kan worden opgeslagen nadat de licentie door de server is uitgegeven. De waarde moet niet-negatief zijn. </p> <p>U kunt <span class="codeph"> -l 0 </span> om aan te geven dat het in cache plaatsen van licenties niet is toegestaan. Geef voor een onbeperkte licentiecache <span class="codeph"> -l </span> zonder minuten. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -ldate </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De einddatum van de licentiecache. </p> <p class="- topic/p ">Dit geeft de einddatum aan waarop de client licenties in de licentiesector van de client in cache kan plaatsen nadat de Primetime DRM-server de licentie heeft uitgegeven. </p> <p>U kunt de datum in de volgende notaties opgeven: 
     <ul id="ul_112DE7248A9C48B19520A3AA9E5D1F03"> 
      <li id="li_01C5400E78B84A3B8955972FBA875AAC"> <span class="+ topic/ph pr-d/codeph codeph"> jjjj-mm-dd </span> </li> 
      <li id="li_AA13B1EFA07A4542A3DB41FA3320B143"> <span class="+ topic/ph pr-d/codeph codeph"> jjjj-mm-dd-h24:min:sec </span> </li> 
     </ul>Bijvoorbeeld: <span class="codeph"> 2008-12-1 </span> of <span class="codeph"> 2008-12-1-00:00:00 </span> voor middernacht op 1 december 2008. U moet deze toepassing toepassen <span class="codeph"> -l </span> zonder minuten op te geven voor het in cache plaatsen van een onbeperkte licentie. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -authNS </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De verificatienaamruimte. </p> <p class="- topic/p ">Als u deze optie toepast, moet de client een gebruikersnaam en wachtwoord invoeren die door de opgegeven instantie zijn uitgegeven. </p> <p>U kunt deze optie niet toepassen samen met <span class="codeph"> -x </span>. </p> <p>Deze optie is niet toegestaan voor updates. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -x </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Anonieme toegang toestaan. </p> <p class="- topic/p ">U kunt deze optie niet toepassen samen met <span class="codeph"> -authNS </span>. </p> <p class="- topic/p ">Deze optie is niet toegestaan voor updates. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -air pubId </span>[: <span class="+ topic/ph pr-d/codeph codeph"> appId </span>[:[ <span class="+ topic/ph pr-d/codeph codeph"> min </span>]:[ <span class="+ topic/ph pr-d/codeph codeph"> max </span>]] </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Een lijst van gewenste personen van AIR-toepassingen die beveiligde inhoud kunnen afspelen. </p> <p class="- topic/p ">U kunt deze optie toepassen om te beperken welke uitgevers, toepassingen, en versies tot de inhoud kunnen toegang hebben die met dit beleid DRM wordt beschermd. </p> <p class="- topic/p ">Als u geen <i class="+ topic/ph hi-d/i ">appId</i>, alle toepassingen voor de uitgever <i class="+ topic/ph hi-d/i ">pubId</i> zijn toegestaan. </p> <p>Opmerking:  <i class="+ topic/ph hi-d/i ">min</i> en <i class="+ topic/ph hi-d/i ">max</i> versienummers zijn optioneel. </p> <p class="- topic/p ">U kunt meerdere <span class="codeph"> -air </span> opties om meerdere toepassingen toe te staan. Als u geen AIR- of SWF-toepassing opgeeft, hebben alle toepassingen toegang tot deze inhoud. Tijdens een update kunt u alle items uit de lijst verwijderen of verwijderen door op <span class="codeph"> -air </span> zonder de overige argumenten . </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -drmBlacklist-naam </span> <i class="+ topic/ph hi-d/i ">/</i> <span class="+ topic/ph pr-d/codeph codeph"> value </span> <i class="+ topic/ph hi-d/i "> </i> <span class="+ topic/ph pr-d/codeph codeph"> paren </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De DRM-clients die geen toegang hebben tot beveiligde inhoud. </p> <p class="- topic/p ">De waarde ondersteunt door komma's gescheiden naam:waardeparen in de volgende indeling: </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> os | release= stringValue </span> </p> <p class="- topic/p ">Bijvoorbeeld: <span class="codeph"> os=Win,release=2.0.1 </span>. Tijdens een update kunt u alle items uit de lijst verwijderen door op <span class="codeph"> -drmBlacklist </span> zonder de overige argumenten. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -drmLevel int </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Geeft aan dat DRM-clients een toegewezen minimumbeveiligingsniveau moeten hebben om toegang tot beveiligde inhoud te krijgen. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -opAnalog NO_PROTECTION | USE_IF_AVAILABLE | VEREIST | NO_PLAYBACK | REQUIRED_ACP | REQUIRED_CGMSA | USE_IF_AVAILABLE_ACP | USE_IF_AVAILABLE_CGMSA </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Restricties voor analoge uitvoerbescherming </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -opDigital NO_PROTECTION | USE_IF_AVAILABLE | VEREIST | NO_PLAYBACK </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Beperkingen op het gebied van bescherming van digitale uitvoer </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -runtimeBlacklist-naam </span> <i class="+ topic/ph hi-d/i ">/</i> <span class="+ topic/ph pr-d/codeph codeph"> value </span> <i class="+ topic/ph hi-d/i "> </i> <span class="+ topic/ph pr-d/codeph codeph"> paren </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De runtimes van de toepassing die geen toegang hebben tot beveiligde inhoud. </p> <p class="- topic/p ">De waarde ondersteunt door komma's gescheiden namen:waardeparen in de volgende notatie: </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> os | Aanvraag | release= stringValue </span> </p> <p class="- topic/p ">Bijvoorbeeld: <span class="codeph"> os=Win,release=2.0.1,toepassing=AIR </span>. Tijdens een update kunt u alle items uit de lijst verwijderen door op <span class="codeph"> -runtimeBlacklist </span> zonder de overige argumenten . </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -runtimeLevel int </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Geeft aan dat de runtimes van de toepassing een opgegeven minimumbeveiligingsniveau moeten hebben om toegang te krijgen tot beveiligde inhoud. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -swf url </span> </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -swf file= swf_file </span>, <span class="+ topic/ph pr-d/codeph codeph"> time= max_time_to_verify </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Een lijst van gewenste personen van SWF-toepassingen die beveiligde inhoud mogen afspelen. </p> <p class="- topic/p ">U kunt meerdere <span class="codeph"> -swf </span> opties om meerdere toepassingen toe te staan. Als u geen AIR- of SWF-toepassingen opgeeft, hebben alle toepassingen toegang tot deze inhoud. </p> <p>Tijdens een update kunt u alle items uit de lijst verwijderen door op <span class="codeph"> -swf </span> zonder de overige argumenten . Als u een SWF door zijn knoeiboelwaarde wilt identificeren, moet u het dossier van de SWF specificeren waarvoor om de knoeiboel te berekenen en de maximumtijd om voor de controle van de SWF toe te staan om te voltooien (in seconden). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -k name= value </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Hier geeft u de aangepaste sleutel of waarden op die u aan een DRM-beleid wilt toevoegen. </p> <p class="- topic/p ">U kunt meerdere <span class="codeph"> -k </span> opties. Tijdens de update kunt u <span class="codeph"> -k </span> zonder de resterende argumenten als u alle eigenschappen wilt verwijderen. De interpretatie of verwerking van de gegevens wordt beheerd door de Primetime DRM-licentieserver. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -p name= value </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Voegt een aangepaste eigenschap toe die wordt weergegeven in de licentie die voor elke client wordt gegenereerd. </p> <p class="- topic/p ">U kunt meerdere <span class="codeph"> -p </span> opties om meerdere eigenschappen toe te voegen. Tijdens een update moet u deze toepassen <span class="codeph"> -p </span> zonder de resterende argumenten als u alle eigenschappen wilt verwijderen. De interpretatie of verwerking van deze gegevens wordt beheerd door de implementatie van de clienttoepassing. </p> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> <span class="codeph"> -opOTA whitelist=&lt;connection types=""&gt; </span> </span> </td> 
   <td colname="2" class="- topic/entry "> Over de beperkingen van de bescherming van de luchtoutput (OTA). De <span class="codeph"> whitelist </span> veld geeft aan welke verbindingstypen voor lijst van gewenste personen worden gebruikt en welke notatie &lt;connection types=""&gt; is <span class="codeph"> [type(,type)*] </span>, waarbij het type een van de volgende items kan zijn: MIRACAST, AIRPLAY, WIDI, DLNA </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -opResolution &lt;filename&gt; </span> </td> 
   <td colname="2" class="- topic/entry "> <p>Op resolutie gebaseerde beperkingen van de outputbescherming zoals die in het gespecificeerde dossier worden bepaald. </p> <p>De codering van dit bestand is JSON. De grammatica voor de opmaak vindt u in <i>Informatie over op resolutie gebaseerde uitvoerbeveiliging</i>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Voorbeelden**

Om een beleid tot stand te brengen dat anonieme toegang tot uw inhoud toestaat, gebruikend uw eigen dossier van configuratieeigenschappen:

```
java -jar libs\AdobePolicyManager.jar new policy_test.pol -x -c my_configuration.properties
```
