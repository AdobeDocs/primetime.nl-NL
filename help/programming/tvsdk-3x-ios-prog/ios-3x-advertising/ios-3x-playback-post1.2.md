---
description: Het gedrag van het afspelen van media wordt beïnvloed door zoeken, onderbreken en het opnemen van advertenties.
title: Standaardgedrag en aangepast afspeelgedrag met advertenties
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---


# Standaardgedrag en aangepast afspeelgedrag met advertenties {#default-and-customized-playback-behavior-with-ads}

Het gedrag van het afspelen van media wordt beïnvloed door zoeken, onderbreken en het opnemen van advertenties.

Gebruik `PTAdPolicySelector` om het standaardgedrag te overschrijven.

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
   <th colname="col1" class="entry"><b>Videoactiviteit</b></th> 
   <th colname="col2" class="entry"><b>Standaardgedragsbeleid voor TVSDK</b></th> 
   <th colname="col3" class="entry"><b>Aanpassing beschikbaar via PTAdPolicySelector</b></th>
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> Tijdens normaal afspelen wordt een advertentieeinde gevonden. </td> 
   <td colname="col2"></td> 
   <td colname="col3">Geef een ander beleid voor het advertentieeinde op met <span class="codeph"> selectPolicyForAdBreak</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Uw toepassing zoekt naar voorwaarts over en onderverdelingen in de hoofdinhoud. </td> 
   <td colname="col2"> Hiermee wordt het laatste niet-gecontroleerde ad-einde afgespeeld dat is overgeslagen en wordt het afspelen hervat op de gewenste zoekpositie wanneer het afspelen van het einde of de eindemarkeringen is voltooid. </td> 
   <td colname="col3">Selecteer met <span class="codeph"> selectAdBreaksToPlay</span> welk overgeslagen einde moet worden afgespeeld. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Uw toepassing zoekt achterwaarts over een of meerdere pagina's in de hoofdinhoud. </td> 
   <td colname="col2"> Hiermee gaat u naar de gewenste zoekpositie zonder dat er een advertentie wordt afgespeeld. </td> 
   <td colname="col3">Selecteer met <span class="codeph"> selectAdBreaksToPlay</span> welk overgeslagen einde moet worden afgespeeld.                      </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Uw toepassing zoekt verder in een advertentie-einde. </td> 
   <td colname="col2"> Hiermee wordt afgespeeld vanaf het begin van de advertentie waarin de zoekopdracht is beëindigd. </td> 
   <td colname="col3">Geef een ander advertentiebeleid op voor het advertentieeinde en voor de specifieke advertentie waar de zoekopdracht is beëindigd met <span class="codeph"> selectPolicyForSeekIntoAd</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Uw toepassing zoekt terug naar een advertentie-einde. </td> 
   <td colname="col2"> Hiermee wordt afgespeeld vanaf het begin van de advertentie waarin de zoekopdracht is beëindigd. </td> 
   <td colname="col3">Geef een ander advertentiebeleid op voor het advertentieeinde en voor de specifieke advertentie waarin de zoekactie is beëindigd met <span class="codeph"> selectPolicyForSeekIntoAd</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Uw toepassing zoekt voorwaarts of achterwaarts over gecontroleerde advertentie(s) naar de hoofdinhoud. </td> 
   <td colname="col2"> Als de laatste overgeslagen advertentie-onderbreking reeds is gecontroleerd, slaat aan gebruiker-geselecteerde vraagpositie over. </td> 
   <td colname="col3">Selecteer welke overgeslagen onderbrekingen om te spelen gebruikend <span class="codeph"> selectAdBreaksToPlay</span> en bepaal welke onderbrekingen reeds zijn gecontroleerd door <span class="codeph"> PTAdBreak.isWatched</span> te gebruiken. <p> <p>Belangrijk:  Standaard markeert TVSDK een advertentie-einde zoals onmiddellijk na het invoeren van de eerste advertentie in het ad-einde wordt gecontroleerd. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Uw toepassing zoekt voorwaarts of achteruit over een of meer advertenties en stapt af in een gecontroleerd advertentieeinde. </td> 
   <td colname="col2"> Hiermee slaat u het ad-einde over en zoekt u naar de positie direct na het ad-einde. </td> 
   <td colname="col3">Geef een ander advertentiebeleid op voor het advertentieeinde (met de gecontroleerde status ingesteld op true) en voor de specifieke advertentie waar de zoekopdracht is beëindigd met <span class="codeph"> selectPolicyForSeekIntoAd</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Uw toepassing zoekt voorwaarts over advertenties die met aangepaste advertentiemarkeringen zijn ingevoegd. </td> 
   <td colname="col2"> Hiermee gaat u naar de door de gebruiker geselecteerde zoekpositie. </td> 
   <td colname="col3"></td> 
  </tr> 
 </tbody> 
</table>