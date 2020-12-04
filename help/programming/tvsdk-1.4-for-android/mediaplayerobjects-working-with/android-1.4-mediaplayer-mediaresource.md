---
description: Met de methoden in de MediaPlayerItem-klasse kunt u informatie ophalen over de inhoudsstroom die wordt vertegenwoordigd door een geladen MediaResource.
seo-description: Met de methoden in de MediaPlayerItem-klasse kunt u informatie ophalen over de inhoudsstroom die wordt vertegenwoordigd door een geladen MediaResource.
seo-title: Methoden van MediaPlayer voor toegang tot MediaResource-informatie
title: Methoden van MediaPlayer voor toegang tot MediaResource-informatie
uuid: 5d83491c-6577-46fe-98af-83f0fde7a7d0
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '431'
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
   <td colname="1"> <b>Labels toevoegen</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;string&gt; ListgetAdTags()  </span> </td> 
   <td colname="3"> <p>Bevat de lijst met advertentietags die worden gebruikt voor het plaatsingsproces. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Live stream</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isLive();  </span> </td> 
   <td colname="3"> <p>True if the stream is live; false als het om VOD gaat. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>DRM beveiligd</b> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isProtected();  </span> </td> 
   <td colname="3"> <p>True if the stream is protected DRM. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;drmmetadatainfo&gt; ListgetDRMMetadataInfos();  </span> </td> 
   <td colname="3"> <p>Hiermee worden alle DRM-metagegevensobjecten weergegeven die in het manifest zijn aangetroffen. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Ondertiteling</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean hasClosedCaptions();  </span> </td> 
   <td colname="3"> <p>True if closed-caption tracks are available. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;closedcaptionstrack&gt; ListgetClosedCationsTracks();  </span> </td> 
   <td colname="3"> <p>Bevat een lijst met beschikbare Closed Caption-tracks. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> ClosedCaptionsTrack get SelectedClosedCaptionsTrack();  </span> </td> 
   <td colname="3"> <p>Hiermee wordt de huidige gesloten bijschrifttrack opgehaald die is geselecteerd met <span class="codeph"> SelectClosedCaptionsTrack </span>. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectClosedCaptionsTrack ( ClosedCaptionsTrack closedCaptionsTrack)  </span> </td> 
   <td colname="3"> <p>Hiermee stelt u een Closed Caption-track in als de huidige Closed Caption-track. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Alternatieve audiotracks</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean hasAlternateAudio();  </span> </td> 
   <td colname="3"> <p>True als de stream alternatieve audiotracks heeft. </p> <p>Tip:  De hoofdaudiotrack (standaard) maakt ook deel uit van de lijst met alternatieve audiotracks. </p> <p>TVSDK voor Android beschouwt de hoofdaudiotrack als een van de items in de alternatieve audiotracklijst. Daarom is het enige geval waarbij <span class="codeph"> MediaPlayerItem.hasAlternateAudio </span> false retourneert, wanneer de stream helemaal geen audio heeft. Als de inhoud slechts één audiospoor heeft, keert deze methode waar terug, en <span class="codeph"> MediaPlayerItem.getAudioTracks </span> keert een lijst met één enkel element (het standaard audiospoor) terug. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;audiotrack&gt; ListgetAudioTracks();  </span> </td> 
   <td colname="3"> Geeft een lijst met beschikbare alternatieve audiotracks. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;audiotrack&gt; ListgetAudioTracks();  </span> </td> 
   <td colname="3"> <p>Geeft een lijst met beschikbare alternatieve audiotracks. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> AudioTrack getSelectedAudioTrack();  </span> </td> 
   <td colname="3"> <p>Hiermee wordt de audiotrack opgehaald die is geselecteerd met <span class="codeph"> selectAudioTrack </span>. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectAudioTrack ( AudioTrack AudioTrack )  </span> </td> 
   <td colname="3"> <p>Hiermee selecteert u een audiotrack als huidige audiotrack. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Timed metadata</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean hasTimedMetadata();  </span> </td> 
   <td colname="3"> <p>True if the stream has associated timed metadata. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;timedmetadata&gt; ListgetTimedMetadata();  </span> </td> 
   <td colname="3"> <p>Bevat een lijst met de metagegevensobjecten met tijdslimiet die aan de stream zijn gekoppeld. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isDynamic();  </span> </td> 
   <td colname="3"> <p>True if the stream is a multiple bit rate (MBR) stream. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;profile&gt; ListgetProfiles();  </span> </td> 
   <td colname="3"> <p>Verstrekt een lijst van de bijbehorende profielen van het beetjetarief. Voor elk profiel kunt u de bitsnelheid en de hoogte en breedte van het profiel ophalen. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Steen spelen</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isTrickPlaySupported();  </span> </td> 
   <td colname="3"> <p>True if the player supports fast forward, rewind, and resume. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt; Float=""&gt; ListgetAvailablePlaybackRates  </span> </td> 
   <td colname="3"> <p>Verstrekt de lijst van beschikbare playbacktarieven in de context van de truc-speleigenschap. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Mediabron</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> MediaResource getResource();  </span> </td> 
   <td colname="3"> <p>Retourneert de mediabron die aan dit item is gekoppeld. </p> </td> 
  </tr> 
 </tbody> 
</table>

