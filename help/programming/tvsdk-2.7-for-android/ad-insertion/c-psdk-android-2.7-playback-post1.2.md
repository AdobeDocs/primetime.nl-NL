---
description: Het gedrag van het afspelen van media wordt beïnvloed door zoeken, pauzeren, vooruitspoelen of terugspoelen en door advertenties.
title: Standaardgedrag en aangepast afspeelgedrag met advertenties
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 0%

---

# Standaardgedrag en aangepast afspeelgedrag met advertenties{#default-and-customized-playback-behavior-with-ads}

Het gedrag van het afspelen van media wordt beïnvloed door zoeken, pauzeren, vooruitspoelen of terugspoelen en door advertenties.

Als u het standaardgedrag wilt overschrijven, gebruikt u `AdBreakPolicySelector` .

>[!IMPORTANT]
>
>TVSDK biedt geen manier om zoeken tijdens advertenties uit te schakelen. Adobe raadt u aan uw toepassing te configureren om zoeken tijdens advertenties uit te schakelen.

Hier volgt het afspeelgedrag voor live/lineaire inhoud:

* Als u het afspelen hervat na een pauze, wordt de inhoud afgespeeld die op het moment van de pauze is gebufferd.

  Als de hervattende positie zich nog in de playbackwaaier bevindt, zou de playback ononderbroken moeten zijn. Anders springt TVSDK naar het nieuwe live punt. U kunt ook een zoekbewerking uitvoeren en een ander afspeelpunt selecteren.
* TVSDK verhelpt advertenties tussen cues na de positie waarop de toepassing live wordt afgespeeld.

  Het afspelen begint nadat het eerste actiepunt is opgelost. De standaardwaarde voor het invoeren van live afspelen is het live punt van de client, maar u kunt een andere positie kiezen. Alle aanwijzingen vóór de eerste positie worden opgelost nadat de toepassing een zoekactie uitvoert in het DVR-venster.

In de volgende tabel wordt beschreven hoe met TVSDK advertenties en afbrekingen tijdens het afspelen worden verwerkt:

<table id="table_466538B1C2A646B89EB4F9AA111203BE"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Videoactiviteit </th> 
   <th colname="col2" class="entry"> Standaardgedragsbeleid voor TVSDK </th> 
   <th colname="col3" class="entry">Aanpassing beschikbaar via <span class="codeph"> AdBreakPolicySelector </span> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> Tijdens normaal afspelen wordt een advertentieeinde gevonden. </td> 
   <td colname="col2"> 
    <ul id="ul_10D2638676EA4ADDA718E61BD4FDC1D2"> 
     <li id="li_D5CC30F063934C738971E2E8AF00C137"> Hiermee speelt u voor live/lineair het ad-einde af, zelfs als het ad-einde al is gecontroleerd. </li> 
     <li id="li_D962C0938DA74186AE99D117E5A74E38">Voor VOD speelt u het advertentiescheiding af en markeert u het ad-einde zoals gecontroleerd. </li> 
    </ul> </td> 
   <td colname="col3">Geef een ander beleid voor het advertentiesonderbreking op door <span class="codeph"> selectPolicyForAdBreak</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Uw toepassing zoekt naar voorwaarts over en onderverdelingen in de hoofdinhoud. </td> 
   <td colname="col2"> Hiermee wordt het laatste niet-gecontroleerde ad-einde afgespeeld dat is overgeslagen en wordt het afspelen hervat op de gewenste zoekpositie wanneer het afspelen van het einde of de eindemarkeringen is voltooid. </td> 
   <td colname="col3">Selecteer welk overgeslagen einde te gebruiken te spelen <span class="codeph"> selectAdBreaksToPlay</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Uw toepassing zoekt achterwaarts over een of meerdere pagina's in de hoofdinhoud. </td> 
   <td colname="col2"> Hiermee gaat u naar de gewenste zoekpositie zonder dat er een advertentie wordt afgespeeld. </td> 
   <td colname="col3">Selecteer welk overgeslagen einde te gebruiken te spelen <span class="codeph"> selectAdBreaksToPlay</span>.                      </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Uw toepassing zoekt verder in een advertentie-einde. </td> 
   <td colname="col2"> Hiermee wordt afgespeeld vanaf het begin van de advertentie waarin de zoekopdracht is beëindigd. </td> 
   <td colname="col3">Geef een ander advertentiebeleid op voor het advertentieeinde en voor de specifieke advertentie waar de zoekactie is geëindigd met gebruik <span class="codeph"> selectPolicyForSeekIntoAd</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Uw toepassing zoekt terug naar een advertentie-einde. </td> 
   <td colname="col2"> Hiermee wordt afgespeeld vanaf het begin van de advertentie waarin de zoekopdracht is beëindigd. </td> 
   <td colname="col3">Geef een ander advertentiebeleid op voor het advertentieeinde en voor de specifieke advertentie waarin de zoekactie is beëindigd met het gebruik van <span class="codeph"> selectPolicyForSeekIntoAd</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Uw toepassing zoekt voorwaarts of achterwaarts over gecontroleerde advertentie(s) naar de hoofdinhoud. </td> 
   <td colname="col2"> Als de laatste overgeslagen advertentie-onderbreking reeds is gecontroleerd, slaat aan gebruiker-geselecteerde vraagpositie over. </td> 
   <td colname="col3">Selecteer welke overgeslagen onderbrekingen om te spelen gebruiken <span class="codeph"> selectAdBreaksToPlay</span> en bepalen welke onderbrekingen al zijn gecontroleerd met <span class="codeph"> AdBreak.isWatched</span> . <p>Belangrijk: TVSDK markeert standaard een advertentie-einde zoals onmiddellijk na het invoeren van de eerste advertentie in het ad-einde wordt gecontroleerd. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Uw toepassing zoekt voorwaarts of achteruit over een of meer advertenties en stapt af in een gecontroleerd advertentieeinde. </td> 
   <td colname="col2"> Hiermee slaat u het ad-einde over en zoekt u naar de positie direct na het ad-einde. </td> 
   <td colname="col3">Geef een ander advertentiebeleid op voor het ad-einde (met de status gecontroleerde op true) en voor de specifieke advertentie waar de zoekactie is beëindigd met het gebruik van <span class="codeph"> selectPolicyForSeekIntoAd</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Uw toepassing gaat truc-spel (wijze DVR) in. Afspeelsnelheid kan negatief (terugspoelen) of groter dan 1 (vooruitspoelen) zijn. </td> 
   <td colname="col2"> Hiermee slaat u alle advertenties over tijdens snel vooruit- of terugspoelen, speelt u het laatste einde dat is overgeslagen na het afspelen van de truc af en slaat u de door de gebruiker geselecteerde positie voor het afspelen van de truc over wanneer die onderbreking het afspelen beëindigt. </td> 
   <td colname="col3">Selecteer welke overgeslagen onderbrekingen worden afgespeeld nadat de truc eindigt met <span class="codeph"> selectAdBreaksToPlay</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Uw toepassing zoekt voorwaarts over advertenties die met aangepaste advertentiemarkeringen zijn ingevoegd. </td> 
   <td colname="col2"> Hiermee gaat u naar de door de gebruiker geselecteerde zoekpositie. </td> 
   <td colname="col3">Zie voor meer informatie <a href="../../tvsdk-2.7-for-android/content-playback-options/ui-configure/t-psdk-android-2.7-ui-seek-scrub-bar-display.md" format="dita" scope="local"> Een zoekbalk weergeven met de huidige afspeelpositie...</a> </td> 
  </tr> 
 </tbody> 
</table>
