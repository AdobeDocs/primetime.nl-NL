---
description: TVSDK vereist specifieke eigenschappen voor media-inhoud, manifestinhoud en softwareversies.
seo-description: TVSDK vereist specifieke eigenschappen voor media-inhoud, manifestinhoud en softwareversies.
seo-title: Vereisten
title: Vereisten
uuid: 7e5fb176-4c3f-4c12-9080-3afced28627b
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Vereisten {#requirements}

TVSDK vereist specifieke eigenschappen voor media-inhoud, manifestinhoud en softwareversies.

## Systeem- en softwarevereisten {#section_61C32A0209C44230B392B113B85643EE}

Als u TVSDK wilt gebruiken, dient u ervoor te zorgen dat uw hardware-, besturingssysteem- en toepassingsversies allemaal voldoen aan de onderstaande minimale vereisten.

Besturingssysteem: iOS 6.0 of hoger

## Inhoud- en manifestvereisten {#section_05FA02E2189742008DA09D87E66DCAB7}

Controleer de beperkingen en vereisten voor streams en afspeellijsten (manifests), inclusief DRM-coderingssleutels.

| Keyframes van inhoudssegmenten | Elk inhoudssegment moet beginnen met een keyframe. |
|---|---|
| Volgnummers in live/lineaire video | Moet op elk gewenst moment overeenkomen met alle bitsnelheidsuitvoeringen voor de hoofdinhoud. |

## #EXT-X-VERSION-vereisten {#section_C03D3DCE1D244E26BBD2C1D7144FDFBD}

De versie van `#EXT-X-VERSION` in het [!DNL .m3u8] bestand bepaalt welke functies beschikbaar zijn voor uw toepassing en welke `EXT` tags geldig zijn in uw afspeellijst/manifest.

Hier is wat informatie over de `#EXT-X-VERSION` markering, die de het protocolversie van HLS specificeert:

* De versie moet overeenkomen met de functies en kenmerken in de HLS-afspeellijst. anders kunnen er afspeelfouten optreden.

   Zie de [HTTP Live Streaming-specificatie](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1)voor meer informatie.
* Als de tag niet is opgenomen in de afspeellijsten van de stramien of media, of als er geen versie is opgegeven, wordt standaard versie 1 gebruikt. Inhoud die niet voldoet aan versie 1, wordt niet afgespeeld.
* Adobe raadt u aan ten minste versie 2 te gebruiken voor afspelen in op TVSDK gebaseerde clients.

De cliënten en de servers moeten de versies op de volgende manier uitvoeren:

<table id="table_62EB98EDD9DE49EC84CB1C7D59BC40E6"> 
 <thead> 
  <tr> 
   <th colname="1" class="entry"> Gebruik ten minste deze versie </th> 
   <th colname="2" class="entry"> Deze functies gebruiken </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSIE:2 </span> </td> 
   <td colname="2"> Het IV-kenmerk van de <span class="codeph"> EXT-X-KEY- </span> tag. </td> 
  </tr> 
  <tr> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSIE:3 </span> </td> 
   <td colname="2"> 
    <ul id="ul_C9500D3F934848639C204BF248F139FF"> 
     <li id="li_535A7E3FABCB46FE872A7EA5DE2A1784">Duur van drijvende komma <span class="codeph"> EXTINF- </span> waarde <p>De duurtags ( <span class="codeph"> #EXTINF: </span>&lt;duration&gt;,&lt;title&gt;) in versie 2 zijn afgerond naar gehele getallen. Voor versie 3 en hoger is een exacte duur vereist in een zwevend punt. </p> </li> 
     <li id="li_8DF5E91F1D5D4E19894595E1FE0A5EDE"> TVSDK-functies zoals invoeging en naadloze ABR </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="1"> <p> <span class="codeph"> EXT-X-VERSIE:4 </span> </p> </td> 
   <td colname="2"> <p> 
     <ul id="ul_99E24D013E3141308B5A57446A9B8033"> 
      <li id="li_F36E65ADD2CA451C82FF18DBD5667927">De <span class="codeph"> EXT-X-BYTERANGE- </span> tag </li> 
      <li id="li_8C653168A7B84D11AC233E7548A8D2EF">De <span class="codeph"> EXT-X-I-FRAME-STREAM-INF- </span> tag </li> 
      <li id="li_2922B34717CB4F6189068529CDBE6D10">De <span class="codeph"> EXT-X-I-FRAMES-ONLY- </span> tag </li> 
      <li id="li_D015D78E217641D7867EB509E9F9EEE2">De <span class="codeph"> EXT-X-MEDIA- </span> tag </li> 
      <li id="li_CA068EA381984F5497FE67617CA8BB34">De <span class="codeph"> AUDIO- </span> en <span class="codeph"> VIDEO- </span> kenmerken van de <span class="codeph"> EXT-X-STREAM-INF- </span> tag </li> 
      <li id="li_EE78CC7D194A4EB2897F9AE8E4B081B8"> Alternatieve TVSDK-audio </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>
