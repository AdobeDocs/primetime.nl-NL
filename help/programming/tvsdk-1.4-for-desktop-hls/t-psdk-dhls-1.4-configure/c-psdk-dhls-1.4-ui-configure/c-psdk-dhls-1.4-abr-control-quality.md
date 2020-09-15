---
description: HLS- en DASH-streams bieden verschillende bitsnelheidcoderingen (profielen) voor dezelfde korte videoprand. TVSDK kan het kwaliteitsniveau voor elke uitbarsting selecteren op basis van de beschikbare bandbreedte.
seo-description: HLS- en DASH-streams bieden verschillende bitsnelheidcoderingen (profielen) voor dezelfde korte videoprand. TVSDK kan het kwaliteitsniveau voor elke uitbarsting selecteren op basis van de beschikbare bandbreedte.
seo-title: Adaptieve bitsnelheden (ABR) voor videokwaliteit
title: Adaptieve bitsnelheden (ABR) voor videokwaliteit
uuid: e3d5ef90-067d-48e0-a025-081de931d842
translation-type: tm+mt
source-git-commit: 5df9a8b98baaf1cd1803581d2b60c7ed4261a0e8
workflow-type: tm+mt
source-wordcount: '1011'
ht-degree: 0%

---


# Adaptieve bitsnelheden (ABR) voor videokwaliteit{#adaptive-bit-rates-abr-for-video-quality}

HLS- en DASH-streams bieden verschillende bitsnelheidcoderingen (profielen) voor dezelfde korte videoprand. TVSDK kan het kwaliteitsniveau voor elke uitbarsting selecteren op basis van de beschikbare bandbreedte.

TVSDK controleert constant het beetjetarief om ervoor te zorgen dat de inhoud bij de optimale beetjetarief voor de huidige netwerkverbinding wordt gespeeld.

U kunt het adaptieve beetje-tarief (ABR) omschakelingsbeleid en de aanvankelijke, minimum, en maximumbeetjetarieven voor een multibit-tarief (MBR) stroom plaatsen. TVSDK schakelt automatisch over naar de bitsnelheid die de beste afspeelervaring in de opgegeven configuratie biedt.

