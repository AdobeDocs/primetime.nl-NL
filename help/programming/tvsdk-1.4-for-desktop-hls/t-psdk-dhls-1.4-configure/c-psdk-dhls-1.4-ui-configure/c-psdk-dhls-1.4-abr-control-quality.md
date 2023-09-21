---
description: HLS- en DASH-streams bieden verschillende bitsnelheidcoderingen (profielen) voor dezelfde korte videoprand. TVSDK kan het kwaliteitsniveau voor elke uitbarsting selecteren op basis van de beschikbare bandbreedte.
title: Adaptieve bitsnelheden (ABR) voor videokwaliteit
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '973'
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
   <td colname="col2"> <p>De gewenste afspeelbitsnelheid (in bits per seconde) voor het eerste segment. Wanneer het afspelen begint, wordt het dichtstbijzijnde profiel, dat gelijk is aan of groter is dan de aanvankelijke bitsnelheid, gebruikt voor het eerste segment. </p> <p> Als een minimale bitsnelheid is gedefinieerd en de aanvankelijke bitsnelheid lager is dan de minimale bitsnelheid, selecteert TVSDK het profiel met de laagste bitsnelheid boven de minimale bitsnelheid. Als de aanvankelijke snelheid boven de maximumsnelheid ligt, kiest TVSDK de hoogste snelheid onder de maximumsnelheid. </p> <p>Als de aanvankelijke bitsnelheid nul of ongedefinieerd is, wordt de aanvankelijke bitsnelheid bepaald door het ABR-beleid. </p> <p> <span class="apiname"> ABRInitialBitRate </span> Hiermee wordt een geheel getal geretourneerd dat het byte-per-seconde-profiel vertegenwoordigt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Minimale bitsnelheid </td> 
   <td colname="col2"> <p>Het laagste toegestane beetjetarief waaraan ABR kan schakelen. De omschakeling ABR negeert profielen met een beetjetarief dat lager is dan dit beetjetarief. </p> <p> <span class="apiname"> ABRMinBitRate </span> Hiermee wordt een geheel-getalwaarde geretourneerd die het bits-per-seconde-profiel vertegenwoordigt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Maximale bitsnelheid </td> 
   <td colname="col2"> <p>Het hoogste toegestane beetjetarief waaraan ABR kan schakelen. De omschakeling ABR negeert profielen met een beetjetarief hoger dan dit beetjetarief. </p> <p> <span class="apiname"> ABRMaxBitRate </span> Hiermee wordt een geheel-getalwaarde geretourneerd die het bits-per-seconde-profiel vertegenwoordigt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> ABR-switchbeleid </td> 
   <td colname="col2"> De schakelaars van de playback geleidelijk aan het hoogste beetje-tarief profiel wanneer mogelijk. U kunt het beleid voor omschakeling plaatsen ABR, die bepaalt hoe snel TVSDK tussen profielen schakelt. De standaardwaarde is <span class="codeph"> MODERATE_POLICY </span>. <p>Wanneer TVSDK besluit over te schakelen naar een hogere bitsnelheid, selecteert de speler het ideale bitsnelheidprofiel om over te schakelen op basis van het huidige ABR-beleid: 
     <ul id="ul_058D0FFC944C476A83BB9E756B95DEBD"> 
      <li id="li_C690A12DC34C4754B01C2D0616FB6A0A"> <span class="codeph"> CONSERVATIVE_POLICY </span>: Schakelt over naar het profiel met de volgende hogere bitsnelheid wanneer de bandbreedte 50% hoger is dan de huidige bitsnelheid. </li> 
      <li id="li_FF5BDB099B554940AC296938C7A12B81"> <span class="codeph"> MODERATE_POLICY </span>: schakelt naar het volgende hogere bitsnelheidprofiel wanneer de bandbreedte 20% hoger is dan de huidige bitsnelheid. </li> 
      <li id="li_E602508429864C279BF78360E95718A6"> <span class="codeph"> AGRESSIVE_POLICY </span>: schakelt onmiddellijk naar het hoogste bitsnelheidprofiel wanneer de bandbreedte hoger is dan de huidige bitsnelheid. </li> 
     </ul> </p> <p>Als de aanvankelijke bitsnelheid nul is of niet is opgegeven, maar een beleid is opgegeven, begint het afspelen met het laagste bitsnelheidprofiel voor conservatief, het profiel dat zich het dichtst bij de mediane bitsnelheid van beschikbare profielen voor matig en het hoogste bitsnelheidprofiel voor agressief bevindt. </p> <p>Het beleid werkt in de beperkingen van de minimum en maximumbeetjetarieven, als deze tarieven worden gespecificeerd. </p> <p> <span class="codeph"> ABRPopolicy </span> retourneert de huidige instelling van het dialoogvenster <span class="codeph"> ABRControlParameters </span> enum: CONSERVATIVE_POLICY, MODERATE_POLICY, of AGGRESSIVE_POLICY. </p> </td> 
  </tr> 
 </tbody> 
</table>

Houd rekening met het volgende:

