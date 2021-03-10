---
description: Met de methoden in de MediaPlayerItem-klasse kunt u informatie ophalen over de inhoudsstroom die wordt vertegenwoordigd door een geladen MediaResource.
title: Methoden van MediaPlayer voor toegang tot MediaResource-informatie
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---


# Methoden van MediaPlayer voor de toegang tot van MediaResource informatie{#mediaplayer-methods-for-accessing-mediaresource-information}

Met de methoden in de MediaPlayerItem-klasse kunt u informatie ophalen over de inhoudsstroom die wordt vertegenwoordigd door een geladen MediaResource.

<table frame="all" colsep="1" rowsep="1" id="table_77B55D506FE24326A03D97AA087231FF"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="2" class="entry"> Methode </th> 
   <th colname="3" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Live stream  </b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get isLive():Boolean;  </span> </td> 
   <td colname="3"> <p>True if the stream is live; false als het om VOD gaat. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>DRM beveiligd</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get isProtected():Boolean;  </span> </td> 
   <td colname="3"> <p>True if the stream is protected DRM. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get drmMetadataInfos(): Vector.&lt;drmmetadatainfo&gt;;  </span> </td> 
   <td colname="3"> <p>Hiermee worden alle DRM-metagegevensobjecten weergegeven die in het manifest zijn aangetroffen. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Ondertiteling</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get hasClosedCaptions():Boolean;  </span> </td> 
   <td colname="3"> <p>True if closed-caption tracks are available. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get closedCaptionsTracks():Vector.&lt;closedcaptionstrack&gt;;  </span> </td> 
   <td colname="3"> <p>Bevat een lijst met beschikbare Closed Caption-tracks. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get selectedClosedCaptionsTrack():ClosedCaptionsTrack  </span> </td> 
   <td colname="3"> <p>Hiermee wordt de huidige gesloten bijschrifttrack opgehaald die is geselecteerd met <span class="codeph"> SelectClosedCaptionsTrack </span>. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectClosedCaptionsTrack (closedCaptionsTrack: com.adobe.mediacore.info:ClosedCaptionsTrack )  </span> </td> 
   <td colname="3"> <p>Hiermee stelt u een Closed Caption-track in als de huidige Closed Caption-track. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Alternatieve audiotracks  </b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get hasAlternateAudio():Boolean;  </span> </td> 
   <td colname="3"> <p>True als de stream alternatieve audiotracks heeft. </p> <p>Tip:  De hoofdaudiotrack (standaard) maakt ook deel uit van de lijst met alternatieve audiotracks. </p> <p>TVSDK voor Desktop HLS beschouwt de belangrijkste audiospoor als één van de punten in de afwisselende audiospoorlijst. Daarom is het enige geval waarbij <span class="codeph"> MediaPlayerItem.hasAlternateAudio </span> false retourneert, wanneer de stream helemaal geen audio heeft. Als de inhoud slechts één audiospoor heeft, keert deze methode waar terug, en <span class="codeph"> krijgt AudioTracks </span> keert een lijst met één enkel element (het gebrek audiospoor) terug. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get audioTracks():Vector.&lt;audiotrack&gt;;  </span> </td> 
   <td colname="3"> Geeft een lijst met beschikbare alternatieve audiotracks. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get audioTracks():Vector.&lt;audiotrack&gt;;  </span> </td> 
   <td colname="3"> <p>Geeft een lijst met beschikbare alternatieve audiotracks. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get selectedAudioTrack():AudioTrack;  </span> </td> 
   <td colname="3"> <p>Hiermee wordt de audiotrack opgehaald die is geselecteerd met <span class="codeph"> selectAudioTrack </span>. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectAudioTrack(audioTrack: AudioTrack )  </span> </td> 
   <td colname="3"> <p>Hiermee selecteert u een audiotrack als huidige audiotrack. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Timed metadata</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get hasTimedMetadata():Boolean;  </span> </td> 
   <td colname="3"> <p>True if the stream has associated timed metadata. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get timedMetadata():Vector.&lt;timedmetadata&gt;;  </span> </td> 
   <td colname="3"> <p>Bevat een lijst met de metagegevensobjecten met tijdslimiet die aan de stream zijn gekoppeld. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get isDynamic():Boolean;  </span> </td> 
   <td colname="3"> <p>True if the stream is a multiple bit rate (MBR) stream. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get profiles():Vector.&lt;profile&gt;;  </span> </td> 
   <td colname="3"> <p>Verstrekt een lijst van de bijbehorende profielen van het beetjetarief. Voor elk profiel kunt u de bitsnelheid en de hoogte en breedte van het profiel ophalen. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Steen spelen  </b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get isTrickPlaySupported():Boolean;  </span> </td> 
   <td colname="3"> <p>True if the player supports fast forward, rewind, and resume. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get availablePlaybackRates():Vector.&lt;number&gt; </span> </td> 
   <td colname="3"> <p>Verstrekt de lijst van beschikbare playbacktarieven in de context van de truc-speleigenschap. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Mediaspeler  </b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get player():MediaPlayer  </span> </td> 
   <td colname="3"> <p>Retourneert de mediaspeler die momenteel aan deze speler is gekoppeld. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Mediabron</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get resource():MediaResource;  </span> </td> 
   <td colname="3"> <p>Retourneert de mediabron die aan dit item is gekoppeld. </p> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="2"> <span class="codeph"> function get resourceId():int  </span> </td> 
   <td colname="3"> <p>Retourneert de media-id die aan dit item is gekoppeld. </p> </td> 
  </tr> 
 </tbody> 
</table>