<table id="table_AF838E082235406AA359BF1C1A77F85F"> 
 <tbody> 
  <tr> 
   <td colname="col01"> Oorspronkelijke bitsnelheid </td> 
   <td colname="col2"> <p>De gewenste afspeelbitsnelheid (in bits per seconde) voor het eerste segment. Wanneer het afspelen begint, wordt het dichtstbijzijnde profiel, dat gelijk is aan of groter is dan de aanvankelijke bitsnelheid, gebruikt voor het eerste segment. </p> <p> Als een minimale bitsnelheid is gedefinieerd en de aanvankelijke bitsnelheid lager is dan de minimale bitsnelheid, selecteert TVSDK het profiel met de laagste bitsnelheid boven de minimale bitsnelheid. Als de aanvankelijke snelheid boven de maximumsnelheid ligt, kiest TVSDK de hoogste snelheid onder de maximumsnelheid. </p> <p>Als de aanvankelijke bitsnelheid nul of ongedefinieerd is, wordt de aanvankelijke bitsnelheid bepaald door het ABR-beleid. </p> <p> <span class="apiname"> ABRInitialBitRate </span> keert een geheelwaarde terug die het byte-per-tweede profiel vertegenwoordigt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Minimale bitsnelheid </td> 
   <td colname="col2"> <p>Het laagste toegestane beetjetarief waaraan ABR kan schakelen. De omschakeling ABR negeert profielen met een beetjetarief dat lager is dan dit beetjetarief. </p> <p> <span class="apiname"> ABRMinBitRate </span> retourneert een geheel-getalwaarde die het bits-per-tweede profiel vertegenwoordigt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Maximale bitsnelheid </td> 
   <td colname="col2"> <p>Het hoogste toegestane beetjetarief waaraan ABR kan schakelen. De omschakeling ABR negeert profielen met een beetjetarief hoger dan dit beetjetarief. </p> <p> <span class="apiname"> ABRMaxBitRate </span> retourneert een geheel-getalwaarde die het bits-per-tweede profiel vertegenwoordigt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> ABR-switchbeleid </td> 
   <td colname="col2"> De schakelaars van de playback geleidelijk aan het hoogste beetje-tarief profiel wanneer mogelijk. U kunt het beleid voor omschakeling plaatsen ABR, die bepaalt hoe snel TVSDK tussen profielen schakelt. Het gebrek is <span class="codeph"> MODERATE_POLICY </span>. <p>Wanneer TVSDK besluit over te schakelen naar een hogere bitsnelheid, selecteert de speler het ideale bitsnelheidprofiel om over te schakelen op basis van het huidige ABR-beleid: 
     <ul id="ul_058D0FFC944C476A83BB9E756B95DEBD"> 
      <li id="li_C690A12DC34C4754B01C2D0616FB6A0A"> <span class="codeph"> CONSERVATIVE_POLICY </span>: Schakelt over naar het profiel met de volgende hogere bitsnelheid wanneer de bandbreedte 50% hoger is dan de huidige bitsnelheid. </li> 
      <li id="li_FF5BDB099B554940AC296938C7A12B81"> <span class="codeph"> MODERATE_POLICY </span>: Schakelt over naar het volgende profiel met een hogere bitsnelheid wanneer de bandbreedte 20% hoger is dan de huidige bitsnelheid. </li> 
      <li id="li_E602508429864C279BF78360E95718A6"> <span class="codeph"> AGRESSIVE_POLICY </span>: Schakelt onmiddellijk naar het hoogste beetje-tarief profiel wanneer de bandbreedte hoger is dan het huidige beetjetarief. </li> 
     </ul> </p> <p>Als de aanvankelijke bitsnelheid nul is of niet is opgegeven, maar een beleid is opgegeven, begint het afspelen met het laagste bitsnelheidprofiel voor conservatief, het profiel dat zich het dichtst bij de mediane bitsnelheid van beschikbare profielen voor matig en het hoogste bitsnelheidprofiel voor agressief bevindt. </p> <p>Het beleid werkt in de beperkingen van de minimum en maximumbeetjetarieven, als deze tarieven worden gespecificeerd. </p> <p> <span class="codeph"> ABRPopolicy </span> retourneert de huidige instelling in de <span class="codeph"> opsomming ABRControlParameters </span> : CONSERVATIVE_POLICY, MODERATE_POLICY, of AGGRESSIVE_POLICY. </p> </td> 
  </tr> 
 </tbody> 
</table>

Houd rekening met het volgende:

* Het uitvalmechanisme van TVSDK heeft mogelijk voorrang op uw instellingen, omdat TVSDK een continue afspeelervaring bevordert in plaats van strikt de hand te houden aan de controleparameters.
* Wanneer de bitsnelheid verandert, wordt TVSDK verzonden `ProfileEvent.PROFILE_CHANGED`.
* U kunt de ABR-instellingen op elk gewenst moment wijzigen en de speler schakelt over naar het profiel dat het meest overeenkomt met de meest recente instellingen.

Als een stream bijvoorbeeld de volgende profielen heeft:

* 1: 300000
* 2: 700000
* 3: 1500000
* 4: 2400000
* 5: 4000000

Als u een bereik van 300000 tot 2000000 opgeeft, houdt TVSDK alleen rekening met de profielen 1, 2 en 3. Hierdoor kunnen toepassingen zich aanpassen aan verschillende netwerkvoorwaarden, zoals het schakelen van wifi naar 3G of naar verschillende apparaten, zoals een telefoon, tablet of desktopcomputer.

Voer een van de volgende handelingen uit om ABR-besturingsparameters in te stellen:

* Gebruik de klasse `ABRControlParameterBuilder` helper om een willekeurige subset van de parameters in te stellen (wordt uitgevoerd op `ABRControlParameter` achter de scènes)

* Stel de parameters voor de `ABRControlParameter` klasse in.

