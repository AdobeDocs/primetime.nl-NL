---
description: TVSDK heeft specifieke vereisten voor media-, manifestinhoud, DRM- en softwareversies.
title: Vereisten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# Vereisten {#requirements}

TVSDK vereist specifieke eigenschappen voor media-inhoud, manifestinhoud, DRM en softwareversies.

## Systeem- en softwarevereisten {#section_96E5B079900246E78682AE44D3F23068}

Als u TVSDK wilt gebruiken, moet u ervoor zorgen dat uw hardware, besturingssysteem en toepassingsversies allemaal voldoen aan de onderstaande minimale vereisten.

| Besturingssysteem | iOS 7.0 of hoger |
|---|---|
| Xcode | Xcode 10 voor iOS 12 en Xcode 9 voor iOS 11 |

## Vereisten voor inhoud en manifest {#section_72DD0E4DA9774DCCADB42887497F1386}

Controleer de beperkingen en vereisten voor streams en afspeellijsten (manifests), inclusief DRM-coderingssleutels.

| Keyframes van inhoudssegmenten | Elk inhoudssegment moet beginnen met een keyframe. |
|---|---|
| Volgnummers in live/lineaire video | Moet op elk gewenst moment overeenkomen tussen alle bitsnelheidweergaven voor de hoofdinhoud. |

## VEREISTEN VOOR EXT-X-VERSIE {#section_C03D3DCE1D244E26BBD2C1D7144FDFBD}

De versie van `#EXT-X-VERSION` het [!DNL .m3u8] manifestbestand bepaalt welke functies voor uw toepassing beschikbaar zijn en welke `EXT` tags geldig zijn.

Hier volgt wat informatie over de `#EXT-X-VERSION` tag, die de HLS-protocolversie aangeeft:

* De versie moet overeenkomen met de functies en kenmerken in de HLS-afspeellijst; Anders kunnen er afspeelfouten optreden. Zie [de specificatie](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1) HTTP Live Streaming voor meer informatie.
* Adobe raadt aan om ten minste versie 2 van HLS te gebruiken voor afspelen in TVSDK-clients.

  Clients en servers moeten de versies op de volgende manier implementeren:

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
   <td colname="2"> Het IV-kenmerk van de <span class="codeph"> tag EXT-X-KEY </span> . </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSIE:3 </span> </td> 
   <td colname="2"> 
    <ul id="ul_C9500D3F934848639C204BF248F139FF"> 
     <li id="li_535A7E3FABCB46FE872A7EA5DE2A1784">Zwevende-punt <span class="codeph"> EXTINF-duurwaarden </span> <p>De tags voor de duur ( <span class="codeph"> #EXTINF: </span>&lt;duration&gt;,&lt;title&gt;) in versie 2 werden afgerond op gehele getallen. &lt;/title&gt;&lt;/duration&gt; Voor versie 3 en hoger moet de tijdsduur exact worden opgegeven, in een zwevend punt. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSIE:4 </span> </td> 
   <td colname="2"> 
    <ul id="ul_3355A6CBBE2141DDB92660BB4B604D70"> 
     <li id="li_5E73D41AF6DC4CEE88D6C029FFCFC350">De <span class="codeph"> EXT-X-BYTERANGE-tag </span> </li> 
     <li id="li_BF5141F516F749E5890860D487EB5287">De <span class="codeph"> EXT-X-I-FRAME-STREAM-INF-tag </span> </li> 
     <li id="li_E0D399A13812499B94107CDE62998EE9">De <span class="codeph"> ALLEEN EXT-X-I-FRAMES </span> tag </li> 
     <li id="li_A7783AFF99854EFBBAECD2967E4CBF2B">De <span class="codeph"> EXT-X-MEDIA </span> tag </li> 
     <li id="li_15AE652F33C1454AA90DDC65E7D6C2FD">De <span class="codeph"> AUDIO </span> en <span class="codeph"> VIDEO </span> kenmerken van de <span class="codeph"> EXT-X-STREAM-INF </span> tag </li> 
     <li id="li_DB2A7847D5884F6E91FD9E78101FBCA5">Alternatieve TVSDK-audio </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
