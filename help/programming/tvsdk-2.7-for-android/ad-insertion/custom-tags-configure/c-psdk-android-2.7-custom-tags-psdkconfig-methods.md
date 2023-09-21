---
description: U kunt namen van aangepaste tags globaal configureren in TVSDK met de klasse MediaPlayerItemConfig.
title: Methoden van de klasse Config voor tags
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---

# Methoden van de klasse Config voor tags {#config-class-methods-for-tags}

U kunt namen van aangepaste tags globaal configureren in TVSDK met de klasse MediaPlayerItemConfig.

TVSDK past automatisch de globale configuratie op om het even welke media stroom toe die geen stroom-specifieke configuratie specificeert.

`MediaPlayerItemConfig` stelt deze methoden beschikbaar voor het beheer van aangepaste tags:

<table id="table_B37A6C75270D47BC99258F2884AD6905"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <b>Abonneren op specifieke aangepaste tags</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public final String[] getSubscribedTags </span> </td> 
   <td colname="col2"> <p>Hiermee wordt de huidige lijst met geabonneerde tags opgehaald. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public final void setSubscribedTags(String[] tags); </span> </td> 
   <td colname="col2"> <p>Hiermee stelt u de lijst met geabonneerde tags in die aan de toepassing worden blootgesteld. </p> <p>Uw toepassing wordt ook automatisch geabonneerd op alle tags die via <span class="codeph"> setAdTags </span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <b>De advertentietags aanpassen die worden gebruikt door de standaardopportuniteitsdetector</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public final String[] getAdTags; </span> </td> 
   <td colname="col2"> <p>Hiermee wordt de huidige lijst met advertentietags opgehaald. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public final void setAdTags(String[] tags); </span> </td> 
   <td colname="col2"> <p>Hiermee stelt u de lijst met advertentietags in die door de standaardopportuniteitsgenerator wordt gebruikt. </p> </td> 
  </tr> 
 </tbody> 
</table>

Houd rekening met het volgende:

* De settermethoden staan niet toe dat de tagparameter null-waarden bevat.

  Indien aangetroffen, genereert TVSDK een `IllegalArgumentException`.
* De aangepaste tagnaam moet de `#` voorvoegsel

  Bijvoorbeeld: `#EXT-X-ASSET` is een correcte aangepaste tagnaam, maar `EXT-X-ASSET` is onjuist.

* U kunt de configuratie niet wijzigen nadat de mediastream is geladen.
