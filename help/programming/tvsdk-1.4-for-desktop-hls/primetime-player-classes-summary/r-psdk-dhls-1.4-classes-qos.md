---
description: Deze klassen bieden informatie die u helpt te bepalen hoe goed de speler presteert.
seo-description: Deze klassen bieden informatie die u helpt te bepalen hoe goed de speler presteert.
seo-title: QoS-klassen
title: QoS-klassen
uuid: c1192474-d183-4995-87ef-839699844b48
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# QoS-klassen {#qos-classes}

Deze klassen bieden informatie die u helpt te bepalen hoe goed de speler presteert.

Pakket: [com.adobe.mediacore.qos](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/qos/package-detail.html) Package: [com.adobe.mediacore.qos.metrics](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/qos/metrics/package-detail.html)

<table frame="all" colsep="1" rowsep="1" id="table_2893EFF9755149159A4F94E781C76B6E"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Naam </th> 
   <th colname="2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/qos/metrics/BufferingMetrics.html" format="html" scope="external"> BufferingMetrics</a></span> </td> 
   <td colname="2"> Verstrekt informatie over hoeveel tijd de speler besteedde terwijl het als buffer optreden voor en hoe vaak een als buffer optredende voor gebeurtenis voorkwam. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/qos/DeviceInformation.html" format="html" scope="external"> DeviceInformation</a></span> </td> 
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
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/qos/LoadInformation.html" format="html" scope="external"> LoadInformation</a></span> </td> 
   <td colname="2"> Bevat diverse informatie QoS over ladende diverse middelen (dossiers, manifest of playlist, fragmenten/segmenten, sporen, etc.). </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/qos/LoadInformationType.html" format="html" scope="external"> LoadInformationType</a></span> </td> 
   <td colname="2"> Opsommingsklasse die mogelijke waarden opsomt voor de eigenschap type van LoadInformation-objecten. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/qos/PlaybackInformation.html" format="html" scope="external"> Afspeelgegevens</a></span> </td> 
   <td colname="2"> Verstrekt informatie over hoe de playback uitvoert. Dit omvat de framesnelheid, de bitsnelheid van het profiel, de totale tijd die is besteed aan buffering, het aantal bufferpogingen, de tijd die het heeft geduurd om de eerste byte van het eerste videofragment op te halen, de tijd die het heeft geduurd om het eerste frame te renderen, de momenteel gebufferde lengte en de buffertijd. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/qos/metrics/PlaybackLoadMetrics.html" format="html" scope="external"> PlaybackLoadMetrics</a></span> </td> 
   <td colname="2"> Verstrekt informatie over hoeveel tijd het voor de media aan lading kostte, hoeveel het voor de speler kostte om het eerste kader terug te geven of, in het geval van een fout, om te ontbreken. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/qos/metrics/PlaybackMetrics.html" format="html" scope="external"> PlaybackMetrics</a></span> </td> 
   <td colname="2"> Verstrekt informatie over hoe het playback zich gedraagt. Hieronder vallen de framesnelheid, bitsnelheid, bufferlengte, enzovoort. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/qos/metrics/PlaybackSessionMetrics.html" format="html" scope="external"> PlaybackSessionMetrics</a></span> </td> 
   <td colname="2"> Verstrekt informatie over hoeveel seconden de speler terwijl eigenlijk het spelen en hoeveel tijd de video eigenlijk op het scherm was besteedde. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/qos/QOSProvider.html" format="html" scope="external"> QOSProvider</a></span> </td> 
   <td colname="2">
    <ph>
      Verstrekt essentiële metriek QoS voor zowel playback als het apparaat.
    </ph>
    <ph>
      QOS-informatieleveranciersklasse.
    </ph> </td> 
  </tr> 
 </tbody> 
</table>

