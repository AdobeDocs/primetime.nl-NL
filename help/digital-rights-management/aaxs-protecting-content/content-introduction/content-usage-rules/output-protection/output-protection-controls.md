---
title: Besturingselementen voor uitvoerbeveiliging
description: Besturingselementen voor uitvoerbeveiliging
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 0%

---

# Besturingselementen voor uitvoerbeveiliging {#output-protection-controls}

**Bepaal of uitvoer naar externe renderapparaten is beveiligd. Geef onafhankelijke analoge en digitale uitvoer op.**

Controls whether output to external rendering devices should be limited. Een extern apparaat wordt gedefinieerd als een video- of audioapparaat dat niet in de computer is ingesloten. In de lijst met externe apparaten zijn geïntegreerde beeldschermen, zoals notebookcomputers, niet opgenomen. Restricties voor analoge en digitale uitvoer kunnen onafhankelijk worden opgegeven.

De volgende opties/niveaus van handhaving zijn beschikbaar:

<table frame="all" colsep="0" rowsep="1" id="adobetable_fvw_5fx_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Optie </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Ondersteund in analoge apparaten </p> </th> 
   <th colname="3" class="- topic/entry entry"> <p class="- topic/p ">Ondersteund in digitale apparaten </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Vereist</b> — Analoge kopieerbeveiliging (ACP) of Copy Generation Management System - Analog (CGMS-A) moet uitvoerbeveiliging zijn ingeschakeld om inhoud op een extern apparaat af te spelen. De cliënten van de Toegang van de Adobe moeten outputbescherming toelaten gebruikend ACS of CGMS-A. Op apparaten die beide steunen, zullen de Adobe Toegang 3.0 cliënten proberen om allebei toe te laten. U moet echter slechts één speler inschakelen om de inhoud af te spelen. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">ACS vereist</b> — ACS-outputbescherming is vereist. Afspelen is niet toegestaan op CGMS-A. Adobe Access 2.0-clients bieden geen ondersteuning voor deze optie. Als deze optie is ingesteld, gedraagt een Adobe Access 2.0-client zich alsof de optie "Geen afspelen" is opgegeven. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">CGMS-A vereist</b> — CGMS-A-uitvoerbeveiliging is vereist. Afspelen is niet toegestaan voor ACS-landen. Adobe Access 2.0-clients bieden geen ondersteuning voor deze optie. Als deze optie is ingesteld, gedraagt een Adobe Access 2.0-client zich alsof de optie "Geen afspelen" is opgegeven. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Gebruik indien beschikbaar</b> — Poging om ACS- en CGMS-A-uitvoerbescherming in te schakelen, indien beschikbaar, en afspelen toe te staan als deze niet beschikbaar is. Adobe Access 3.0-clients zullen proberen om, indien mogelijk, zowel ACS als CGMS-A in te schakelen. Adobe Access 2.0-clients zullen alleen proberen ACS of CGMS-A in te schakelen. De Adobe Access-client zal bijvoorbeeld proberen ACS of CGMS-A in te schakelen. Als de poging slaagt, zal de andere optie niet worden toegelaten. Als de poging mislukt, wordt een tweede poging gedaan om de andere optie in te schakelen. Zelfs als beide pogingen mislukken, wordt de inhoud toch afgespeeld. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">ACS gebruiken indien beschikbaar</b> — Poging om ACS-uitvoerbescherming in te schakelen indien beschikbaar, maar afspelen toestaan als deze niet beschikbaar is. De bescherming is niet beschikbaar op CGMS-A. Adobe Access 2.0-clients bieden geen ondersteuning voor deze optie. Indien ingesteld, gedraagt een Adobe Access 2.0-client zich alsof de optie "Geen beveiliging" is opgegeven. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">CGMS-A gebruiken indien beschikbaar </b>— Poging om CGMS-A-uitvoerbeveiliging in te schakelen, indien beschikbaar, maar afspelen toestaan als dit niet het geval is. De bescherming is niet beschikbaar op ACS. Adobe Access 2.0-clients bieden geen ondersteuning voor deze optie. Indien ingesteld, gedraagt een Adobe Access 2.0-client zich alsof de optie "Geen beveiliging" is opgegeven. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Geen bescherming</b> — Voor analoge en digitale uitvoer wordt geen uitvoerbescherming ingeschakeld. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Geen afspelen</b> —Afspelen naar een extern apparaat niet toestaan voor analoge en digitale uitvoer. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Hoewel deze regels op alle platforms consistent worden toegepast, is het momenteel alleen mogelijk om uitvoerbeveiliging op Windows-platforms veilig in te schakelen. Op andere platforms (zoals Macintosh en Linux) zijn er geen ondersteunende besturingssysteemfuncties beschikbaar voor toepassingen van derden.

Voorbeeld van gebruik: sommige inhoud dwingt uitvoerbeveiligingselementen af en het beschermingsniveau kan door de inhoudsdistributeur worden ingesteld. Als &quot;Vereist&quot; is opgegeven en wordt geprobeerd de inhoud af te spelen op een Macintosh, wordt de inhoud niet afgespeeld op externe apparaten. De inhoud wordt echter afgespeeld op interne monitoren.

Als &quot;Vereist&quot; is opgegeven en wordt geprobeerd om de inhoud op Linux af te spelen, wordt de inhoud op geen enkel apparaat afgespeeld, omdat er geen onderscheid kan worden gemaakt tussen interne en externe apparaten.

Als u &quot;Gebruik indien beschikbaar&quot; opgeeft, wordt de uitvoerbeveiliging waar mogelijk ingeschakeld. Op Windows-computers die ondersteuning bieden voor het Certified Output Protection Protocol (COPP) wordt de inhoud met uitvoerbeveiliging doorgegeven aan een extern scherm. Dit voorbeeld wordt soms &quot;selecteerbare outputcontrole&quot;genoemd.
