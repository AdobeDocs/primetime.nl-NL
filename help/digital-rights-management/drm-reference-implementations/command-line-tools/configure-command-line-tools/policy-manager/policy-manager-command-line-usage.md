---
description: 'null'
seo-description: 'null'
seo-title: Het gebruik van de Opdracht van de Manager van het beleid
title: Het gebruik van de Opdracht van de Manager van het beleid
uuid: 9b17bc9a-0b1b-405f-a62b-0310c43c9255
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '1228'
ht-degree: 0%

---


# Het gebruik van de Opdracht van de Manager van het beleid {#policy-manager-command-line-usage}

```
java -jar AdobePolicyManager.jar  
<i class="+ topic ph hi-d="" i "="">
  command filename [options] 
</i class="+ topic>
```

**Tabel 1: Opdrachten**

| Opdracht | Beschrijving |
|---|---|
| `new` | Hiermee wordt een nieuw DRM-beleid gemaakt |
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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Hier geeft u de naam en locatie op van het configuratiebestand. </p> <p class="- topic/p ">Als u geen naam of een plaats specificeert, zoekt de Manager van het Beleid DRM naar <span class="filepath"> flashaccessTools.properties </span> in de huidige het werk folder. </p> <p>Opmerking:  Opties die u op de opdrachtregel opgeeft, hebben voorrang op de opties die u in het configuratiebestand opgeeft. </p> </td> 
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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De datum voordat de licenties geldig worden. </p> <p>U kunt de datum opgeven in de <span class="+ topic/ph pr-d/codeph codeph"> notatie </span> jjjj-mm-dd <span class="+ topic/ph pr-d/codeph codeph"> of </span> jjjj-mm-dd-h24:min:sec. Bijvoorbeeld 2008-12-1 of 2008-12-1-00:00:00 voor middernacht op 1 December 2008. </p> <p> 
     <ul id="ul_D5DB5044756D4BD6A734813971598425"> 
      <li id="li_B6BD62A524384060A9DDA14FF50936FA">De waarde moet groter zijn dan de waarde van <span class="codeph"> -s </span> indien aanwezig. </li> 
      <li id="li_C3C5AD0231A240EC9AC57685B9206E8D">U kunt deze optie niet toepassen met <span class="codeph"> -r </span>. </li> 
      <li id="li_3790E2F829A149979BF44E0914CFF431">Als u de einddatum wilt verwijderen wanneer u een DRM-beleid bijwerkt, past u <span class="codeph"> -e toe </span> zonder een datum op te geven. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -r minuten </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De duur in minuten dat de beveiligde inhoud geldig is. </p> <p class="- topic/p ">Het DRM-beleid wordt geldig wanneer de inhoud wordt beveiligd met de verpakker. </p> <p> 
     <ul id="ul_4690A0E4677A4DF6A006B7FCBD46F1BE"> 
      <li id="li_D1F098D44B494EE7A8647C0B62D5ACFA">De waarde moet niet-negatief zijn. </li> 
      <li id="li_ADFDCB01EEE04B37AFA42886AAEF47EB">U kunt deze optie niet samen met <span class="codeph"> -e toepassen </span>. </li> 
      <li id="li_E80563E68BEB43FC9E29A694594CAE01">Als u de duur wilt verwijderen wanneer u een DRM-beleid bijwerkt, past u <span class="codeph"> -r toe </span> zonder minuten op te geven. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -s date </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De datum waarop de vergunningen geldig worden. </p> <p>U kunt de datum opgeven in de <span class="+ topic/ph pr-d/codeph codeph"> notatie </span> jjjj-mm-dd <span class="+ topic/ph pr-d/codeph codeph"> of </span> jjjj-mm-dd-h24:min:sec. Bijvoorbeeld, <span class="codeph"> 2008-12-1 </span> of <span class="codeph"> 2008-12-1-00:00:00 </span> voor middernacht op 1 December, 2008. </p> <p> 
     <ul id="ul_D52B337F547F4E7AB87FE025236CA930"> 
      <li id="li_DBAE380972434DB1A4EF20D399038AB8">De waarde moet kleiner zijn dan de waarde van <span class="codeph"> -e </span>, indien aanwezig. </li> 
      <li id="li_2899EC5559CF44319A4AC4ECD90A5B9A">U kunt deze optie niet samen met <span class="codeph"> -r </span>toepassen. </li> 
      <li id="li_19861B1A64E44B95B649948EAB3E4085">Als u de begindatum wilt verwijderen wanneer u een DRM-beleid bijwerkt, gebruikt u <span class="codeph"> -s </span> zonder een datum op te geven. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -w [&lt;minutes&gt;[,enableHS|disableHS]] </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Het afspeelvenster is het aantal minuten dat de inhoud kan worden weergegeven vanaf het eerste afspelen. </p> <p>Als deze niet is opgegeven of als <span class="codeph"> -w </span> wordt gebruikt zonder een aantal minuten op te geven, is er geen beperking voor het afspeelvenster. De waarde moet niet-negatief zijn. </p> <p>De optionele <span class="codeph"> schakeltHS- </span> of <span class="codeph"> HS- </span> markeringssignalen in of uit om hardstop in of uit te schakelen. De markering geeft aan of de decoderingscontext aan het einde van het afspeelvenster (ingeschakeld) is verwijderd of niet (uitgeschakeld). </p> <p>Als u bijvoorbeeld wilt opgeven dat de inhoud alleen gedurende 60 minuten mag worden weergegeven en een vaste stop vereist: 
     <codeblock>
       -w&amp;nbsp;60,enableHS 
     </codeblock> </p> <p>Opmerking:  <i>Harde stop</i> wordt momenteel niet ondersteund in Flash Player, Android en iOS. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -l minuten </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De duur van het in cache plaatsen van licenties is de tijd in minuten dat een licentie in de Licentieopslag van de client kan worden opgeslagen nadat de licentie door de server is uitgegeven. De waarde moet niet-negatief zijn. </p> <p>U kunt <span class="codeph"> -l 0 opgeven </span> om aan te geven dat het in cache plaatsen van licenties niet is toegestaan. Geef voor een onbeperkte licentie-caching <span class="codeph"> -l op </span> zonder minuten. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -ldate </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De einddatum van de licentiecache. </p> <p class="- topic/p ">Dit geeft de einddatum aan waarop de client licenties in de licentiesector van de client in cache kan plaatsen nadat de Primetime DRM-server de licentie heeft uitgegeven. </p> <p>U kunt de datum in de volgende notaties opgeven: 
     <ul id="ul_112DE7248A9C48B19520A3AA9E5D1F03"> 
      <li id="li_01C5400E78B84A3B8955972FBA875AAC"> <span class="+ topic/ph pr-d/codeph codeph"> jjjj-mm-dd </span> </li> 
      <li id="li_AA13B1EFA07A4542A3DB41FA3320B143"> <span class="+ topic/ph pr-d/codeph codeph"> jjjj-mm-dd-h24:min:sec </span> </li> 
     </ul>Bijvoorbeeld, <span class="codeph"> 2008-12-1 </span> of <span class="codeph"> 2008-12-1-00:00:00 </span> voor middernacht op 1 December, 2008. U moet <span class="codeph"> -l toepassen </span> zonder minuten op te geven voor het in cache plaatsen van een onbeperkte licentie. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -authNS </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De verificatienaamruimte. </p> <p class="- topic/p ">Als u deze optie toepast, moet de client een gebruikersnaam en wachtwoord invoeren die door de opgegeven instantie zijn uitgegeven. </p> <p>U kunt deze optie niet samen met <span class="codeph"> -x toepassen </span>. </p> <p>Deze optie is niet toegestaan voor updates. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -x </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Anonieme toegang toestaan. </p> <p class="- topic/p ">U kunt deze optie niet samen met <span class="codeph"> -authNS toepassen </span>. </p> <p class="- topic/p ">Deze optie is niet toegestaan voor updates. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -air pubId </span>[: <span class="+ topic/ph pr-d/codeph codeph"> appId </span>[:[ <span class="+ topic/ph pr-d/codeph codeph"> min </span>]:[ <span class="+ topic/ph pr-d/codeph codeph"> max </span>]] </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Een lijst met toegestane AIR-toepassingen die beveiligde inhoud kunnen afspelen. </p> <p class="- topic/p ">U kunt deze optie toepassen om te beperken welke uitgevers, toepassingen, en versies tot de inhoud kunnen toegang hebben die met dit beleid DRM wordt beschermd. </p> <p class="- topic/p ">Als u geen <i class="+ topic/ph hi-d/i ">appId</i>opgeeft, zijn alle toepassingen voor uitgever <i class="+ topic/ph hi-d/i ">pubId</i> toegestaan. </p> <p>Opmerking:  <i class="+ topic/ph hi-d/i ">min</i> - en <i class="+ topic/ph hi-d/i ">max</i> -versienummers zijn optioneel. </p> <p class="- topic/p ">U kunt meerdere <span class="codeph"> -air- </span> opties opgeven om meerdere toepassingen toe te staan. Als u geen AIR- of SWF-toepassing opgeeft, hebben alle toepassingen toegang tot deze inhoud. Als u tijdens een update alle items uit de lijst wilt verwijderen of verwijderen, past u <span class="codeph"> -air toe </span> zonder de resterende argumenten. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -drmBlacklist name </span> / <i class="+ topic/ph hi-d/i "></i> value <span class="+ topic/ph pr-d/codeph codeph"> </span><i class="+ topic/ph hi-d/i "> </i> <span class="+ topic/ph pr-d/codeph codeph"> pairs </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De DRM-clients die geen toegang hebben tot beveiligde inhoud. </p> <p class="- topic/p ">De waarde ondersteunt door komma's gescheiden naam:waardeparen in de volgende indeling: </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> os | release= stringValue </span> </p> <p class="- topic/p ">Bijvoorbeeld, <span class="codeph"> os=Win, versie=2.0.1 </span>. Als u tijdens een update alle items uit de lijst wilt verwijderen, past u <span class="codeph"> -drmBlacklist toe </span> zonder de resterende argumenten. </p> </td> 
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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Beperkingen van de bescherming van digitale uitvoer </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -runtimeBlacklist-naam </span> / <i class="+ topic/ph hi-d/i "></i> value <span class="+ topic/ph pr-d/codeph codeph"> </span><i class="+ topic/ph hi-d/i "> </i> <span class="+ topic/ph pr-d/codeph codeph"> paren </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De toepassingsruntimes die geen toegang hebben tot beveiligde inhoud. </p> <p class="- topic/p ">De waarde ondersteunt door komma's gescheiden naam:waardeparen in de volgende indeling: </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> os | Aanvraag | release= stringValue </span> </p> <p class="- topic/p ">Bijvoorbeeld <span class="codeph"> os=Win,release=2.0.1,application=AIR </span>. Als u tijdens een update alle items uit de lijst wilt verwijderen, past u <span class="codeph"> -runtimeBlacklist toe </span> zonder de resterende argumenten. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -runtimeLevel int </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Geeft aan dat de runtimes van de toepassing een opgegeven minimumbeveiligingsniveau moeten hebben om toegang te krijgen tot beveiligde inhoud. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -swf url </span> </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -swf file= swf_file </span>, <span class="+ topic/ph pr-d/codeph codeph"> time= max_time_to_verify </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Een lijst met SWF-toepassingen die beveiligde inhoud mogen afspelen. </p> <p class="- topic/p ">U kunt meerdere <span class="codeph"> -swf- </span> opties opgeven om meerdere toepassingen toe te staan. Als u geen AIR- of SWF-toepassingen opgeeft, hebben alle toepassingen toegang tot deze inhoud. </p> <p>Als u tijdens een update alle items uit de lijst wilt verwijderen, past u <span class="codeph"> -swf toe </span> zonder de resterende argumenten. Als u een SWF-bestand wilt identificeren aan de hand van de hashwaarde, moet u het SWF-bestand opgeven waarvoor de hash moet worden berekend en de maximale tijd die nodig is om de SWF-verificatie te voltooien (in seconden). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -k name= value </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Hier geeft u aangepaste sleutels of waarden op die u aan een DRM-beleid wilt toevoegen. </p> <p class="- topic/p ">U kunt meerdere <span class="codeph"> -k- </span> opties opgeven. Tijdens de update kunt u <span class="codeph"> -k </span> zonder de resterende argumenten toepassen als u alle eigenschappen wilt verwijderen. De interpretatie of verwerking van de gegevens wordt beheerd door de Primetime DRM-licentieserver. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -p name= value </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Voegt een aangepaste eigenschap toe die wordt weergegeven in de licentie die voor elke client wordt gegenereerd. </p> <p class="- topic/p ">U kunt meerdere <span class="codeph"> -p- </span> opties opgeven om meerdere eigenschappen toe te voegen. Tijdens een update moet u <span class="codeph"> -p toepassen </span> zonder de resterende argumenten als u alle eigenschappen wilt verwijderen. De interpretatie of verwerking van deze gegevens wordt beheerd door de implementatie van de clienttoepassing. </p> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> <span class="codeph"> -opOTA whitelist=&lt;connection types&gt; </span> </span> </td> 
   <td colname="2" class="- topic/entry "> Over de beperkingen van de bescherming van de luchtoutput (OTA). In het <span class="codeph"> whitelist- </span> veld wordt aangegeven welke verbindingstypen zijn toegestaan voor lijst en de indeling van &lt;verbindingstypen&gt; is <span class="codeph"> [type(,type)*] </span>, waarbij het type een van de volgende kan zijn: MIRACAST, AIRPLAY, WIDI, DLNA </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -opResolution &lt;filename&gt; </span> </td> 
   <td colname="2" class="- topic/entry "> <p>Op resolutie gebaseerde beperkingen van de outputbescherming zoals die in het gespecificeerde dossier worden bepaald. </p> <p>De codering van dit bestand is JSON. De grammatica voor de opmaak vindt u in <i>Info over op resolutie gebaseerde uitvoerbeveiliging</i>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Voorbeelden**

Om een beleid tot stand te brengen dat anonieme toegang tot uw inhoud toestaat, gebruikend uw eigen dossier van configuratieeigenschappen:

```
java -jar libs\AdobePolicyManager.jar new policy_test.pol -x -c my_configuration.properties
```
