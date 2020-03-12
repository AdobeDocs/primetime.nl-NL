---
description: 'De versie van #EXT-X-VERSION in het .m3u8-bestand bepaalt welke functies beschikbaar zijn voor uw toepassing en welke EXT-tags geldig zijn in uw afspeellijst/manifest.'
seo-description: 'De versie van #EXT-X-VERSION in het .m3u8-bestand bepaalt welke functies beschikbaar zijn voor uw toepassing en welke EXT-tags geldig zijn in uw afspeellijst/manifest.'
seo-title: '#EXT-X-VERSION-vereisten'
title: '#EXT-X-VERSION-vereisten'
uuid: 8d22930f-4faf-4a40-b1f0-507886cd8938
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# #EXT-X-VERSION-vereisten{#ext-x-version-requirements}

De versie van #EXT-X-VERSION in het .m3u8-bestand bepaalt welke functies beschikbaar zijn voor uw toepassing en welke EXT-tags geldig zijn in uw afspeellijst/manifest.

<!--<a id="section_8850183988124049A001758F117AD3A6"></a>-->

Hier is wat informatie over de `#EXT-X-VERSION` markering, die de het protocolversie van HLS specificeert:

* De versie moet overeenkomen met de functies en kenmerken in de HLS-afspeellijst. anders kunnen er afspeelfouten optreden. Zie de [HTTP Live Streaming-specificatie](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1)voor meer informatie.
* Adobe raadt u aan ten minste versie 2 te gebruiken voor afspelen in op TVSDK gebaseerde Browser-clients.

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
   <td colname="1"> <span class="codeph"> EXT-X-VERSIE:3 </span> </td> 
   <td colname="2"> 
    <ul id="ul_C9500D3F934848639C204BF248F139FF"> 
     <li id="li_535A7E3FABCB46FE872A7EA5DE2A1784">Duur van drijvende komma <span class="codeph"> EXTINF- </span> waarde <p>De duurtags ( <span class="codeph"> #EXTINF: </span>&lt;duration&gt;,&lt;title&gt;) in versie 2 zijn afgerond naar gehele getallen. Voor versie 3 en hoger is een exacte duur vereist in een zwevend punt. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSIE:4 </span> </td> 
   <td colname="2"> 
    <ul id="ul_3355A6CBBE2141DDB92660BB4B604D70"> 
     <li id="li_A7783AFF99854EFBBAECD2967E4CBF2B">De <span class="codeph"> EXT-X-MEDIA- </span> tag </li> 
     <li id="li_15AE652F33C1454AA90DDC65E7D6C2FD">De <span class="codeph"> AUDIO- </span> en <span class="codeph"> VIDEO- </span> kenmerken van de <span class="codeph"> EXT-X-STREAM-INF- </span> tag </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

