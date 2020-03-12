---
description: Met de methoden in de MediaPlayerItem-klasse kunt u informatie ophalen over de inhoudsstroom die wordt vertegenwoordigd door een geladen MediaResource.
seo-description: Met de methoden in de MediaPlayerItem-klasse kunt u informatie ophalen over de inhoudsstroom die wordt vertegenwoordigd door een geladen MediaResource.
seo-title: Attributen van MediaPlayer voor toegang tot MediaResource-informatie
title: Attributen van MediaPlayer voor toegang tot MediaResource-informatie
uuid: d26f39d6-0a6b-4072-b99a-8767a511a846
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Attributen van MediaPlayer voor toegang tot MediaResource-informatie{#mediaplayer-attributes-to-access-mediaresource-information}

Met de methoden in de MediaPlayerItem-klasse kunt u informatie ophalen over de inhoudsstroom die wordt vertegenwoordigd door een geladen MediaResource.

<table frame="all" colsep="1" rowsep="1" id="table_46225307CA5B4BB1869576E0B9141E38"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Doel </th> 
   <th colname="2" class="entry"> Kenmerk </th> 
   <th colname="3" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> Live stream </td> 
   <td colname="2"> <span class="codeph"> leven </span> </td> 
   <td colname="3"> True if the stream is live; false als het om VOD gaat. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1" morerows="2"> Ondertiteling </td> 
   <td colname="2"> <span class="codeph"> hasClosedCaptions </span> </td> 
   <td colname="3"> True if closed-caption tracks are available. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> closedCaptionsTracks </span> </td> 
   <td colname="3"> Bevat een lijst met beschikbare Closed Caption-tracks. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectedClosedCaptionsTrack </span> </td> 
   <td colname="3"> Hiermee wordt de Closed Caption-track opgehaald die is geselecteerd met <span class="codeph"> selectClosedCaptionsTrack </span>. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1" morerows="2"> Alternatieve audio </td> 
   <td colname="2"> <span class="codeph"> hasAlternateAudio </span> </td> 
   <td colname="3"> <p>True als de stream alternatieve audiotracks heeft. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> audioTracks </span> </td> 
   <td colname="3"> Geeft een lijst met beschikbare alternatieve audiotracks. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectedAudioTrack </span> </td> 
   <td colname="3"> 
    <ph>
      Hiermee wordt de geselecteerde audiotrack opgehaald die is geselecteerd met <span class="codeph"> selectAudioTrack </span>. 
    </ph> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1" morerows="1"> Timed metadata </td> 
   <td colname="2"> <span class="codeph"> hasTimedMetadata </span> </td> 
   <td colname="3"> True if the stream has associated timed metadata. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> timedMetadata </span> </td> 
   <td colname="3"> Bevat een lijst met de metagegevensobjecten met tijdinstellingen die aan de stream zijn gekoppeld. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1" morerows="1"> Meerdere profielen (bitsnelheden) </td> 
   <td colname="2" morerows="1"> <span class="codeph"> profielen </span> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="3"> Verstrekt een lijst van de bijbehorende profielen van het beetjetarief die met deze stroom worden geassocieerd. <p>Opmerking:  U kunt de bitsnelheid voor elk profiel en de hoogte en breedte van het profiel ophalen. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Mediabron </td> 
   <td colname="2"> <span class="codeph"> resource </span> </td> 
   <td colname="3"> Retourneert de mediabron die aan dit item is gekoppeld. </td> 
  </tr> 
 </tbody> 
</table>

