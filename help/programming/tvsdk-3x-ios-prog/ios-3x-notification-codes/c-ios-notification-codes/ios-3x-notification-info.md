---
description: Deze tabel bevat gedetailleerde informatie over meldingen van INFO-typen.
seo-description: Deze tabel bevat gedetailleerde informatie over meldingen van INFO-typen.
seo-title: INFO-meldingscodes
title: INFO-meldingscodes
uuid: 21297863-dac1-45a4-ac9d-309d1f746f8b
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# INFO-meldingscodes {#info-notification-codes}

Deze tabel bevat gedetailleerde informatie over meldingen van INFO-typen.

De meeste informatieve meldingen bevatten relevante metagegevens, bijvoorbeeld de URL van de bron die niet is gedownload. Sommige meldingen bevatten metagegevens om op te geven of het probleem is opgetreden in de hoofdvideo-inhoud, in de alternatieve audio-inhoud of in een advertentie.

<table frame="all" colsep="1" rowsep="1" id="table_503463046E764A87B10EB5D8B294EB23"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"><b>Code</b></th> 
   <th colname="2" class="entry"><b>Naam</b></th> 
   <th colname="3" class="entry"><b>Melding binnen</b></th> 
   <th colname="4" class="entry"><b>Metagegevenstoetsen</b></th> 
   <th colname="5" class="entry"><b>Opmerkingen</b></th> 
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
   <td colname="1"><span class="codeph"> 300000 </span> </td> 
   <td colname="2"><span class="codeph"> PLAYBACK_START </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"> Geen </td> 
   <td colname="5"> Het afspelen is gestart. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300001 </span> </td> 
   <td colname="2"><span class="codeph"> PLAYBACK_COMPLETE </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"> Geen </td> 
   <td colname="5"> Het afspelen is voltooid. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300002 </span> </td> 
   <td colname="2"><span class="codeph"> ZOEKEN_START </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"> <p> Geen </p> </td> 
   <td colname="5"> Er is een zoekbewerking gestart. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300003 </span> </td> 
   <td colname="2"><span class="codeph"> ZOEKEN_COMPLETE </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"> <p>Geen </p> </td> 
   <td colname="5"> Een zoekbewerking is voltooid. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300005 </span> </td> 
   <td colname="2"><span class="codeph"> PLAYER_STATE_CHANGE </span> </td> 
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
   <td colname="1"><span class="codeph"> 302000 </span> </td> 
   <td colname="2"><span class="codeph"> BITRATE_CHANGE </span> </td> 
   <td colname="3"> <p>Geen </p> </td> 
   <td colname="4"><span class="codeph"> BITRAAT </span> </td> 
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
   <td colname="1"><span class="codeph"> 304000 </span> </td> 
   <td colname="2"><span class="codeph"> AUDIO_TRACK_CHANGE </span> </td> 
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
   <td colname="1"><span class="codeph"> 307000 </span> </td> 
   <td colname="2"><span class="codeph"> SUBTITLES_TRACK_CHANGE </span> </td> 
   <td colname="3"> <p>Geen </p> </td> 
   <td colname="4"> <p>Geen </p> </td> 
   <td colname="5"> <p>De track voor ondertitels is gewijzigd. </p> </td> 
  </tr> 
 </tbody> 
</table>