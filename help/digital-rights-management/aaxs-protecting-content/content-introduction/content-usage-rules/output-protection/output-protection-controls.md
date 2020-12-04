---
seo-title: Besturingselementen voor uitvoerbeveiliging
title: Besturingselementen voor uitvoerbeveiliging
uuid: 1f4cc617-7f14-4952-8e61-6acbdf01d10e
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 0%

---


# Besturingselementen voor uitvoerbescherming {#output-protection-controls}

**Bepaal of uitvoer naar externe renderapparaten is beveiligd. Geef onafhankelijke analoge en digitale uitvoer op.**

Bepaalt of uitvoer naar externe renderingapparaten moet worden beperkt. Een extern apparaat wordt gedefinieerd als een video- of audioapparaat dat niet in de computer is ingesloten. In de lijst met externe apparaten zijn geïntegreerde beeldschermen, zoals notebookcomputers, niet opgenomen. Restricties voor analoge en digitale uitvoer kunnen onafhankelijk worden opgegeven.

De volgende opties/niveaus van handhaving zijn beschikbaar:

<table frame="all" colsep="0" rowsep="1" id="adobetable_fvw_5fx_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Option </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Ondersteund in analoge apparaten </p> </th> 
   <th colname="3" class="- topic/entry entry"> <p class="- topic/p ">Ondersteund in digitale apparaten </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Vereist</b> : de bescherming van analoge kopieerbeveiliging (ACP) of het systeem van het beheer van de productie van kopieën - analoge (CGMS-A)-uitvoer moet zijn ingeschakeld om de inhoud op een extern apparaat af te spelen. De cliënten van de Toegang van Adobe moeten outputbescherming toelaten gebruikend ACS of CGMS-A. Op apparaten die beide steunen, zullen de Adobe Access 3.0 cliënten proberen om allebei toe te laten. U moet echter slechts één speler inschakelen om de inhoud af te spelen. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">ACS vereist</b>  — ACS-uitvoerbescherming is vereist. Afspelen is niet toegestaan op CGMS-A. Adobe Access 2.0-clients bieden geen ondersteuning voor deze optie. Indien ingesteld, gedraagt een Adobe Access 2.0-client zich alsof de optie "Geen afspelen" is opgegeven. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">CGMS-A Required</b>  — CGMS-A output protection is required. Afspelen is niet toegestaan voor ACS-landen. Adobe Access 2.0-clients bieden geen ondersteuning voor deze optie. Indien ingesteld, gedraagt een Adobe Access 2.0-client zich alsof de optie "Geen afspelen" is opgegeven. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Gebruik indien beschikbaar</b>  — probeer ACS- en CGMS-A-uitvoerbeveiliging in te schakelen als deze beschikbaar is en sta afspelen toe als deze niet beschikbaar is. Adobe Access 3.0-klanten zullen proberen om, indien mogelijk, zowel ACS als CGMS-A in te schakelen. Adobe Access 2.0-clients zullen alleen proberen ACS of CGMS-A in te schakelen. De Adobe Access-client zal bijvoorbeeld proberen ACS of CGMS-A in te schakelen. Als de poging slaagt, zal de andere optie niet worden toegelaten. Als de poging mislukt, wordt een tweede poging gedaan om de andere optie in te schakelen. Zelfs als beide pogingen mislukken, wordt de inhoud toch afgespeeld. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Gebruik ACP indien beschikbaar</b>  — Poging om ACS-uitvoerbescherming in te schakelen indien beschikbaar, maar sta afspelen toe als deze niet beschikbaar is. De bescherming is niet beschikbaar op CGMS-A. Adobe Access 2.0-clients bieden geen ondersteuning voor deze optie. Indien ingesteld, gedraagt een Adobe Access 2.0-client zich alsof de optie "Geen beveiliging" is opgegeven. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Gebruik CGMS-A indien beschikbaar  </b>— probeer CGMS-A-uitvoerbeveiliging in te schakelen als deze beschikbaar is, maar sta afspelen toe als deze niet beschikbaar is. De bescherming is niet beschikbaar op ACS. Adobe Access 2.0-clients bieden geen ondersteuning voor deze optie. Indien ingesteld, gedraagt een Adobe Access 2.0-client zich alsof de optie "Geen beveiliging" is opgegeven. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Geen bescherming</b> — Er wordt geen uitvoerbescherming afgedwongen voor analoge en digitale uitvoer. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Afspelen</b>  is niet mogelijk - Afspelen op een extern apparaat voor analoge en digitale uitvoer is niet toegestaan. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Hoewel deze regels op alle platforms consistent worden toegepast, is het momenteel alleen mogelijk om uitvoerbeveiliging op Windows-platforms veilig in te schakelen. Op andere platforms (zoals Macintosh en Linux) zijn er geen ondersteunende besturingssysteemfuncties beschikbaar voor toepassingen van derden.

Voorbeeld van gebruik: Sommige inhoud dwingt uitvoerbeveiligingsinstellingen af en het beschermingsniveau kan worden ingesteld door de inhoudsdistributeur. Als &quot;Vereist&quot; is opgegeven en wordt geprobeerd de inhoud af te spelen op een Macintosh, wordt de inhoud niet afgespeeld op externe apparaten. De inhoud wordt echter afgespeeld op interne monitoren.

Als &quot;Vereist&quot; is opgegeven en wordt geprobeerd om de inhoud op Linux af te spelen, wordt de inhoud op geen enkel apparaat afgespeeld, omdat er geen onderscheid kan worden gemaakt tussen interne en externe apparaten.

Als u &quot;Gebruik indien beschikbaar&quot; opgeeft, wordt de uitvoerbeveiliging waar mogelijk ingeschakeld. Op Windows-computers die ondersteuning bieden voor het Certified Output Protection Protocol (COPP) wordt de inhoud met uitvoerbeveiliging doorgegeven aan een extern scherm. Dit voorbeeld wordt soms &quot;selecteerbare outputcontrole&quot;genoemd.