## Aangepaste bitsnelheden configureren met ABRControlParametersBuilder {#section_3DDE397A7CE445E1832EBAA46CE5C069}

Het gebruik van de `ABRControlParametersBuilder` hulplijnklasse is de eenvoudigste, meest efficiënte manier om ABR-parameters in te stellen.

* De `ABRControlParametersBuilder` constructor stelt alle ABR-parameters in op standaardwaarden voor het onderliggende `ABRControlParameters` object.

* U kunt individuele parameters ABR tijdens runtime terugstellen, zolang u een verwijzing naar het zelfde `ABRControlParametersBuilder` geval handhaaft.

Deze klasse bevat ook de `toABRControlParameters()` helpermethode. Gebruik deze methode om een instantie van op te halen `ABRControlParameters` en in te stellen op de `mediaPlayer.ABRControlParameters` eigenschap. Hierdoor worden uw instellingen van kracht in de speler.

1. Instantieer de `ABRControlParametersBuilder` hulpklasse, en plaats de parameters op de Speler van Media.

   >[!NOTE]
   >
   >In het volgende voorbeeld worden alle parameters bijvoorbeeld geïnitialiseerd naar de standaardwaarden en wordt alleen het beleid ingesteld op conservatief. De maximale bitsnelheid wordt beperkt tot 1000000:
   >
   >
   ```
   >var abrBuilder:ABRControlParametersBuilder =  
   >   new ABRControlParametersBuilder(); 
   >abrBuilder.policy = ABRControlParameters.CONSERVATIVE_POLICY; 
   >abrBuilder.maxBitRate = 1000000; 
   >mediaPlayer.abrControlParameters =  
   >   abrBuilder.toABRControlParameters();
   >```

1. Pas individuele parameters ABR bij runtime aan.

   Om individuele parameters te wijzigen terwijl het verlaten van de rest parameters zoals zij waren:

   ```
   // If later you want to reset the max bit rate to 2000000 
   abrBuilder.maxBitRate = 2000000; 
   mediaPlayer.abrControlParameters =  
     abrBuilder.toABRControlParameters();
   ```

   Als u de vorige instellingen wilt behouden, moet u een verwijzing behouden naar dezelfde `ABRControlParametersBuilder` instantie die u in Stap 1 hebt gemaakt.

## Aangepaste bitsnelheden configureren met ABRControlParameters {#section_02161FD0A73F40ED9CAE17F9AF850483}

U kunt waarden voor ABR-besturingselementen alleen instellen met `ABRControlParameters`, maar u kunt op elk gewenst moment een nieuwe waarde maken.

Deze mogelijkheid om ABR-parameters in te stellen werd ondersteund vóór het bestaan van de `ABRControlParametersBuilder` klasse, maar deze mogelijkheid is nog steeds effectief voor het instellen van ABR-parameters tijdens de constructietijd. Als u echter individuele parameters wilt wijzigen na de constructie, moet u de `ABRControlParametersBuilder` klasse gebruiken.

De volgende voorwaarden zijn van toepassing op `ABRControlParameters`:

* U moet waarden opgeven voor alle parameters tijdens de constructietijd.
* U kunt afzonderlijke waarden niet wijzigen na de constructietijd.
* Als de parameters die u opgeeft buiten het toegestane bereik vallen, `ArgumentError` wordt een fout gegenereerd.

1. Bepaal aanvankelijke, minimum, en maximumbeetjetarieven.
1. Bepaal het beleid ABR:

   * `CONSERVATIVE_POLICY`
   * `MODERATE_POLICY`
   * `AGGRESSIVE_POLICY`

1. Stel de ABR-parameterwaarden in de `ABRControlParameters` constructor in en wijs deze toe aan de Media Player.

   ```
   mediaPlayer.abrControlParameters = new ABRControlParameters( 
       ABRControlParameters.CONSERVATIVE_POLICY, 
       0, // Initial bit rate 
       0, // Minimum bit rate 
       1000000 // Maximum bit rate 
   );
   ```

