---
description: U kunt namen van aangepaste tags globaal configureren in TVSDK met de klasse MediaPlayerItemConfig.
seo-description: U kunt namen van aangepaste tags globaal configureren in TVSDK met de klasse MediaPlayerItemConfig.
seo-title: Methoden van de klasse Config voor tags
title: Methoden van de klasse Config voor tags
uuid: 64284876-1f31-47e0-a99b-3bfe17e10707
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

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
   <td colname="col2"> <p>Hiermee stelt u de lijst met geabonneerde tags in die aan de toepassing worden blootgesteld. </p> <p>Uw toepassing wordt ook automatisch geabonneerd op alle tags die via <span class="codeph"> setAdTags worden verzonden </span>. </p> </td> 
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
* De aangepaste tagnaam moet het `#` voorvoegsel bevatten.

   De aangepaste tagnaam `#EXT-X-ASSET` is bijvoorbeeld correct, maar `EXT-X-ASSET` is onjuist.

* U kunt de configuratie niet wijzigen nadat de mediastream is geladen.
