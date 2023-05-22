---
description: TVSDK vereist specifieke eigenschappen voor mediacontent, manifestcontent en softwareversies.
title: Vereisten
exl-id: 2b81ae19-7907-4038-80e1-f579a8c04540
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# Vereisten {#requirements}

TVSDK vereist specifieke eigenschappen voor media-inhoud, manifestinhoud en softwareversies.

## Systeem- en softwarevereisten {#section_61C32A0209C44230B392B113B85643EE}

Om TVSDK te gebruiken, moet u controleren of de versies van uw hardware, besturingssysteem en toepassingen voldoen aan de onderstaande minimumvereisten.

Besturingssysteem: iOS 6.0 of hoger

## Inhouds- en manifestvereisten {#section_05FA02E2189742008DA09D87E66DCAB7}

Controleer de beperkingen en vereisten voor streams en afspeellijsten (manifesten), inclusief DRM-coderingssleutels.a

| Hoofdframes van contentsegmenten | Elk contentsegment moet beginnen met een hoofdframe. |
|---|---|
| Volgnummers in live/lineaire video | Moet op elk gewenst moment overeenkomen met alle bitsnelheidsuitvoeringen voor de hoofdinhoud. |

## #EXT-X-VERSION-vereisten {#section_C03D3DCE1D244E26BBD2C1D7144FDFBD}

De versie van `#EXT-X-VERSION` in de [!DNL .m3u8] heeft invloed op welke functies beschikbaar zijn voor uw toepassing en wat `EXT` -tags zijn geldig in uw afspeellijst/manifest.

Hier volgt informatie over de tag `#EXT-X-VERSION`, die de versie van het HLS-protocol aangeeft:

* De versie moet overeenkomen met de functies en kenmerken in de HLS-afspeellijst; anders kunnen afspeelfouten optreden.

   Zie [HTTP Live Streaming specificatie](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1) voor meer informatie.
* Als de tag niet is opgenomen in de master afspeellijsten of de mediaspellijsten, of als er geen versie is opgegeven, wordt versie 1 standaard gebruikt. Content die niet voldoet aan versie 1 wordt niet afgespeeld.
* Adobe raadt u aan ten minste versie 2 te gebruiken voor afspelen in clients die zijn gebaseerd op TVSDK.

Clients en servers moeten de versies op de volgende manier implementeren:

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
   <td colname="2"> De eigenschap IV van de <span class="codeph"> EXT-X-KEY </span> tag. </td> 
  </tr> 
  <tr> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:3 </span> </td> 
   <td colname="2"> 
    <ul id="ul_C9500D3F934848639C204BF248F139FF"> 
     <li id="li_535A7E3FABCB46FE872A7EA5DE2A1784">Drijvende-komma <span class="codeph"> EXTINF </span> duurwaarden <p>De duurtags ( <span class="codeph"> #EXTINF: </span>&lt;duration&gt;,&lt;title&gt;) in versie 2 werden afgerond naar gehele waarden. Versie 3 en hoger vereisen dat de tijdsduur exact moet zijn in drijvende-komma. </p> </li> 
     <li id="li_8DF5E91F1D5D4E19894595E1FE0A5EDE"> TVSDK-functies zoals het invoegen van advertenties en naadloze ABR </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="1"> <p> <span class="codeph"> EXT-X-VERSION:4 </span> </p> </td> 
   <td colname="2"> <p> 
     <ul id="ul_99E24D013E3141308B5A57446A9B8033"> 
      <li id="li_F36E65ADD2CA451C82FF18DBD5667927">De tag <span class="codeph"> EXT-X-BYTERANGE </span> </li> 
      <li id="li_8C653168A7B84D11AC233E7548A8D2EF">De tag <span class="codeph"> EXT-X-I-FRAME-STREAM-INF </span> </li> 
      <li id="li_2922B34717CB4F6189068529CDBE6D10">De <span class="codeph"> ALLEEN EXT-X-I-FRAMES </span> tag </li> 
      <li id="li_D015D78E217641D7867EB509E9F9EEE2">De <span class="codeph"> EXT-X-MEDIA </span> tag </li> 
      <li id="li_CA068EA381984F5497FE67617CA8BB34">De <span class="codeph"> AUDIO </span> en <span class="codeph"> VIDEO </span> kenmerken van de <span class="codeph"> EXT-X-STREAM-INF </span> tag </li> 
      <li id="li_EE78CC7D194A4EB2897F9AE8E4B081B8"> Alternatieve TVSDK-audio </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>
