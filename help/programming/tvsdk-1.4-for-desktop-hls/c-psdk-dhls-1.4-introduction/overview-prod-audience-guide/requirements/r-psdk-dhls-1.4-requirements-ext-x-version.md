---
description: De versie van EXT-X-VERSION in het .m3u8-bestand beïnvloedt welke functies beschikbaar zijn voor uw applicatie en welke EXT-tags geldig zijn in uw afspeellijst/manifest.
title: EXT-X-VERSION requirements
exl-id: ee778fe1-d050-4c90-af8d-6600fff72e52
source-git-commit: e2a796dc5eb017929297d127cc79b65ba51a0c75
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# EXT-X-VERSION requirements{#ext-x-version-requirements}

De versie van #EXT-X-VERSION in het .m3u8-bestand heeft invloed op welke functies beschikbaar zijn voor uw applicatie en welke EXT-tags geldig zijn in uw afspeellijst/manifest.

<!--<a id="section_8850183988124049A001758F117AD3A6"></a>-->

Hier volgt informatie over de tag `#EXT-X-VERSION`, die de versie van het HLS-protocol opgeeft:

* De versie moet overeenkomen met de functies en kenmerken in de HLS-afspeellijst; anders kunnen afspeelfouten optreden.

   Zie [HTTP Live Streaming-specificatie](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1) voor meer informatie.
* De versie moet overeenkomen met de functies en kenmerken in de HLS-afspeellijst; anders kunnen afspeelfouten optreden.

   Zie [HTTP Live Streaming specificatie](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1) voor meer informatie.
* Adobe raadt u aan ten minste versie 2 te gebruiken voor het afspelen in op -based clients.

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
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:2 </span> </td> 
   <td colname="2"> Het kenmerk IV van de tag <span class="codeph"> EXT-X-KEY </span>. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:3 </span> </td> 
   <td colname="2"> 
    <ul id="ul_C9500D3F934848639C204BF248F139FF"> 
     <li id="li_535A7E3FABCB46FE872A7EA5DE2A1784">drijvende komma <span class="codeph"> EXTINF </span> waarden voor duur <p>De duurtags ( <span class="codeph"> #EXTINF: </span>&lt;duration&gt;,&lt;title&gt;) in versie 2 werden afgerond naar gehele waarden. Versie 3 en hoger vereisen dat de tijdsduur exact moet zijn in drijvende-komma. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> <p> <span class="codeph"> EXT-X-VERSION:4 </span> </p> </td> 
   <td colname="2"> <p> 
     <ul id="ul_83D61E909D0C413FBDAB7A4A0BE1F03C"> 
      <li id="li_5071F2BE2DB74BBFB1F23B3B30C5CFD6">De tag <span class="codeph"> EXT-X-BYTERANGE </span> </li> 
      <li id="li_A093F448567D475AB44656D4600BCBD6">De tag <span class="codeph"> EXT-X-I-FRAME-STREAM-INF </span> </li> 
      <li id="li_1084AE3B10FD4EB387D25EEDDFBBC8CD">De tag <span class="codeph"> EXT-X-I-FRAMES-ONLY </span> </li> 
      <li id="li_4FEFA36E300C403DBB77BB4DA46DB4EB">De tag <span class="codeph"> EXT-X-MEDIA </span> </li> 
      <li id="li_E53D81AED45C47AEA346FA3A1B191E5C">De <span class="codeph"> AUDIO </span> en <span class="codeph"> VIDEO </span> kenmerken van de <span class="codeph"> EXT-X-STREAM-INF </span> tag </li> 
      <li id="li_2E99A4971B8046F3845CF3D4D363CCCF">TVSDK alternate audio </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>
