---
description: Het gedrag van het afspelen van media wordt beïnvloed door zoeken, pauzeren, snel vooruitspoelen of terugspoelen (de modus voor het kunstspel) en het opnemen van reclame.
title: Standaardgedrag en aangepast afspeelgedrag met advertenties
exl-id: 56544683-28a3-4720-bfd8-946cb09880aa
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# Standaardgedrag en aangepast afspeelgedrag met advertenties{#default-and-customized-playback-behavior-with-ads}

Het gedrag van het afspelen van media wordt beïnvloed door zoeken, pauzeren, snel vooruitspoelen of terugspoelen (de modus voor het kunstspel) en het opnemen van reclame.

Als u het standaardgedrag wilt overschrijven, gebruikt u `AdBreakPolicySelector`.

>[!IMPORTANT]
>
>Browser-TVSDK biedt geen manier om zoeken tijdens advertenties uit te schakelen. Adobe raadt u aan uw toepassing te configureren om zoeken tijdens advertenties uit te schakelen.

In de volgende tabel wordt beschreven hoe in Browser-TVSDK advertenties en afbrekingen tijdens het afspelen worden verwerkt:

<table id="table_466538B1C2A646B89EB4F9AA111203BE"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Videoactiviteit </th> 
   <th colname="col2" class="entry"> Standaardgedragsbeleid voor TVSDK-browsers </th> 
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
   <td colname="col3">Geef een ander advertentiebeleid op voor het advertentieeinde en voor de specifieke advertentie waar de zoekactie is geëindigd door gebruik te maken van <span class="codeph"> selectPolicyForSeekIntoAd</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Uw toepassing zoekt terug naar een advertentie-einde. </td> 
   <td colname="col2"> Hiermee wordt afgespeeld vanaf het begin van de advertentie waarin de zoekopdracht is beëindigd. </td> 
   <td colname="col3">Geef een ander advertentiebeleid op voor het advertentieeinde en voor de specifieke advertentie waarin de zoekactie is beëindigd met het gebruik van <span class="codeph"> selectPolicyForSeekIntoAd</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Uw toepassing zoekt voorwaarts of achterwaarts over gecontroleerde advertentie(s) naar de hoofdinhoud. </td> 
   <td colname="col2"> Als de laatste overgeslagen advertentie-onderbreking reeds is gecontroleerd, slaat aan gebruiker-geselecteerde vraagpositie over. </td> 
   <td colname="col3">Selecteer welke overgeslagen onderbrekingen om te spelen gebruiken <span class="codeph"> selectAdBreaksToPlay</span> en bepalen welke onderbrekingen al zijn gecontroleerd met <span class="codeph"> isWatched</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Uw toepassing zoekt voorwaarts of achteruit over een of meer advertenties en stapt af in een gecontroleerd advertentieeinde. </td> 
   <td colname="col2"> Hiermee slaat u het ad-einde over en zoekt u naar de positie direct na het ad-einde. </td> 
   <td colname="col3">Geef een ander advertentiebeleid op voor het ad-einde (met de status gecontroleerde op true) en voor de specifieke advertentie waar de zoekactie is beëindigd met het gebruik van <span class="codeph"> selectPolicyForSeekIntoAd</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Uw toepassing zoekt voorwaarts over advertenties die met aangepaste advertentiemarkeringen zijn ingevoegd. </td> 
   <td colname="col2"> Hiermee gaat u naar de door de gebruiker geselecteerde zoekpositie. </td> 
   <td colname="col3">Zie voor meer informatie <a href="../../browser-tvsdk-2.4/content-playback-options-browser-tvsdk/ui-configure/t-psdk-browser-tvsdk-2.4-ui-seek-scrub-bar-display.md" format="dita" scope="local"> Handgreep zoeken bij gebruik van de zoekbalk</a> </td> 
  </tr> 
 </tbody> 
</table>

## Aangepaste advertenties instellen {#section_custom_ad_behaviors}

U kunt het voorkeursgedrag instellen in de fabriek voor advertentie-inhoud in `retrieveAdPolicySelectorCallbackFunc` methode. U kunt de `selectPolicyForAdBreak`, `selectWatchedPolicyForAdBreak`, `selectPolicyForSeekIntoAd`, en `selectAdBreaksToPlay` in de inhoudsfabriek om een beleid te selecteren.
