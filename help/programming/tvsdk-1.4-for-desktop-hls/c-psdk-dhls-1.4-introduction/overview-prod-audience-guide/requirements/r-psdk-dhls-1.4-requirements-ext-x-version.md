---
description: De versie van EXT-X-VERSION in het .m3u8-bestand bepaalt welke functies beschikbaar zijn voor uw toepassing en welke EXT-tags geldig zijn in uw afspeellijst/manifest.
title: VEREISTEN VOOR EXT-X-VERSIE
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# VEREISTEN VOOR EXT-X-VERSIE{#ext-x-version-requirements}

De versie van #EXT-X-VERSION in het .m3u8-bestand bepaalt welke functies beschikbaar zijn voor uw toepassing en welke EXT-tags geldig zijn in uw afspeellijst/manifest.

<!--<a id="section_8850183988124049A001758F117AD3A6"></a>-->

Hier volgt wat informatie over de `#EXT-X-VERSION` tag, die de HLS-protocolversie aangeeft:

* De versie moet overeenkomen met de functies en kenmerken in de HLS-afspeellijst; Anders kunnen er afspeelfouten optreden.

  Zie [de specificatie](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1) HTTP Live Streaming voor meer informatie.
* De versie moet overeenkomen met de functies en kenmerken in de HLS-afspeellijst; Anders kunnen er afspeelfouten optreden.

  Zie [de specificatie](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1) HTTP Live Streaming voor meer informatie.
* Adobe raadt aan om ten minste versie 2 te gebruiken voor het afspelen in clients die zijn gebaseerd op afspelen.

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
   <td colname="1"> <span class="codeph"> EXT-X-VERSIE:2 </span> </td> 
   <td colname="2"> Het IV-kenmerk van de <span class="codeph"> tag EXT-X-KEY </span> . </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSIE:3 </span> </td> 
   <td colname="2"> 
    <ul id="ul_C9500D3F934848639C204BF248F139FF"> 
     <li id="li_535A7E3FABCB46FE872A7EA5DE2A1784">Zwevende-punt <span class="codeph"> EXTINF-duurwaarden </span> <p>De tags voor de duur ( <span class="codeph"> #EXTINF: </span>&lt;duration&gt;,&lt;title&gt;) in versie 2 werden afgerond op gehele getallen. &lt;/title&gt;&lt;/duration&gt; Voor versie 3 en hoger moet de tijdsduur exact gelijk zijn aan het zwevende punt. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> <p> <span class="codeph"> EXT-X-VERSIE:4 </span> </p> </td> 
   <td colname="2"> <p> 
     <ul id="ul_83D61E909D0C413FBDAB7A4A0BE1F03C"> 
      <li id="li_5071F2BE2DB74BBFB1F23B3B30C5CFD6">De <span class="codeph"> EXT-X-BYTERANGE-tag </span> </li> 
      <li id="li_A093F448567D475AB44656D4600BCBD6">De <span class="codeph"> EXT-X-I-FRAME-STREAM-INF-tag </span> </li> 
      <li id="li_1084AE3B10FD4EB387D25EEDDFBBC8CD">De <span class="codeph"> tag EXT-X-I-FRAMES-ONLY </span> </li> 
      <li id="li_4FEFA36E300C403DBB77BB4DA46DB4EB">De <span class="codeph"> EXT-X-MEDIA-tag </span> </li> 
      <li id="li_E53D81AED45C47AEA346FA3A1B191E5C">De <span class="codeph"> AUDIO </span> en <span class="codeph"> VIDEO </span> kenmerken van de <span class="codeph"> EXT-X-STREAM-INF </span> tag </li> 
      <li id="li_2E99A4971B8046F3845CF3D4D363CCCF">Alternatieve audio VIA TVSDK </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>
