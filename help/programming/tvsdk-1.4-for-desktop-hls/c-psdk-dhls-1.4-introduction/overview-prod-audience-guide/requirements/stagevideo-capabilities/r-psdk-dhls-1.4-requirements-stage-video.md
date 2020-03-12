---
description: Op apparaten die GPU-versnelling (hardware) ondersteunen, kunt u een flash.media.StageVideo-object gebruiken om video direct op het apparaat te verwerken.
seo-description: Op apparaten die GPU-versnelling (hardware) ondersteunen, kunt u een flash.media.StageVideo-object gebruiken om video direct op het apparaat te verwerken.
seo-title: Minimumvereisten voor StageVideo
title: Minimumvereisten voor StageVideo
uuid: 8916dbac-33e0-4efd-8105-9ddbc85f0a3f
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Minimumvereisten voor StageVideo{#stagevideo-minimum-requirements}

Op apparaten die GPU-versnelling (hardware) ondersteunen, kunt u een flash.media.StageVideo-object gebruiken om video direct op het apparaat te verwerken.

<!--<a id="section_64DDAA8DB215493E8A7CA6636819D350"></a>-->

Een combinatie van verschillende factoren bepaalt wanneer en hoe u kunt gebruiken `StageVideo`. In de volgende tabel wordt een momentopname gegeven van enkele vereisten en beperkingen die aan het gebruik van StageVideo zijn gekoppeld. Deze eisen en beperkingen kunnen worden gewijzigd.

<table id="table_882F4462A5AE47E28A60A39D112164A7"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Platform </th> 
   <th colname="col2" class="entry"> Windows en Mac OS </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> Flash Player </td> 
   <td colname="col2"> 
    <ul id="ul_s42_lm2_jp"> 
     <li id="li_308FA9EC206B437A9EE04C29F9480B73">Minstens Flash 10.1 of hoger </li> 
     <li id="li_5898EDB0D12A43389076BCC7F4A27A0A">Flash 15 en hoger voor de functie voor het terugzetten naar software </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1">Browsers en <span class="codeph"> Wmode</span> -instellingen </td> 
   <td colname="col2"> <p><b>In Flash 15</b>stelt u <span class="codeph"> wmode=opaque</span> in zodat u HTML-overlays kunt gebruiken. </p> <p>De volgende browsers ondersteunen momenteel geen hardwareversnelling: 
     <ul id="ul_frv_ykf_jp"> 
      <li id="li_3D407A61FEE042A9B85A6EFACA6D7719">Mozilla Firefox op Microsoft Windows </li> 
      <li id="li_39B85AC352564DA8B86EA826638F1F4B">Google Chrome voor 26 en elke versie van Chrome in Windows XP en Vista </li> 
      <li id="li_0042BA6070C849E6B7C4B4BF4333F712">Microsoft Internet Explorer (alle versies) </li> 
     </ul>Andere combinaties browser/OS kunnen de toegang tot hardwareversnelling verhinderen. In deze scenario's, valt <span class="codeph"> StageVideo</span> terug naar software met een negatieve invloed op prestaties. </p> <p><b>Als in Flash 14 en lager</b>hardwareversnelling niet door de browser wordt ondersteund, kan de Flash-speler rechtstreeks naar de GPU renderen, maar <span class="codeph"> wmode=direct</span> instellen om deze rendering in te schakelen. <p>Tip:  Mogelijk moeten GPU-stuurprogramma's die ouder zijn dan 2009 worden bijgewerkt, omdat deze stuurprogramma's mogelijk geen ondersteuning bieden voor hardwareversnelling. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Object NetStream </td> 
   <td colname="col2">De <span class="codeph"> gebeurtenis StageVideoEvent.RENDER_STATE</span> wordt alleen verzonden als u een <span class="codeph"> NetStream</span> -object aan het <span class="codeph"> StageVideo</span> -object koppelt. </td> 
  </tr> 
 </tbody> 
</table>

