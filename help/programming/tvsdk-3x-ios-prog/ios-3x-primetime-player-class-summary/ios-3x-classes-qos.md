---
description: Deze klassen bieden informatie die u helpt te bepalen hoe goed de speler presteert.
title: QoS-klassen
exl-id: ecbeddc6-b5f3-4ee1-a22c-5beec42df5ab
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# QoS-klassen {#qos-classes}

Deze klassen bieden informatie die u helpt te bepalen hoe goed de speler presteert.

<table frame="all" colsep="1" rowsep="1" id="table_2893EFF9755149159A4F94E781C76B6E"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"><b>Naam</b></th> 
   <th colname="2" class="entry"><b>Beschrijving</b></th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTDeviceInformation.html" format="html" scope="external"> PTDeviceInformation</a> </td> 
   <td colname="2">Verstrekt informatie over het platform en het werkende systeem waarop TVSDK loopt: 
    <ul id="ul_0DE69F3B38E84964AB98DCCD11E5E123"> 
     <li id="li_19B2D1889FCA4B0F8FCB0EE8F87353B2">Versie van het besturingssysteem van het platform </li> 
     <li id="li_CA35F4A48FD34555AC7D7832D5997AD4">Versienummer van de TVSDK-bibliotheek </li> 
     <li id="li_30D38320C2A3440E92C0A477FFFBF9A0">Modelnaam van apparaat </li> 
     <li id="li_2D15164B987E405685B96A900EBF041D">Naam van fabrikant van apparaat </li> 
     <li id="li_B78485CB9580444DB9694404706BA191">Device UUID </li> 
     <li id="li_841EA77499B44F0692192F9DE1A798E4">Breedte/hoogte van het apparaatscherm </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTPlaybackInformation.html" format="html" scope="external"> PTPlaybackInformation</a> </td> 
   <td colname="2"> Verstrekt informatie over hoe de playback uitvoert. Dit omvat de framesnelheid, de bitsnelheid van het profiel, de totale tijd die is besteed aan buffering, het aantal bufferpogingen, de tijd die het heeft geduurd om de eerste byte van het eerste videofragment op te halen, de tijd die het heeft geduurd om het eerste frame te renderen, de momenteel gebufferde lengte en de buffertijd. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTQoSProvider.html" format="html" scope="external"> PTQoSProvider</a> </td> 
   <td colname="2">
    <pre>
      Verstrekt essentiële metriek QoS voor zowel playback als het apparaat.
    </pre>
    <pre>
      QOS-informatieleveranciersklasse.
    </pre> </td> 
  </tr> 
 </tbody> 
</table>
