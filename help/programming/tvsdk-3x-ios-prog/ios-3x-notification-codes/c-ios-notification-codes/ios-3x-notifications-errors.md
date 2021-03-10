---
description: Het TVSDK-meldingssysteem produceert verschillende fouten, waarschuwingen en informatieve kennisgevingen die diagnostische metagegevens bieden.
title: FOUTmeldingscodes
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 5%

---


# FOUTmeldingscodes {#error-notification-codes}

Deze tabel bevat gedetailleerde informatie over meldingen van FOUTtypen.

De meeste fouten bevatten relevante metagegevens, bijvoorbeeld de URL van de bron die niet is gedownload. Sommige meldingen bevatten metagegevens om op te geven of het probleem is opgetreden in de hoofdvideo-inhoud, in de alternatieve audio-inhoud of in een advertentie.

<table frame="all" colsep="1" rowsep="1" id="table_8B61210A406A45ACBE37FC29729DDE22"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"><b>Code</b></th> 
   <th colname="2" class="entry"><b>Naam</b></th> 
   <th colname="3" class="entry"><b>InnerNotification</b></th> 
   <th colname="4" class="entry"><b>Metagegevenstoetsen</b></th> 
   <th colname="5" class="entry"><b>Opmerkingen</b></th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><b>DRM</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 100000  </span> </td> 
   <td colname="2"><span class="codeph"> DRM_ERROR  </span> </td> 
   <td colname="3"> </td> 
   <td colname="4"><span class="codeph"> MAJOR_DRM_CODE  </span><span class="codeph"> MINOR_DRM_CODE  </span><span class="codeph"> DESCRIPTION  </span> </td> 
   <td colname="5"></td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Afspelen</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101000  </span> </td> 
   <td colname="2"><span class="codeph"> PLAYBACK_ERROR  </span> </td> 
   <td colname="3"></td> 
   <td colname="4"></td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101001  </span> </td> 
   <td colname="2"><span class="codeph"> NATIVE_PLAYBACK_ERROR  </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION  </span><span class="codeph"> INTERNAL_ERROR  </span><span class="codeph"> URL  </span> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101008  </span> </td> 
   <td colname="2"><span class="codeph"> ZOEKEN_FOUT  </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> BESCHRIJVING</span> </td> 
   <td colname="5"> <p>Er is een fout opgetreden tijdens het uitvoeren van een zoekbewerking. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101009  </span> </td> 
   <td colname="2"><span class="codeph"> PAUSE_ERROR  </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"> <p>Geen </p> </td> 
   <td colname="5"> <p>Er is een fout opgetreden tijdens het uitvoeren van een pauzebewerking. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101101  </span> </td> 
   <td colname="2"><span class="codeph"> AUDIO_TRACK_CHANGE_FAIL  </span> </td> 
   <td colname="3"><span class="codeph"> PLAYER_NOT_READY  </span> </td> 
   <td colname="4"> Geen </td> 
   <td colname="5"> <p>  </p> <p>  </p>
    <!-- workaround for PDF having too much negative kerning in column 2 --> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Ongeldige resource</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 102000  </span> </td> 
   <td colname="2"><span class="codeph"> INVALID_MEDIA_PLAYER_ITEM  </span> </td> 
   <td colname="3"> <p>Geen </p> </td> 
   <td colname="4"> Geen </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Ad-verwerking</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104001  </span> </td> 
   <td colname="2"><span class="codeph"> AD_RESOLVER_METADATA_INVALID  </span> </td> 
   <td colname="3"> <span class="codeph"> AD_NOT_INSERTED</span> </td> 
   <td colname="4"> <p>Geen </p> </td> 
   <td colname="5"> <p>Oplossen van toevoegen is mislukt vanwege ongeldige indeling voor ad-metagegevens. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104005  </span> </td> 
   <td colname="2"><span class="codeph"> AD_INSERTION_FAIL  </span> </td> 
   <td colname="3"> <span class="codeph"> AD_NOT_INSERTED  </span> </td> 
   <td colname="4"> <p>Geen </p> </td> 
   <td colname="5"> <p>Oplossingsfase van advertentie is mislukt. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104006  </span> </td> 
   <td colname="2"><span class="codeph"> AD_UNREACHABLE  </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"> Geen </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Oorspronkelijk</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106000  </span> </td> 
   <td colname="2"><span class="codeph"> NATIVE_ERROR  </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"> <span class="codeph"> INTERNAL_ERROR  </span> </td> 
   <td colname="5"> <p>Er is een iOS-fout op laag niveau opgetreden. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Configuratie</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 107002  </span> </td> 
   <td colname="2"><span class="codeph"> SET_CC_VISIBILITY_ ERROR  </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"> <p>Geen </p> </td> 
   <td colname="5"> <p>Er is een fout opgetreden bij het wijzigen van de zichtbaarheid van de CC-tracks. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 107003  </span> </td> 
   <td colname="2"><span class="codeph"> SET_CC_STYLING_ ERROR  </span> </td> 
   <td colname="3"> <span class="codeph"> NATIVE_ERROR  </span> </td> 
   <td colname="4"> <p>Geen </p> </td> 
   <td colname="5"> <p>Er is een fout opgetreden tijdens het wijzigen van de opmaakopties voor de CC-tracks. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>unieke iOS</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 170000  </span> </td> 
   <td colname="2"><span class="codeph"> AD_HLS_VERSION_INCOMPATIBLE  </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"> <span class="codeph"> AD_ASSET</span> </td> 
   <td colname="5"> <p>De HLS-versie van de advertenties is hoger dan de HLS-versie van de inhoud. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 170001  </span> </td> 
   <td colname="2"><span class="codeph"> ARGUMENT_ERROR  </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"> Geen </td> 
   <td colname="5"> <p>Argument-fout </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 170002  </span> </td> 
   <td colname="2"><span class="codeph"> M3U8_PARSER_ERROR  </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> BESCHRIJVING  </span> </td> 
   <td colname="5"> <p>Kan m3u8 niet parseren. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 170003  </span> </td> 
   <td colname="2"><span class="codeph"> WEBVTT_PARSER_ERROR  </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"> Geen </td> 
   <td colname="5"> <p>Kan Webvtt niet parseren. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 170004  </span> </td> 
   <td colname="2"><span class="codeph"> HLS_SEGMENT_ERROR  </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION  </span><span class="codeph"> URL  </span><span class="codeph"> INTERNAL_ERROR  </span> </td> 
   <td colname="5"> <p>Het segment overschrijdt de opgegeven bandbreedte voor de variant. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 170005  </span> </td> 
   <td colname="2"><span class="codeph"> MBR_MEDIASEQUENCE_OFFSYNC  </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"> Geen </td> 
   <td colname="5"> <p>Het aantal mediareeksen is niet synchroon voor alle HLS-streams van dit MBR. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 170006  </span> </td> 
   <td colname="2"><span class="codeph"> MISSING_FILE_ERROR  </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION  </span><span class="codeph"> URL  </span><span class="codeph"> INTERNAL_ERROR  </span> </td> 
   <td colname="5"> <p>Bestand ontbreekt of reageert niet. </p> <p>HTTP 404: Bestand niet gevonden. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 170007  </span> </td> 
   <td colname="2"><span class="codeph"> AD_EMPTY_RESPONSE  </span> </td> 
   <td colname="3"><span class="codeph"> AD_INSERTION_FAIL  </span> </td> 
   <td colname="4"> Geen </td> 
   <td colname="5"> <p>Kan de advertenties niet ophalen. Lege reactie. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 170008  </span> </td> 
   <td colname="2"><span class="codeph"> AD_TIMEOUT  </span> </td> 
   <td colname="3"><span class="codeph"> AD_INSERTION_FAIL  </span> </td> 
   <td colname="4"> Geen </td> 
   <td colname="5"> <p>Kan de advertenties niet ophalen. Time-outfout. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 170009  </span> </td> 
   <td colname="2"><span class="codeph"> SUBTITLES_TRACK_CHANGE_FAIL  </span> </td> 
   <td colname="3"><span class="codeph"> PLAYER_NOT_READY  </span> </td> 
   <td colname="4"> Geen </td> 
   <td colname="5"> <p>Fout bij het wijzigen van de track voor ondertitels. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 170010  </span> </td> 
   <td colname="2"><span class="codeph"> SiteCatalyst_ERROR  </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> BESCHRIJVING  </span> </td> 
   <td colname="5"> <p>Fout in Site-katalysator. Zie beschrijving. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 170011  </span> </td> 
   <td colname="2"><span class="codeph"> AD_TARGET_DURATION_INCOMPATIBLE  </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"> <span class="codeph"> AD_ASSET</span> </td> 
   <td colname="5"> <p>De TARGET-DUUR van de steun is hoger dan de TARGET-DUUR van de inhoud. </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>adID en source (URL) kunnen worden opgehaald via `PTAdAsset` in de metagegevens van de melding met de `AD_ASSET`-toets.
>
>Het `[]` attribuut specificeert een facultatieve sleutel voor bericht.
