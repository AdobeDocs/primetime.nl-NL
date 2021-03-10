---
title: Gebruik van opdrachtregels
description: Gebruik van opdrachtregels
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '1026'
ht-degree: 0%

---


# Gebruik van opdrachtregel {#command-line-usage}

Alvorens de Manager van het Beleid te gebruiken, zorg ervoor dat u aan de vereisten voldoet die in Vereisten worden vermeld.

Beleidsbeheer bevindt zich in de map [!DNL \Reference Implementation\Command Line Tools] op de dvd. Gebruik de volgende syntaxis om het gereedschap uit te voeren:

```
java -jar AdobePolicyManager.jar  
<i class="+ topic ph hi-d="" i "="">
  command filename [options] 
</i class="+ topic>
```

De volgende tabel bevat beschrijvingen van de opdrachtregelacties die in de bovenstaande syntaxis worden getoond:

| Handeling opdrachtregel | Beschrijving |
|---|---|
| `new` | Hiermee maakt u een nieuw beleid. |
| `detail` | Beschrijft een bestaand beleid. |
| `update` | Hiermee werkt u een bestaand beleid bij. |

In de volgende tabel worden de opdrachtregelopties beschreven die samen met de bovenstaande syntaxis kunnen worden opgegeven:

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_q5h_cpy_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Opdrachtregeloptie </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Beschrijving </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -c configfile  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Hier geeft u de locatie van het configuratiebestand op. Als deze optie niet wordt gebruikt, zal de Manager van het Beleid <span class="filepath"> flashaccess.properties </span> in de het werk folder zoeken. De opties die op de bevellijn worden gespecificeerd hebben belangrijkheid over die aanwezig in het configuratiedossier. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Als het doelbestand al bestaat, overschrijft u dit zonder dat u daarom wordt gevraagd. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -noprompt  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Vraag niet of het doelbestand moet worden overschreven. Als het doelbestand al bestaat en <span class="codeph"> -o </span> niet is ingesteld, wordt een fout geretourneerd. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -root  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Geeft aan dat het beleid een hoofdlicentie heeft. Niet toegestaan voor updates. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -e-datum  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De datum waarop de certificaten geldig zijn. Geef <span class="+ topic/ph pr-d/codeph codeph"> jjjj-mm-dd </span> of <span class="+ topic/ph pr-d/codeph codeph"> jjjj-mm-dd-h24:min:sec </span> op. Bijvoorbeeld 2008-12-1 of 2008-12-1-00:00:00 voor middernacht op 1 December 2008. De waarde moet groter zijn dan de waarde van <span class="codeph"> -s </span>, indien aanwezig. Deze optie kan niet worden gebruikt met <span class="codeph"> -r </span>. Als u de einddatum wilt verwijderen bij het bijwerken van een beleid, gebruikt u <span class="codeph"> -e </span> zonder een datum op te geven. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -r minuten  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De duur (minuten) gedurende welke de met dit beleid beveiligde inhoud geldig is, te beginnen wanneer de inhoud met de pakketsoftware is beveiligd. De waarde moet niet-negatief zijn. Deze optie kan niet worden gebruikt met <span class="codeph"> -e </span>. Als u de duur van het bijwerken van een beleid wilt verwijderen, gebruikt u <span class="codeph"> -r </span> zonder een aantal minuten op te geven. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -s date  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De datum waarna de certificaten geldig zijn. Geef <span class="+ topic/ph pr-d/codeph codeph"> jjjj-mm-dd </span> of <span class="+ topic/ph pr-d/codeph codeph"> jjjj-mm-dd-h24:min:sec </span> op. Bijvoorbeeld 2008-12-1 of 2008-12-1-00:00:00 voor middernacht op 1 December 2008. De waarde moet lager zijn dan de waarde van <span class="codeph"> -e </span>, indien aanwezig. Deze optie kan niet worden gebruikt met <span class="codeph"> -r </span>. Als u de begindatum wilt verwijderen bij het bijwerken van een beleid, gebruikt u <span class="codeph"> -s </span> zonder een datum op te geven. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -w minuten  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Het afspeelvenster (het aantal minuten dat de inhoud kan worden weergegeven, te beginnen bij het eerste afspelen). Als deze optie niet is opgegeven of als <span class="codeph"> -w </span> wordt gebruikt zonder het aantal minuten op te geven, is er geen beperking voor het afspeelvenster. De waarde moet niet-negatief zijn. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -l minuten  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De duur van het in cache plaatsen van licenties in minuten. Dit is de tijd dat een licentie in de licentieserve van de client in cache mag worden geplaatst nadat de licentie door de server is uitgegeven. De waarde moet niet-negatief zijn. Geef <span class="codeph"> -l 0 </span> op om aan te geven dat het in cache plaatsen van licenties niet is toegestaan. Gebruik <span class="codeph"> -l </span> zonder een aantal minuten op te geven voor het in cache plaatsen van een onbeperkte licentie. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -ldate  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De einddatum van het in cache plaatsen van licenties (de datum waarna licenties mogelijk niet in cache worden geplaatst in de Licentieopslag van de client, nadat de licentie door de server is uitgegeven). Geef <span class="+ topic/ph pr-d/codeph codeph"> jjjj-mm-dd </span><i class="+ topic/ph hi-d/i "> </i>of<i class="+ topic/ph hi-d/i "> </i> <span class="+ topic/ph pr-d/codeph codeph"> jjjj-mm-dd-h24:min:sec </span> op. Bijvoorbeeld 2008-12-1 of 2008-12-1-00:00:00 voor middernacht op 1 December 2008. Gebruik <span class="codeph"> -l </span> zonder een aantal minuten op te geven voor het in cache plaatsen van een onbeperkte licentie. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -authNS  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De verificatienaamruimte. Indien opgegeven, moet de client worden geverifieerd met een gebruikersnaam en wachtwoord die door de opgegeven instantie zijn uitgegeven. Deze optie kan niet worden gebruikt met <span class="codeph"> -x </span>. Updates zijn niet toegestaan. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -x  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Anonieme toegang toestaan. Deze optie kan niet worden gebruikt met <span class="codeph"> -authNS </span>. Updates zijn niet toegestaan. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -air pubId  </span>[:  <span class="+ topic/ph pr-d/codeph codeph"> appId  </span>[:[  <span class="+ topic/ph pr-d/codeph codeph"> min  </span>]:[  <span class="+ topic/ph pr-d/codeph codeph"> max  </span>]] </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Een lijst van gewenste personen van AIR-toepassingen die beveiligde inhoud mag afspelen. Gebruik deze optie om te beperken tot welke uitgevers, toepassingen en versies toegang hebben tot inhoud die met dit beleid is beveiligd. </p> <p class="- topic/p ">Als <i class="+ topic/ph hi-d/i ">appId</i> niet is opgegeven, zijn alle toepassingen voor uitgever <i class="+ topic/ph hi-d/i ">pubId</i> toegestaan. </p> <p class="- topic/p "><i class="+ topic/ph hi-d/i "></i> minen  <i class="+ topic/ph hi-d/i "></i> versienummers zijn optioneel. </p> <p class="- topic/p ">U kunt meerdere <span class="codeph"> -air </span>-opties opgeven om meerdere toepassingen toe te staan. Als er geen AIR- of SWF-toepassingen zijn opgegeven, hebben alle toepassingen toegang tot deze inhoud. Gebruik tijdens een update -air zonder de resterende argumenten om alle items uit de lijst te verwijderen. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -drmBlacklist name  </span> <i class="+ topic/ph hi-d/i ">/</i> <span class="+ topic/ph pr-d/codeph codeph"> value  </span> <i class="+ topic/ph hi-d/i "> </i> <span class="+ topic/ph pr-d/codeph codeph"> pairs  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De DRM-clients hebben toegang tot beveiligde inhoud beperkt. De waarde bestaat uit door komma's gescheiden naam:waardeparen met de volgende notatie: </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> os | release= stringValue  </span> </p> <p class="- topic/p ">Bijvoorbeeld <span class="codeph"> os=Win,release=2.0.1 </span>. Tijdens een update gebruikt u <span class="codeph"> -drmBlacklist </span> zonder de resterende argumenten om alle vermeldingen uit de lijst te verwijderen. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -drmLevel int  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Geeft aan dat DRM-clients het opgegeven minimale beveiligingsniveau moeten hebben om toegang te krijgen tot beveiligde inhoud. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -opAnalog NO_PROTECTION | USE_IF_AVAILABLE | VEREIST | NO_PLAYBACK | ACP_REQUIRED | CGMS-A_REQUIRED | USE_ACP_IF_AVAILABLE | USE_CGMS-A_IF_AVAILABLE  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Restricties op het gebied van analoge uitvoerbescherming. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -opDigital NO_PROTECTION | USE_IF_AVAILABLE | VEREIST | NO_PLAYBACK  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Beperkingen op het gebied van de bescherming van digitale uitvoer. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -runtimeBlacklist naam  </span> <i class="+ topic/ph hi-d/i ">/</i> <span class="+ topic/ph pr-d/codeph codeph"> value  </span> <i class="+ topic/ph hi-d/i "> </i> <span class="+ topic/ph pr-d/codeph codeph"> paren  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De runtimes van de toepassing hebben de toegang tot beveiligde inhoud beperkt. De waarde bestaat uit door komma's gescheiden naam:waardeparen met de volgende notatie: </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> os | Aanvraag | release= stringValue  </span> </p> <p class="- topic/p ">Bijvoorbeeld <span class="codeph"> os=Win,release=2.0.1,application=AIR </span>. Tijdens een update gebruikt u <span class="codeph"> -runtimeBlacklist </span> zonder de resterende argumenten om alle items uit de lijst te verwijderen. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -runtimeLevel int  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Geeft aan dat de runtimes van de toepassing het opgegeven minimale beveiligingsniveau moeten hebben om toegang te krijgen tot beveiligde inhoud. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -swf url  </span> </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -swf file= swf_file  </span>,  <span class="+ topic/ph pr-d/codeph codeph"> time= max_time_to_verify  </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Een lijst van gewenste personen van SWF-toepassingen die beveiligde inhoud mogen afspelen. U kunt opties voor meerdere SWF-bestanden opgeven om meerdere toepassingen toe te staan. Als er geen AIR- of SWF-toepassingen zijn opgegeven, hebben alle toepassingen toegang tot deze inhoud. Gebruik tijdens een update -swf zonder de resterende argumenten om alle items uit de lijst te verwijderen. Als u een SWF wilt identificeren aan de hand van de hashwaarde, geeft u het SWF-bestand op waarvoor de hash moet worden berekend en de maximale tijd die nodig is om de SWF-verificatie te voltooien (in seconden). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -k name= value  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Hiermee geeft u aangepaste sleutels of waarden op die u aan het beleid wilt toevoegen. Er kunnen meerdere <span class="codeph"> -k </span> opties worden opgegeven. Tijdens de update gebruikt u <span class="codeph"> -k </span> zonder de resterende argumenten om alle eigenschappen te verwijderen. De interpretatie of behandeling van deze gegevens is volledig tot de implementatie van de de vergunningsserver van de Toegang van de Adobe. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -p name= value  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Voegt een aangepaste eigenschap toe, die wordt weergegeven in de licentie die voor elke client wordt gegenereerd. Er kunnen meerdere <span class="codeph"> -p </span> opties worden opgegeven om meerdere eigenschappen toe te voegen. Tijdens een update gebruikt u <span class="codeph"> -p </span> zonder de resterende argumenten om alle eigenschappen te verwijderen. De interpretatie of verwerking van deze gegevens is volledig afhankelijk van de implementatie van de clienttoepassing. </p> </td> 
  </tr> 
 </tbody> 
</table>

