---
description: Het gedrag van het afspelen van media wordt beïnvloed door zoeken, onderbreken en het opnemen van advertenties.
title: Standaardgedrag en aangepast afspeelgedrag met advertenties
exl-id: bd92b58a-fc71-41de-a80e-19002d66246f
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# Standaardgedrag en aangepast afspeelgedrag met advertenties{#default-and-customized-playback-behavior-with-ads}

Het gedrag van het afspelen van media wordt beïnvloed door zoeken, onderbreken en het opnemen van advertenties.

Als u het standaardgedrag wilt overschrijven, gebruikt u `PTAdPolicySelector`.

>[!IMPORTANT]
>
>Voor VOD en live/lineair streamen kunnen tijdlijnaanpassingen niet worden herzien. Dit betekent dat een advertentie niet uit de tijdlijn kan worden verwijderd nadat deze is afgespeeld. Als de gebruiker terug zoekt, speelt de zelfde advertentie opnieuw zelfs als het normale beleid zou geweest zijn om het te verwijderen.

>[!IMPORTANT]
>
>TVSDK biedt geen manier om zoeken tijdens advertenties uit te schakelen. Adobe raadt u aan uw toepassing te configureren om zoeken tijdens advertenties uit te schakelen.

In de volgende tabel wordt beschreven hoe met TVSDK advertenties en afbrekingen tijdens het afspelen worden verwerkt:

<table id="table_466538B1C2A646B89EB4F9AA111203BE"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Videoactiviteit </th> 
   <th colname="col2" class="entry"> Standaardgedragsbeleid voor TVSDK </th> 
   <th colname="col3" class="entry">Aanpassing beschikbaar via <span class="codeph"> PTAdPolicySelector</span> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> Tijdens normaal afspelen wordt een advertentieeinde gevonden. </td> 
   <td colname="col2"></td> 
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
   <td colname="col3">Selecteer welke overgeslagen onderbrekingen om te spelen gebruiken <span class="codeph"> selectAdBreaksToPlay</span> en bepalen welke onderbrekingen al zijn gecontroleerd met <span class="codeph"> PTAdBreak.isWatched</span>. <p> <p>Belangrijk: Standaard markeert TVSDK een advertentie-einde zoals onmiddellijk na het invoeren van de eerste advertentie in het ad-einde wordt gecontroleerd. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Uw toepassing zoekt voorwaarts of achteruit over een of meer advertenties en stapt af in een gecontroleerd advertentieeinde. </td> 
   <td colname="col2"> Hiermee slaat u het ad-einde over en zoekt u naar de positie direct na het ad-einde. </td> 
   <td colname="col3">Geef een ander advertentiebeleid op voor het ad-einde (met de status gecontroleerde op true) en voor de specifieke advertentie waar de zoekactie is beëindigd met het gebruik van <span class="codeph"> selectPolicyForSeekIntoAd</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Uw toepassing zoekt voorwaarts over advertenties die met aangepaste advertentiemarkeringen zijn ingevoegd. </td> 
   <td colname="col2"> Hiermee gaat u naar de door de gebruiker geselecteerde zoekpositie. </td> 
   <td colname="col3"></td> 
  </tr> 
 </tbody> 
</table>
