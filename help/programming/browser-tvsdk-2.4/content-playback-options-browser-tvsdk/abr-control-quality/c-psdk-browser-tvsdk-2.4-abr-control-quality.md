---
description: HLS- en DASH-streams bieden verschillende bitsnelheidcoderingen (profielen) voor dezelfde korte videoprand. Browser TVSDK kan het kwaliteitsniveau voor elke uitbarsting selecteren op basis van de beschikbare bandbreedte.
seo-description: HLS- en DASH-streams bieden verschillende bitsnelheidcoderingen (profielen) voor dezelfde korte videoprand. Browser TVSDK kan het kwaliteitsniveau voor elke uitbarsting selecteren op basis van de beschikbare bandbreedte.
seo-title: Adaptieve bitsnelheden (ABR) voor videokwaliteit
title: Adaptieve bitsnelheden (ABR) voor videokwaliteit
uuid: 4c34fb7b-1bbd-4fa9-8929-d50e85a17396
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Overzicht {#adaptive-bit-rates-abr-for-video-quality-overview}

HLS- en DASH-streams bieden verschillende bitsnelheidcoderingen (profielen) voor dezelfde korte videoprand. Browser TVSDK kan het kwaliteitsniveau voor elke uitbarsting selecteren op basis van de beschikbare bandbreedte.

Browser TVSDK controleert constant het beetjetarief om ervoor te zorgen dat de inhoud bij de optimale beetjetarief voor de huidige netwerkverbinding wordt gespeeld.

U kunt het adaptieve beetje-tarief (ABR) omschakelingsbeleid en de aanvankelijke, minimum, en maximumbeetjetarieven voor een multibit-tarief (MBR) stroom plaatsen. Browser TVSDK schakelt automatisch over naar de bitsnelheid die de beste afspeelervaring in de opgegeven configuratie biedt.

<table id="table_AF838E082235406AA359BF1C1A77F85F"> 
 <tbody> 
  <tr> 
   <td colname="col01"> Oorspronkelijke bitsnelheid </td> 
   <td colname="col2">De gewenste afspeelbitsnelheid (in bits per seconde) voor het eerste segment. Wanneer het afspelen begint, wordt het dichtstbijzijnde profiel, dat gelijk is aan of groter is dan de aanvankelijke bitsnelheid, gebruikt voor het eerste segment. <p> Als een minimale bitsnelheid is gedefinieerd en de aanvankelijke bitsnelheid lager is dan de minimale bitsnelheid, selecteert Browser-TVSDK het profiel met de laagste bitsnelheid boven de minimale bitsnelheid. Als de aanvankelijke snelheid boven de maximumsnelheid ligt, selecteert Browser TVSDK de hoogste snelheid onder de maximumsnelheid. </p> <p>Als de aanvankelijke bitsnelheid nul of ongedefinieerd is, wordt de aanvankelijke bitsnelheid bepaald door het ABR-beleid. </p> <p><span class="codeph"> initialBitRate</span> retourneert een geheel-getalwaarde die het byte-per-seconde-profiel vertegenwoordigt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Minimale bitsnelheid </td> 
   <td colname="col2">Het laagste toegestane beetjetarief waaraan ABR kan schakelen. De omschakeling ABR negeert profielen met een beetjetarief dat lager is dan dit beetjetarief. <p><span class="codeph"> minBitRate</span> retourneert een geheel getal dat het bits-per-seconde-profiel vertegenwoordigt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Maximale bitsnelheid </td> 
   <td colname="col2">Het hoogste toegestane beetjetarief waaraan ABR kan schakelen. De omschakeling ABR negeert profielen met een beetjetarief hoger dan dit beetjetarief. <p><span class="codeph"> maxBitRate</span> retourneert een geheel getal dat het bits-per-seconde-profiel vertegenwoordigt. </p> </td> 
  </tr> 
 </tbody> 
</table>

Houd rekening met het volgende:

* Wanneer de bitsnelheid verandert, verzendt Browser-TVSDK `AdobePSDK.ProfileEvent` het type als `AdobePSDK.PSDKEventType.PROFILE_CHANGED`.

* U kunt de ABR-instellingen op elk gewenst moment wijzigen en de speler schakelt over naar het profiel dat het meest overeenkomt met de meest recente instellingen.

Als een stream bijvoorbeeld de volgende profielen heeft:

* 1: 300000
* 2: 700000
* 3: 1500000
* 4: 2400000
* 5: 4000000

Als u een bereik van 300000 tot 2000000 opgeeft, beschouwt Browser-TVSDK alleen de profielen 1, 2 en 3. Hierdoor kunnen toepassingen zich aanpassen aan verschillende netwerkvoorwaarden, zoals het schakelen van wifi naar 3G of naar verschillende apparaten, zoals een telefoon, tablet of desktopcomputer.

ABR-controleparameters instellen:

* Stel de parameters voor de `ABRControlParameters` klasse in.

