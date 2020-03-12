---
description: TVSDK heeft specifieke vereisten voor media-inhoud, manifestinhoud, DRM en softwareversies.
seo-description: TVSDK heeft specifieke vereisten voor media-inhoud, manifestinhoud, DRM en softwareversies.
seo-title: Vereisten
title: Vereisten
uuid: 06e61b9f-cda2-4813-8da4-fb3e0d88ad35
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Vereisten {#requirements}

TVSDK vereist specifieke eigenschappen voor media-inhoud, manifestinhoud, DRM en softwareversies.

## Systeem- en softwarevereisten {#section_96E5B079900246E78682AE44D3F23068}

Als u TVSDK wilt gebruiken, dient u ervoor te zorgen dat uw hardware-, besturingssysteem- en toepassingsversies allemaal voldoen aan de onderstaande minimale vereisten.

| Besturingssysteem | iOS 7.0 of hoger |
|---|---|
| Xcode | Xcode 10 voor iOS 12 en Xcode 9 voor iOS 11 |

## Inhoud- en manifestvereisten {#section_72DD0E4DA9774DCCADB42887497F1386}

Controleer de beperkingen en vereisten voor streams en afspeellijsten (manifests), inclusief DRM-coderingssleutels.

| Keyframes van inhoudssegmenten | Elk inhoudssegment moet beginnen met een keyframe. |
|---|---|
| Volgnummers in live/lineaire video | Moet op elk gewenst moment overeenkomen met alle bitsnelheidsuitvoeringen voor de hoofdinhoud. |

## EXT-X-VERSION-vereisten {#section_C03D3DCE1D244E26BBD2C1D7144FDFBD}

De versie van `#EXT-X-VERSION` het [!DNL .m3u8] manifestbestand bepaalt welke functies beschikbaar zijn voor uw toepassing en welke `EXT` labels geldig zijn.

Hier is wat informatie over de `#EXT-X-VERSION` markering, die de het protocolversie van HLS specificeert:

* De versie moet overeenkomen met de functies en kenmerken in de HLS-afspeellijst. anders kunnen er afspeelfouten optreden. Zie de [HTTP Live Streaming-specificatie](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1)voor meer informatie.
* Adobe raadt u aan ten minste versie 2 van HLS te gebruiken voor afspelen in op TVSDK gebaseerde clients.

   De cliënten en de servers moeten de versies op de volgende manier uitvoeren:

<table frame="all" colsep="1" rowsep="1" id="table_62EB98EDD9DE49EC84CB1C7D59BC40E6"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Gebruik ten minste deze versie </th> 
   <th colname="2" class="entry"> Deze functies gebruiken </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSIE:2 </span> </td> 
   <td colname="2"> Het IV-kenmerk van de <span class="codeph"> EXT-X-KEY- </span> tag. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSIE:3 </span> </td> 
   <td colname="2"> 
    <ul id="ul_C9500D3F934848639C204BF248F139FF"> 
     <li id="li_535A7E3FABCB46FE872A7EA5DE2A1784">Duur van drijvende komma <span class="codeph"> EXTINF- </span> waarde <p>De duurtags ( <span class="codeph"> #EXTINF: </span>&lt;duration&gt;,&lt;title&gt;) in versie 2 zijn afgerond naar gehele getallen. Voor versie 3 en hoger moet de duur exact worden opgegeven in een zwevend punt. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSIE:4 </span> </td> 
   <td colname="2"> 
    <ul id="ul_3355A6CBBE2141DDB92660BB4B604D70"> 
     <li id="li_5E73D41AF6DC4CEE88D6C029FFCFC350">De <span class="codeph"> EXT-X-BYTERANGE- </span> tag </li> 
     <li id="li_BF5141F516F749E5890860D487EB5287">De <span class="codeph"> EXT-X-I-FRAME-STREAM-INF- </span> tag </li> 
     <li id="li_E0D399A13812499B94107CDE62998EE9">De <span class="codeph"> EXT-X-I-FRAMES-ONLY- </span> tag </li> 
     <li id="li_A7783AFF99854EFBBAECD2967E4CBF2B">De <span class="codeph"> EXT-X-MEDIA- </span> tag </li> 
     <li id="li_15AE652F33C1454AA90DDC65E7D6C2FD">De <span class="codeph"> AUDIO- </span> en <span class="codeph"> VIDEO- </span> kenmerken van de <span class="codeph"> EXT-X-STREAM-INF- </span> tag </li> 
     <li id="li_DB2A7847D5884F6E91FD9E78101FBCA5">Alternatieve TVSDK-audio </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>