* Het uitvalmechanisme van TVSDK heeft mogelijk voorrang op uw instellingen, omdat TVSDK een continue afspeelervaring bevordert in plaats van strikt de hand te houden aan de controleparameters.
* Wanneer de bitsnelheid verandert, verzendt TVSDK `ProfileEvent.PROFILE_CHANGED`.
* U kunt de ABR-instellingen op elk gewenst moment wijzigen en de speler schakelt over naar het profiel dat het meest overeenkomt met de meest recente instellingen.

Als een stream bijvoorbeeld de volgende profielen heeft:

* 1: 300000
* 2: 700000
* 3: 1500000
* 4: 2400000
* 5: 4000000

Als u een bereik van 300000 tot 2000000 opgeeft, houdt TVSDK alleen rekening met de profielen 1, 2 en 3. Hierdoor kunnen toepassingen zich aanpassen aan verschillende netwerkvoorwaarden, zoals het schakelen van wifi naar 3G of naar verschillende apparaten, zoals een telefoon, tablet of desktopcomputer.

Voer een van de volgende handelingen uit om ABR-besturingsparameters in te stellen:

* Gebruik de `ABRControlParameterBuilder` helperklasse om het even welke ondergroep van de parameters te plaatsen (werkt op `ABRControlParameter` achter de schermen)

* Stel de parameters in op de knop `ABRControlParameter` klasse.

## Aangepaste bitsnelheden configureren met ABRControlParametersBuilder {#section_3DDE397A7CE445E1832EBAA46CE5C069}

Met de `ABRControlParametersBuilder` helperklasse is de eenvoudigste, meest efficiënte manier om parameters ABR te plaatsen.

* De `ABRControlParametersBuilder` constructor stelt alle ABR-parameters in op standaardwaarden voor de onderliggende waarde `ABRControlParameters` object.

* U kunt individuele parameters ABR tijdens runtime terugstellen zolang u een verwijzing naar het zelfde handhaaft `ABRControlParametersBuilder` -instantie.

Deze klasse bevat ook de klasse `toABRControlParameters()` helpermethode. Gebruik deze methode om een instantie van `ABRControlParameters` en zet deze in op de `mediaPlayer.ABRControlParameters` eigenschap. Hierdoor worden uw instellingen van kracht in de speler.

1. Instantiëren van de `ABRControlParametersBuilder` hulpklasse, en de parameters op de Speler van Media plaatsen.

   >[!NOTE]
   >
   >In het volgende voorbeeld worden alle parameters bijvoorbeeld geïnitialiseerd naar de standaardwaarden en wordt alleen het beleid ingesteld op conservatief. De maximale bitsnelheid wordt beperkt tot 1000000:
   >
   >```
   >var abrBuilder:ABRControlParametersBuilder =  
   >   new ABRControlParametersBuilder(); 
   >abrBuilder.policy = ABRControlParameters.CONSERVATIVE_POLICY; 
   >abrBuilder.maxBitRate = 1000000; 
   >mediaPlayer.abrControlParameters =  
   >   abrBuilder.toABRControlParameters();
   >```
   >

1. Pas individuele parameters ABR bij runtime aan.

   Om individuele parameters te wijzigen terwijl het verlaten van de rest parameters zoals zij waren:

   ```
   // If later you want to reset the max bit rate to 2000000 
   abrBuilder.maxBitRate = 2000000; 
   mediaPlayer.abrControlParameters =  
     abrBuilder.toABRControlParameters();
   ```

   Als u de vorige instellingen wilt behouden, moet u een verwijzing naar dezelfde instellingen behouden `ABRControlParametersBuilder` -instantie die u hebt gemaakt in Stap 1.

## Aangepaste bitsnelheden configureren met behulp van ABRControlParameters {#section_02161FD0A73F40ED9CAE17F9AF850483}

U kunt waarden voor ABR-besturingselementen alleen instellen met `ABRControlParameters`, maar u kunt op elk gewenst moment een nieuwe maken.

Deze mogelijkheid om ABR-parameters in te stellen, werd ondersteund voordat het `ABRControlParametersBuilder` -klasse, maar deze mogelijkheid is nog steeds effectief voor het instellen van ABR-parameters tijdens de constructieperiode. Als u echter individuele parameters wilt wijzigen na de constructie, moet u de opdracht `ABRControlParametersBuilder` klasse.

Voor `ABRControlParameters`:

* U moet waarden opgeven voor alle parameters tijdens de constructietijd.
* U kunt afzonderlijke waarden niet wijzigen na de constructietijd.
* Als de parameters die u opgeeft, zich buiten het toegestane bereik bevinden, `ArgumentError` wordt gegenereerd.

1. Bepaal aanvankelijke, minimum, en maximumbeetjetarieven.
1. Bepaal het beleid ABR:

   * `CONSERVATIVE_POLICY`
   * `MODERATE_POLICY`
   * `AGGRESSIVE_POLICY`

1. De ABR-parameterwaarden instellen in het dialoogvenster `ABRControlParameters` en deze aan de Media Player toewijzen.

   ```
   mediaPlayer.abrControlParameters = new ABRControlParameters( 
       ABRControlParameters.CONSERVATIVE_POLICY, 
       0, // Initial bit rate 
       0, // Minimum bit rate 
       1000000 // Maximum bit rate 
   );
   ```
