---
description: U kunt aangepaste tagnamen in TVSDK globaal configureren met de MediaPlayerItemConfig-klasse of op stream gebaseerd met de MediaPlayerItemConfig-klasse.
title: Methoden van de klasse Config voor tags
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---

# Methoden van de klasse Config voor tags{#config-class-methods-for-tags}

U kunt aangepaste tagnamen in TVSDK globaal configureren met de MediaPlayerItemConfig-klasse of op stream gebaseerd met de MediaPlayerItemConfig-klasse.

TVSDK past de algemene configuratie automatisch toe op elke mediastream waarvoor geen streamspecifieke configuratie is opgegeven.

Beide `PSDKConfig` en `MediaPlayerItemConfig` deze methoden beschikbaar maken voor het beheer van aangepaste tags:

<table id="table_B37A6C75270D47BC99258F2884AD6905"> 
 <tbody> 
  <tr> 
   <td colname="1"><b>Abonneren op specifieke aangepaste tags</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> public function get subscribeTags():Vector.&lt;String&gt;</span> </td> 
   <td colname="col2"> Hiermee wordt de huidige lijst met geabonneerde tags opgehaald. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> public function set subscribeTags():Vector.&lt;String&gt;</span> </td> 
   <td colname="col2">Hiermee stelt u de lijst met geabonneerde tags in die aan de toepassing worden blootgesteld. <p>Uw toepassing wordt ook automatisch geabonneerd op alle tags die via <span class="codeph"> adTags</span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="1"><b>De advertentietags aanpassen die worden gebruikt door de standaardopportuniteitsdetector </b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> public function get adTags():Vector.&lt;String&gt;</span> </td> 
   <td colname="col2"> Hiermee wordt de huidige lijst met advertentietags opgehaald. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> public function set adTags():Vector.&lt;String&gt;</span> </td> 
   <td colname="col2"> Hiermee stelt u de lijst met advertentietags in die door de standaardopportuniteitsgenerator wordt gebruikt. </td> 
  </tr> 
 </tbody> 
</table>

Houd rekening met het volgende:

* De settermethoden staan niet toe dat de tagparameter null-waarden bevat.

  Indien aangetroffen, genereert TVSDK een `IllegalArgumentException`.
* De naam van de aangepaste tag moet het voorvoegsel # bevatten.

  Bijvoorbeeld: `#EXT-X-ASSET` is een correcte aangepaste tagnaam, maar `EXT-X-ASSET` is onjuist.
* U kunt de configuratie niet wijzigen nadat de mediastream is geladen.
