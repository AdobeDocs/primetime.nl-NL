---
description: De versie van EXT-X-VERSION in het .m3u8-bestand bepaalt welke functies beschikbaar zijn voor uw toepassing en welke EXT-tags geldig zijn in uw afspeellijst/manifest.
title: EXT-X-VERSION-vereisten
exl-id: 1b7c205b-c6b1-416f-885a-d1cd23d8e803
source-git-commit: e2a796dc5eb017929297d127cc79b65ba51a0c75
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 0%

---

# EXT-X-VERSION-vereisten{#ext-x-version-requirements}

De versie van `#EXT-X-VERSION` in het .m3u8 dossier beïnvloedt welke eigenschappen aan uw toepassing beschikbaar zijn en welke markeringen EXT in uw playlist/manifest geldig zijn.

<!--<a id="section_8850183988124049A001758F117AD3A6"></a>-->

Hier is wat informatie over de `#EXT-X-VERSION` markering, die de het protocolversie van HLS specificeert:

* De versie moet overeenkomen met de functies en kenmerken in de HLS-afspeellijst. anders kunnen er afspeelfouten optreden. Zie [Live HTTP-streaming specificatie](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1) voor meer informatie.
* Adobe raadt aan ten minste versie 2 te gebruiken voor afspelen in op TVSDK gebaseerde Browser-clients.

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
   <td colname="1"> <span class="codeph"> EXT-X-VERSIE:3  </span> </td> 
   <td colname="2"> 
    <ul id="ul_C9500D3F934848639C204BF248F139FF"> 
     <li id="li_535A7E3FABCB46FE872A7EA5DE2A1784">Duur <span class="codeph"> EXTINF </span> <p>De duurtags ( <span class="codeph"> #EXTINF: </span>&lt;duration&gt;,&lt;title&gt;) in versie 2 zijn afgerond naar gehele getallen. Voor versie 3 en hoger is een exacte duur vereist in een zwevend punt. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSIE:4  </span> </td> 
   <td colname="2"> 
    <ul id="ul_3355A6CBBE2141DDB92660BB4B604D70"> 
     <li id="li_A7783AFF99854EFBBAECD2967E4CBF2B">De tag <span class="codeph"> EXT-X-MEDIA </span> </li> 
     <li id="li_15AE652F33C1454AA90DDC65E7D6C2FD">De <span class="codeph"> AUDIO </span>- en <span class="codeph">-kenmerken VIDEO </span> van de <span class="codeph"> EXT-X-STREAM-INF </span>-tag </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
