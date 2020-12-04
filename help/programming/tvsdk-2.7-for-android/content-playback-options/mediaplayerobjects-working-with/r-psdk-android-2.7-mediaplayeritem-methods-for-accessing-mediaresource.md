---
description: Met de methoden in de MediaPlayerItem-klasse kunt u informatie ophalen over de inhoudsstroom die wordt vertegenwoordigd door een geladen MediaResource.
seo-description: Met de methoden in de MediaPlayerItem-klasse kunt u informatie ophalen over de inhoudsstroom die wordt vertegenwoordigd door een geladen MediaResource.
seo-title: Methoden van MediaPlayerItem voor toegang tot MediaResource-informatie
title: Methoden van MediaPlayerItem voor toegang tot MediaResource-informatie
uuid: c6e77eb7-cefd-48aa-9373-2b44a96217a5
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---


# Methoden van MediaPlayerItem voor de toegang tot MediaResource-informatie {#mediaplayeritem-methods-for-accessing-mediaresource-information}

Met de methoden in de MediaPlayerItem-klasse kunt u informatie ophalen over de inhoudsstroom die wordt vertegenwoordigd door een geladen MediaResource.

<table frame="all" colsep="1" rowsep="1" id="table_F6006A9167044AC087A6ECB20B8CCD5D"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="2" class="entry"> Methode </th> 
   <th colname="3" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Labels toevoegen</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;string&gt; ListgetAdTags()  </span> </td> 
   <td colname="3"> Bevat de lijst met advertentietags die worden gebruikt voor het plaatsingsproces. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Live stream</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isLive();  </span> </td> 
   <td colname="3"> True if the stream is live; false als het om VOD gaat. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>DRM beveiligd</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isProtected();  </span> </td> 
   <td colname="3"> True if the stream is protected DRM. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;drmmetadatainfo&gt; ListgetDRMMetadataInfos();  </span> </td> 
   <td colname="3"> Hiermee worden alle DRM-metagegevensobjecten weergegeven die in het manifest zijn aangetroffen. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Ondertiteling</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean hasClosedCaptions();  </span> </td> 
   <td colname="3"> True if closed-caption tracks are available. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;closedcaptionstrack&gt; ListgetClosedCationsTracks();  </span> </td> 
   <td colname="3"> Bevat een lijst met beschikbare Closed Caption-tracks. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> ClosedCaptionsTrack get SelectedClosedCaptionsTrack();  </span> </td> 
   <td colname="3"> Hiermee wordt de huidige gesloten bijschrifttrack opgehaald die is geselecteerd met <span class="codeph"> SelectClosedCaptionsTrack </span>. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectClosedCaptionsTrack ( ClosedCaptionsTrack closedCaptionsTrack)  </span> </td> 
   <td colname="3"> Hiermee stelt u een Closed Caption-track in als de huidige Closed Caption-track. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Alternatieve audiotracks</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean hasAlternateAudio();  </span> </td> 
   <td colname="3"> True als de stream alternatieve audiotracks heeft. <p>Opmerking:  De hoofdaudiotrack (standaard) maakt ook deel uit van de lijst met alternatieve audiotracks. </p> <p>TVSDK voor Android beschouwt de hoofdaudiotrack als een van de items in de alternatieve audiotracklijst. Daarom is het enige geval waarbij <span class="codeph"> MediaPlayerItem.hasAlternateAudio </span> false retourneert, wanneer de stream helemaal geen audio heeft. Als de inhoud slechts één audiospoor heeft, keert deze methode waar terug, en <span class="codeph"> MediaPlayerItem.getAudioTracks </span> keert een lijst met één enkel element (het standaard audiospoor) terug. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;audiotrack&gt; ListgetAudioTracks();  </span> </td> 
   <td colname="3"> Geeft een lijst met beschikbare alternatieve audiotracks. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> AudioTrack getSelectedAudioTrack();  </span> </td> 
   <td colname="3"> Hiermee wordt de audiotrack opgehaald die is geselecteerd met <span class="codeph"> selectAudioTrack </span>. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectAudioTrack ( AudioTrack AudioTrack )  </span> </td> 
   <td colname="3"> Hiermee selecteert u een audiotrack als huidige audiotrack. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Timed metadata</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean hasTimedMetadata();  </span> </td> 
   <td colname="3"> True if the stream has associated timed metadata. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;timedmetadata&gt; ListgetTimedMetadata();  </span> </td> 
   <td colname="3"> Bevat een lijst met de metagegevensobjecten met tijdslimiet die aan de stream zijn gekoppeld. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Meerdere profielen (bitsnelheden)</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isDynamic();  </span> </td> 
   <td colname="3"> True if the stream is a multiple bit rate (MBR) stream. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;profile&gt; ListgetProfiles();  </span> </td> 
   <td colname="3"> Verstrekt een lijst van de bijbehorende profielen van het beetjetarief. Voor elk profiel kunt u de bitsnelheid en de hoogte en breedte van het profiel ophalen. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Profiel getSelectedProfile()  </span> </td> 
   <td colname="3"> Hiermee wordt het geselecteerde profiel opgehaald. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Steen spelen</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isTrickPlaySupported();  </span> </td> 
   <td colname="3"> True if the player supports fast forward, rewind, and resume. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt; Float=""&gt; ListgetAvailablePlaybackRates()  </span> </td> 
   <td colname="3"> Verstrekt de lijst van beschikbare playbacktarieven in de context van de truc-speleigenschap. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Float getSelectedPlaybackRate()  </span> </td> 
   <td colname="3"> Hiermee wordt de momenteel geselecteerde afspeelsnelheid opgehaald. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> MediaPlayerItemConfig getConfig()  </span> </td> 
   <td colname="3"> Retourneert de <span class="codeph"> MediaPlayerItemConfig </span>-instantie die aan dit item is gekoppeld. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Mediabron</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> MediaResource getResource();  </span> </td> 
   <td colname="3"> Retourneert de mediabron die aan dit item is gekoppeld. </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="2"> <span class="codeph"> int getResourceId()  </span> </td> 
   <td colname="3"> Retourneert de media-id die aan dit item is gekoppeld. Deze id wordt ingesteld wanneer het item wordt geladen met <span class="codeph"> MediaPlayerItemLoader.load </span>. </td> 
  </tr> 
 </tbody> 
</table>
