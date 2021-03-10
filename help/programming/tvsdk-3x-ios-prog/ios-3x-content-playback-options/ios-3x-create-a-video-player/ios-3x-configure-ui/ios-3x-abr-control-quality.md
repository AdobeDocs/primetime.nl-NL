---
description: HLS- en DASH-streams bieden verschillende bitsnelheidcoderingen (profielen) voor dezelfde korte videoprand. TVSDK kan het kwaliteitsniveau voor elke uitbarsting selecteren op basis van de beschikbare bandbreedte.
title: Adaptieve bitsnelheden (ABR) voor videokwaliteit
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 0%

---


# Adaptieve bitsnelheden (ABR) voor videokwaliteit {#adaptive-bit-rates-abr-for-video-quality}

HLS- en DASH-streams bieden verschillende bitsnelheidcoderingen (profielen) voor dezelfde korte videoprand. TVSDK kan het kwaliteitsniveau voor elke uitbarsting selecteren op basis van de beschikbare bandbreedte.

TVSDK controleert constant het beetjetarief om ervoor te zorgen dat de inhoud bij de optimale beetjetarief voor de huidige netwerkverbinding wordt gespeeld.

U kunt het adaptieve beetje-tarief (ABR) omschakelingsbeleid en de aanvankelijke, minimum, en maximumbeetjetarieven voor een multibit-tarief (MBR) stroom plaatsen. TVSDK schakelt automatisch over naar de bitsnelheid die de beste afspeelervaring in de opgegeven configuratie biedt.

<table id="table_AF838E082235406AA359BF1C1A77F85F"> 
 <tbody> 
  <tr> 
   <td colname="col01"> Oorspronkelijke bitsnelheid </td> 
   <td colname="col2"> <p>De gewenste afspeelbitsnelheid (in bits per seconde) voor het eerste segment. Wanneer het afspelen begint, wordt het dichtstbijzijnde profiel, dat gelijk is aan of groter is dan de aanvankelijke bitsnelheid, gebruikt voor het eerste segment. </p> <p> Als een minimale bitsnelheid is gedefinieerd en de aanvankelijke bitsnelheid lager is dan de minimale bitsnelheid, selecteert TVSDK het profiel met de laagste bitsnelheid boven de minimale bitsnelheid. Als de aanvankelijke snelheid boven de maximumsnelheid ligt, kiest TVSDK de hoogste snelheid onder de maximumsnelheid. </p> <p>Als de aanvankelijke bitsnelheid nul of ongedefinieerd is, wordt de aanvankelijke bitsnelheid bepaald door het ABR-beleid. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Minimale bitsnelheid </td> 
   <td colname="col2"> <p>Het laagste toegestane beetjetarief waaraan ABR kan schakelen. De omschakeling ABR negeert profielen met een beetjetarief dat lager is dan dit beetjetarief. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Maximale bitsnelheid </td> 
   <td colname="col2"> <p>Het hoogste toegestane beetjetarief waaraan ABR kan schakelen. De omschakeling ABR negeert profielen met een beetjetarief hoger dan dit beetjetarief. </p> </td> 
  </tr> 
 </tbody> 
</table>

Houd rekening met het volgende:

* TVSDK verzendt geen gebeurtenissen van het schakelen van bitsnelheid.
* U kunt de ABR-instellingen op elk gewenst moment wijzigen en de speler schakelt over naar het profiel dat het meest overeenkomt met de meest recente instellingen.

Als een stream bijvoorbeeld de volgende profielen heeft:

* 1: 300000
* 2: 700000
* 3: 1500000
* 4: 2400000
* 5: 4000000

Als u een bereik van 300000 tot 2000000 opgeeft, houdt TVSDK alleen rekening met de profielen 1, 2 en 3. Hierdoor kunnen toepassingen zich aanpassen aan verschillende netwerkvoorwaarden, zoals het schakelen van WiFi naar 3G of naar verschillende apparaten, zoals een telefoon, tablet of desktopcomputer.

## Aangepaste bitsnelheden {#section_572FCE4CC28D4DF8BD9C461F00B3CA17} configureren

Aangepaste parameters voor de bitsnelheid van TVSDK configureren:

1. Vorm een geval van `PTABRControlParameters` om de aanvankelijke, minimum, en maximum beetje-tarief montages te plaatsen.

   De standaardwaarden worden weergegeven in het volgende codefragment, maar uw toepassing kan voor elk van deze parameters een geheel-getalwaarde instellen.

   >[!IMPORTANT]
   >
   >Geef de bitsnelheidinstellingen op in bits per seconde (bps).

   ```
   // ARC (add autorelease for non-ARC) 
   PTABRControlParameters *abrMetaData =  
       [[PTABRControlParameters alloc] init];  
   
   abrMetaData.initialBitRate = -1; 
   abrMetaData.minBitRate = 0; 
   abrMetaData.maxBitRate = INT_MAX;
   ```

1. Werk uw `PTMediaPlayer` instantie met de gevormde `PTABRControlParameters` instantie bij.

   ```
   // assuming self.player is the PTMediaPlayer instance 
   self.player.abrControlParameters = abrMetaData;
   ```

Houd rekening met het volgende:

* De toepassing moet de eigenschap `abrControlParameters` op `PTMediaPlayer` instellen voordat een instantie `PTMediaPlayerItem` wordt geconfigureerd, zodat de initiële en minimale bitsnelheidinstellingen van kracht worden.

   Nadat het afspelen van inhoud is gestart, heeft het instellen van een nieuwe instantie alleen invloed op de instelling van de maximale bitsnelheid.

* Als u de maximale bitsnelheid tijdens het afspelen wilt bijwerken, maakt u een nieuwe `PTABRControlParameters`-instantie en stelt u deze in op de spelerinstantie.
* U kunt de instelling voor de maximale bitsnelheid alleen bijwerken tijdens het afspelen op iOS 8.0 en hoger. Voor eerdere versies wordt de waarde `maxBitrate` gebruikt die was ingesteld voordat de inhoud werd afgespeeld.