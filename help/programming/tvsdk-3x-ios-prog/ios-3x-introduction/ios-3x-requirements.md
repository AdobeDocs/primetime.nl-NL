---
description: TVSDK heeft specifieke vereisten voor mediacontent, manifestcontent, DRM en softwareversies.
title: Vereisten
exl-id: 8c611ad4-ad04-4bab-83b9-0d8fb6c5cf3d
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# Vereisten {#requirements}

TVSDK vereist specifieke eigenschappen voor media-inhoud, manifestinhoud, DRM en softwareversies.

## Systeem- en softwarevereisten {#section_96E5B079900246E78682AE44D3F23068}

Om TVSDK te gebruiken, moet u controleren of de versies van uw hardware, besturingssysteem en toepassingen voldoen aan de onderstaande minimumvereisten.

| Besturingssysteem | iOS 7.0 of hoger |
|---|---|
| Xcode | Xcode 10 voor iOS 12 en Xcode 9 voor iOS 11 |

## Inhouds- en manifestvereisten {#section_72DD0E4DA9774DCCADB42887497F1386}

Controleer de beperkingen en vereisten voor streams en afspeellijsten (manifests), inclusief DRM-coderingssleutels.

| Keyframes van inhoudssegmenten | Elk inhoudssegment moet beginnen met een keyframe. |
|---|---|
| Volgnummers in live/lineaire video | Must match between all bit-rate renditions for the main content at any given time. |

## EXT-X-VERSION requirements {#section_C03D3DCE1D244E26BBD2C1D7144FDFBD}

De versie van `#EXT-X-VERSION` in het manifestbestand van [!DNL .m3u8] heeft invloed op welke functies beschikbaar zijn voor uw applicatie en welke `EXT` tags geldig zijn.

Hier volgt informatie over de tag `#EXT-X-VERSION`, die de versie van het HLS-protocol aangeeft:

* De versie moet overeenkomen met de functies en kenmerken in de HLS-afspeellijst; anders kunnen afspeelfouten optreden. Zie [HTTP Live Streaming specificatie](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1) voor meer informatie.
* Adobe raadt u aan ten minste versie 2 van HLS te gebruiken voor afspelen in clients die zijn gebaseerd op TVSDK.

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
   <td colname="2"> Het kenmerk IV van de tag <span class="codeph"> EXT-X-KEY </span>. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:3 </span> </td> 
   <td colname="2"> 
    <ul id="ul_C9500D3F934848639C204BF248F139FF"> 
     <li id="li_535A7E3FABCB46FE872A7EA5DE2A1784">Drijvende-komma <span class="codeph"> EXTINF </span> duurwaarden <p>De duurtags ( <span class="codeph"> #EXTINF: </span>&lt;duration&gt;,&lt;title&gt;) in versie 2 werden afgerond naar gehele waarden. Versie 3 en hoger vereisen dat de tijdsduur exact wordt opgegeven, in drijvende komma. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:4 </span> </td> 
   <td colname="2"> 
    <ul id="ul_3355A6CBBE2141DDB92660BB4B604D70"> 
     <li id="li_5E73D41AF6DC4CEE88D6C029FFCFC350">De tag <span class="codeph"> EXT-X-BYTERANGE </span> </li> 
     <li id="li_BF5141F516F749E5890860D487EB5287">De tag <span class="codeph"> EXT-X-I-FRAME-STREAM-INF </span> </li> 
     <li id="li_E0D399A13812499B94107CDE62998EE9">De <span class="codeph"> ALLEEN EXT-X-I-FRAMES </span> tag </li> 
     <li id="li_A7783AFF99854EFBBAECD2967E4CBF2B">De <span class="codeph"> EXT-X-MEDIA </span> tag </li> 
     <li id="li_15AE652F33C1454AA90DDC65E7D6C2FD">De <span class="codeph"> AUDIO </span> en <span class="codeph"> VIDEO </span> kenmerken van de <span class="codeph"> EXT-X-STREAM-INF </span> tag </li> 
     <li id="li_DB2A7847D5884F6E91FD9E78101FBCA5">Alternatieve TVSDK-audio </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
