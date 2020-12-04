---
description: Deze tabel bevat gedetailleerde informatie over meldingen van INFO-typen.
seo-description: Deze tabel bevat gedetailleerde informatie over meldingen van INFO-typen.
seo-title: INFO-meldingscodes
title: INFO-meldingscodes
uuid: 27117707-be3d-4935-a193-85776edd26ce
translation-type: tm+mt
source-git-commit: b9e98ef2b4246fdfd79ebcd91db344c97367d661
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 4%

---


# INFO-meldingscodes{#info-notification-codes}

Deze tabel bevat gedetailleerde informatie over meldingen van INFO-typen.

## Sectietitel {#section_ED4302E363AE48CBA2C3E0B71AE612D8}

De meeste informatieve meldingen bevatten relevante metagegevens, bijvoorbeeld de URL van de bron die niet is gedownload. Sommige meldingen bevatten metagegevens om op te geven of het probleem is opgetreden in de hoofdvideo-inhoud, in de alternatieve audio-inhoud of in een advertentie.

<table frame="all" colsep="1" rowsep="1" id="table_503463046E764A87B10EB5D8B294EB23"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Code </th> 
   <th colname="2" class="entry"> Naam </th> 
   <th colname="3" class="entry"> Melding binnen </th> 
   <th colname="4" class="entry"> Metagegevenstoetsen </th> 
   <th colname="5" class="entry"> Opmerkingen </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><b>Afspelen</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300000  </span> </td> 
   <td colname="2"><span class="codeph"> PLAYBACK_START  </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"> Geen </td> 
   <td colname="5"> Het afspelen is gestart. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300001  </span> </td> 
   <td colname="2"><span class="codeph"> PLAYBACK_COMPLETE  </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"> Geen </td> 
   <td colname="5"> Het afspelen is voltooid. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300002  </span> </td> 
   <td colname="2"><span class="codeph"> ZOEKEN_START  </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> ZOEKEN_TIME</span> </td> 
   <td colname="5"> Er is een zoekbewerking gestart. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300003  </span> </td> 
   <td colname="2"><span class="codeph"> ZOEKEN_COMPLETE  </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> ZOEKEN_TIME</span> </td> 
   <td colname="5"> Een zoekbewerking is voltooid. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300004  </span> </td> 
   <td colname="2"><span class="codeph"> CONTENT_CHANGE  </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"> <span class="codeph"> CONTENT_</span> <span class="codeph"> IDCURRENT_MEDIA_TIME</span> </td> 
   <td colname="5"> De huidige afspeeltijd heeft de rand tussen de hoofd- en alternatieve inhoud overschreden. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300005  </span> </td> 
   <td colname="2"><span class="codeph"> PLAYER_STATE_CHANGE  </span> </td> 
   <td colname="3"> <p>Elke foutmelding. </p> </td> 
   <td colname="4"><span class="codeph"> STAAT  </span> </td> 
   <td colname="5"> De spelerstatus is gewijzigd. Wanneer de status ERROR is, is het binnenste bericht het voorwerp van het foutenmelding dat de schakelaar aan de staat van de FOUT teweegbracht. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300100  </span> </td> 
   <td colname="2"><span class="codeph"> LOAD_INFO_AVAILABLE  </span> </td> 
   <td colname="3"> <p>Geen </p> </td> 
   <td colname="4"> <span class="codeph"> FRAGMENT_</span> <span class="codeph"> URLFRAGMENT_</span> <span class="codeph"> SIZEFRAGMENT_DOWNLOAD_</span> <span class="codeph"> DURATIONPERIOD_INDEX</span> </td> 
   <td colname="5"> Verstrekt informatie met betrekking tot de manier de videosegmenten worden gedownload. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300101  </span> </td> 
   <td colname="2"><span class="codeph"> VIDEO_SIZE_CHANGED  </span> </td> 
   <td colname="3"> <p>Geen </p> </td> 
   <td colname="4"> <span class="codeph"> HOOGTE</span> <p><span class="codeph"> BREEDTE</span> </p> </td> 
   <td colname="5"> De grootte van het afspeelvenster van de video is gewijzigd. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Adaptieve bitsnelheden (ABR)</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 302000  </span> </td> 
   <td colname="2"><span class="codeph"> BITRATE_CHANGE  </span> </td> 
   <td colname="3"> <p>Geen </p> </td> 
   <td colname="4"><span class="codeph"> BITRATE  </span><span class="codeph"> CURRENT_MEDIA_TIME  </span> </td> 
   <td colname="5"> De bitsnelheid van de video is gewijzigd. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Ad-verwerking  </b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303000  </span> </td> 
   <td colname="2"><span class="codeph"> TIMELINE_CHANGE  </span> </td> 
   <td colname="3"> <p>Geen </p> </td> 
   <td colname="4"><span class="codeph"> CONTENT_ID  </span><span class="codeph"> PERIOD_INDEX  </span> </td> 
   <td colname="5"> De tijdlijn is gewijzigd (er is bijvoorbeeld alternatieve inhoud toegevoegd of verwijderd). </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303001  </span> </td> 
   <td colname="2"><span class="codeph"> AD_BREAK_PLACEMENT_COMPLETE  </span> </td> 
   <td colname="3"> <p>Geen </p> </td> 
   <td colname="4"> <span class="codeph"> PROPOSED_AD_</span> <span class="codeph"> BREAKACCEPTED_AD_BREAK</span> </td> 
   <td colname="5"> Een voorgesteld ad-einde is geaccepteerd door TVSDK en (geheel of slechts gedeeltelijk) op de afspeeltijdlijn geplaatst. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303002  </span> </td> 
   <td colname="2"><span class="codeph"> AD_BREAK_START  </span> </td> 
   <td colname="3"> <p>Geen </p> </td> 
   <td colname="4"><span class="codeph"> AD_BREAK  </span> </td> 
   <td colname="5"> Het afspelen van een bepaald advertentieeinde is begonnen. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303003  </span> </td> 
   <td colname="2"><span class="codeph"> AD_BREAK_COMPLETE  </span> </td> 
   <td colname="3"> <p>Geen </p> </td> 
   <td colname="4"><span class="codeph"> AD_BREAK  </span> </td> 
   <td colname="5"> Het afspelen van een bepaald advertentieeinde is voltooid. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303004  </span> </td> 
   <td colname="2"><span class="codeph"> AD_START  </span> </td> 
   <td colname="3"> <p>Geen </p> </td> 
   <td colname="4"> <span class="codeph"> AD_BREAK</span> <p><span class="codeph"> AD</span> </p> </td> 
   <td colname="5"> Het afspelen van een bepaalde advertentie is gestart. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303005  </span> </td> 
   <td colname="2"><span class="codeph"> AD_COMPLETE  </span> </td> 
   <td colname="3"> <p>Geen </p> </td> 
   <td colname="4"> <span class="codeph"> AD_BREAK</span> <p><span class="codeph"> AD</span> </p> </td> 
   <td colname="5"> Het afspelen van een bepaalde advertentie is voltooid. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303006  </span> </td> 
   <td colname="2"><span class="codeph"> AD_PROGRESS  </span> </td> 
   <td colname="3"> <p>Geen </p> </td> 
   <td colname="4"> <span class="codeph"> AD_BREAK</span> <p><span class="codeph"> AD</span> </p> <span class="codeph"> VOORUITGANG</span> </td> 
   <td colname="5"> Het afspelen van een bepaalde advertentie heeft een bepaald percentage van die bepaalde advertentie bereikt. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Laatstgebonden audio (LBA)</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 304000  </span> </td> 
   <td colname="2"><span class="codeph"> AUDIO_TRACK_CHANGE  </span> </td> 
   <td colname="3"> <p>Geen </p> </td> 
   <td colname="4"><span class="codeph"> TRACK_ID  </span><span class="codeph"> CURRENT_MEDIA_TIME  </span> </td> 
   <td colname="5"> <p>De audiotrack is gewijzigd. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>DRM</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 305000  </span> </td> 
   <td colname="2"><span class="codeph"> DRM_METADATA_AVAILABLE  </span> </td> 
   <td colname="3"> <p>Geen </p> </td> 
   <td colname="4"><span class="codeph"> PREFETCH_TIMESTAMP  </span> </td> 
   <td colname="5"> <p>Er zijn nieuwe DRM-gegevens beschikbaar. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Algemeen</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><span class="codeph"> 39999  </span> </td> 
   <td colname="2"><span class="codeph"> GENERIC_INFO  </span> </td> 
   <td colname="3"> <p>Geen </p> </td> 
   <td colname="4"> <p>Geen </p> </td> 
   <td colname="5"> <p>Hiermee wordt een algemene informatiegebeurtenis gemarkeerd. Niet daadwerkelijk uitgegeven door TVSDK. Het is slechts een teller voor het eind van de waaier van numerieke codes die aan TVSDK informatiegebeurtenissen beantwoorden. </p> </td> 
  </tr> 
 </tbody> 
</table>

