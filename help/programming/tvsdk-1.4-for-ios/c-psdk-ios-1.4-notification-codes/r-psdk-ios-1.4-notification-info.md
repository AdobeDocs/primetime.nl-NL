---
description: Deze tabel bevat gedetailleerde informatie over meldingen van INFO-typen.
title: INFO-meldingscodes
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 4%

---


# INFO-meldingscodes{#info-notification-codes}

Deze tabel bevat gedetailleerde informatie over meldingen van INFO-typen.

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
   <td colname="4"> <p> Geen </p> </td> 
   <td colname="5"> Er is een zoekbewerking gestart. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300003  </span> </td> 
   <td colname="2"><span class="codeph"> ZOEKEN_COMPLETE  </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"> <p>Geen </p> </td> 
   <td colname="5"> Een zoekbewerking is voltooid. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300005  </span> </td> 
   <td colname="2"><span class="codeph"> PLAYER_STATE_CHANGE  </span> </td> 
   <td colname="3"> <p>Geen </p> </td> 
   <td colname="4"> <p>Geen </p> </td> 
   <td colname="5"> De spelerstatus is gewijzigd. Wanneer de status ERROR is, is het binnenste bericht het voorwerp van het foutenmelding dat de schakelaar aan de staat van de FOUT teweegbracht. </td> 
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
   <td colname="4"><span class="codeph"> BITRAAT  </span> </td> 
   <td colname="5"> De bitsnelheid van de video is gewijzigd. </td> 
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
   <td colname="4"> <p>Geen </p> </td> 
   <td colname="5"> <p>De audiotrack is gewijzigd. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Ondertitels</b> </td> 
   <td colname="2"> </td>
   <td colname="3"> </td>
   <td colname="4"> </td>
   <td colname="5"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 307000  </span> </td> 
   <td colname="2"><span class="codeph"> SUBTITLES_TRACK_CHANGE  </span> </td> 
   <td colname="3"> <p>Geen </p> </td> 
   <td colname="4"> <p>Geen </p> </td> 
   <td colname="5"> <p>De track voor ondertitels is gewijzigd. </p> </td> 
  </tr> 
 </tbody> 
</table>

