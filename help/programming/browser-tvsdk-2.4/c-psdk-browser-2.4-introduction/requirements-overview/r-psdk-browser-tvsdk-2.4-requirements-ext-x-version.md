---
description: De versie van EXT-X-VERSION in het .m3u8-bestand bepaalt welke functies beschikbaar zijn voor uw toepassing en welke EXT-tags geldig zijn in uw afspeellijst/manifest.
title: VEREISTEN VOOR EXT-X-VERSIE
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 0%

---

# VEREISTEN VOOR EXT-X-VERSIE{#ext-x-version-requirements}

De versie van `#EXT-X-VERSION` het .m3u8-bestand bepaalt welke functies voor uw toepassing beschikbaar zijn en welke EXT-tags geldig zijn in uw afspeellijst/manifest.

<!--<a id="section_8850183988124049A001758F117AD3A6"></a>-->

Hier volgt wat informatie over de `#EXT-X-VERSION` tag, die de HLS-protocolversie aangeeft:

* De versie moet overeenkomen met de functies en kenmerken in de HLS-afspeellijst; Anders kunnen er afspeelfouten optreden. Zie [de specificatie](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1) HTTP Live Streaming voor meer informatie.
* Adobe raadt aan om ten minste versie 2 te gebruiken voor afspelen in browser-TVSDK-clients.

  Clients en servers moeten de versies op de volgende manier implementeren:

<table frame="all" colsep="1" rowsep="1" id="table_62EB98EDD9DE49EC84CB1C7D59BC40E6"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Gebruik ten minste deze versie </th> 
   <th colname="2" class="entry"> Als u deze functies wilt gebruiken </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSIE:3 </span> </td> 
   <td colname="2"> 
    <ul id="ul_C9500D3F934848639C204BF248F139FF"> 
     <li id="li_535A7E3FABCB46FE872A7EA5DE2A1784">Zwevende-punt <span class="codeph"> EXTINF-duurwaarden </span> <p>De tags voor de duur ( <span class="codeph"> #EXTINF: </span>&lt;duration&gt;,&lt;title&gt;) in versie 2 werden afgerond op gehele getallen. &lt;/title&gt;&lt;/duration&gt; Voor versie 3 en hoger moet de tijdsduur exact gelijk zijn aan het zwevende punt. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSIE:4 </span> </td> 
   <td colname="2"> 
    <ul id="ul_3355A6CBBE2141DDB92660BB4B604D70"> 
     <li id="li_A7783AFF99854EFBBAECD2967E4CBF2B">De <span class="codeph"> EXT-X-MEDIA-tag </span> </li> 
     <li id="li_15AE652F33C1454AA90DDC65E7D6C2FD">De <span class="codeph"> AUDIO</span>- en <span class="codeph"> VIDEO-kenmerken </span> van de <span class="codeph"> TAG EXT-X-STREAM-INF </span> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
