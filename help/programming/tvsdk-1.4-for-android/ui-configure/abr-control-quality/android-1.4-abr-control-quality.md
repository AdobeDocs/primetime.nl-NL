---
description: HLS- en DASH-streams bieden verschillende bitsnelheidcoderingen (profielen) voor dezelfde korte videoprand. TVSDK kan het kwaliteitsniveau voor elke uitbarsting selecteren op basis van de beschikbare bandbreedte.
title: Adaptieve bitsnelheden (ABR) voor videokwaliteit
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 0%

---


# Overzicht {#adaptive-bit-rates-abr-for-video-quality-overview}

HLS- en DASH-streams bieden verschillende bitsnelheidcoderingen (profielen) voor dezelfde korte videoprand. TVSDK kan het kwaliteitsniveau voor elke uitbarsting selecteren op basis van de beschikbare bandbreedte.

TVSDK controleert constant het beetjetarief om ervoor te zorgen dat de inhoud bij de optimale beetjetarief voor de huidige netwerkverbinding wordt gespeeld.

U kunt het adaptieve beetje-tarief (ABR) omschakelingsbeleid en de aanvankelijke, minimum, en maximumbeetjetarieven voor een multibit-tarief (MBR) stroom plaatsen. TVSDK schakelt automatisch over naar de bitsnelheid die de beste afspeelervaring in de opgegeven configuratie biedt.

<table id="table_AF838E082235406AA359BF1C1A77F85F"> 
 <tbody> 
  <tr> 
   <td colname="col01"> Oorspronkelijke bitsnelheid </td> 
   <td colname="col2"> <p>De gewenste afspeelbitsnelheid (in bits per seconde) voor het eerste segment. Wanneer het afspelen begint, wordt het dichtstbijzijnde profiel, dat gelijk is aan of groter is dan de aanvankelijke bitsnelheid, gebruikt voor het eerste segment. </p> <p> Als een minimale bitsnelheid is gedefinieerd en de aanvankelijke bitsnelheid lager is dan de minimale bitsnelheid, selecteert TVSDK het profiel met de laagste bitsnelheid boven de minimale bitsnelheid. Als de aanvankelijke snelheid boven de maximumsnelheid ligt, kiest TVSDK de hoogste snelheid onder de maximumsnelheid. </p> <p>Als de aanvankelijke bitsnelheid nul of ongedefinieerd is, wordt de aanvankelijke bitsnelheid bepaald door het ABR-beleid. </p> <p><span class="codeph"> </span> getABRInitialBitRatereturns een geheelwaarde die het byte-per-secondeprofiel vertegenwoordigt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Minimale bitsnelheid </td> 
   <td colname="col2"> <p>Het laagste toegestane beetjetarief waaraan ABR kan schakelen. De omschakeling ABR negeert profielen met een beetjetarief dat lager is dan dit beetjetarief. </p> <p><span class="codeph"> </span> getABRMinBitRatereturns een geheel-getalwaarde die het beetjes-per-tweede profiel vertegenwoordigt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Maximale bitsnelheid </td> 
   <td colname="col2"> <p>Het hoogste toegestane beetjetarief waaraan ABR kan schakelen. De omschakeling ABR negeert profielen met een beetjetarief hoger dan dit beetjetarief. </p> <p><span class="codeph"> </span> getABRMaxBitRatereturns een geheel-getalwaarde die het beetjes-per-tweede profiel vertegenwoordigt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> ABR-switchbeleid </td> 
   <td colname="col2"> De schakelaars van de playback geleidelijk aan het hoogste beetje-tarief profiel wanneer mogelijk. U kunt het beleid voor omschakeling plaatsen ABR, die bepaalt hoe snel TVSDK tussen profielen schakelt. De standaardwaarde is <span class="codeph"> ABR_MODERATE</span>. <p>Wanneer TVSDK besluit over te schakelen naar een hogere bitsnelheid, selecteert de speler het ideale bitsnelheidprofiel om over te schakelen op basis van het huidige ABR-beleid: 
     <ul id="ul_AC9C99D84A3B4A8DBD1A05CC05DEE771"> 
      <li id="li_B79C0AA2CBFB42FF98A257CEC9C400BA"><span class="codeph"> ABR_CONSERVATIVE</span>: Schakelt over naar het profiel met de volgende hogere bitsnelheid wanneer de bandbreedte 50% hoger is dan de huidige bitsnelheid. </li> 
      <li id="li_38CC3A95D8634F359D0F7C273D0108C0"><span class="codeph"> ABR_MODERATE</span>: Schakelt over naar het volgende profiel met een hogere bitsnelheid wanneer de bandbreedte 20% hoger is dan de huidige bitsnelheid. </li> 
      <li id="li_E845C035420D4B3FB2B179F448F8CA85"><span class="codeph"> ABR_AGGRESSIVE</span>: Schakelt onmiddellijk naar het hoogste beetje-tarief profiel wanneer de bandbreedte hoger is dan het huidige beetjetarief. </li> 
     </ul> </p> <p>Als de aanvankelijke bitsnelheid nul is of niet is opgegeven, maar een beleid is opgegeven, begint het afspelen met het laagste bitsnelheidprofiel voor conservatief, het profiel dat zich het dichtst bij de mediane bitsnelheid van beschikbare profielen voor matig en het hoogste bitsnelheidprofiel voor agressief bevindt. </p> <p>Het beleid werkt in de beperkingen van de minimum en maximumbeetjetarieven, als deze tarieven worden gespecificeerd. </p> <p><span class="codeph"> </span> getABRPolicyretourneert de huidige instelling van het  <span class="codeph"> </span> ABRControlParametersenum: 
     <ul id="ul_bd4_5kb_cz"> 
      <li id="li_E7C118AF48994454B7B3C016913DE545"><span class="codeph"> ABR_CONSERVATIVE</span> </li> 
      <li id="li_0A90BB42786449629CE7DD3364B385EE"><span class="codeph"> ABR_MODERATE</span> </li> 
      <li id="li_AFEB9B2862F24A369CA90596184A2883"><span class="codeph"> ABR_AGGRESSIVE</span> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

Houd rekening met het volgende:

* Het uitvalmechanisme van TVSDK heeft mogelijk voorrang op uw instellingen, omdat TVSDK een continue afspeelervaring bevordert in plaats van strikt de hand te houden aan de controleparameters.
* Wanneer de bitsnelheid verandert, verzendt TVSDK `onProfileChanged` gebeurtenissen in `PlaybackEventListener`.

* U kunt de ABR-instellingen op elk gewenst moment wijzigen en de speler schakelt over naar het profiel dat het meest overeenkomt met de meest recente instellingen.

Als een stream bijvoorbeeld de volgende profielen heeft:

* 1: 300000
* 2: 700000
* 3: 1500000
* 4: 2400000
* 5: 4000000

Als u een bereik van 300000 tot 2000000 opgeeft, houdt TVSDK alleen rekening met de profielen 1, 2 en 3. Hierdoor kunnen toepassingen zich aanpassen aan verschillende netwerkvoorwaarden, zoals het schakelen van wifi naar 3G of naar verschillende apparaten, zoals een telefoon, tablet of desktopcomputer.

Als u ABR-besturingsparameters wilt instellen, stelt u de parameters in op de klasse `ABRControlParameter`.
