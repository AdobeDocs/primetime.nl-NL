---
description: Deze tabel bevat gedetailleerde informatie over meldingen van FOUTtypen.
seo-description: Deze tabel bevat gedetailleerde informatie over meldingen van FOUTtypen.
seo-title: FOUTmeldingscodes
title: FOUTmeldingscodes
uuid: 50624782-3d0b-4ac4-b883-355c1f7e9bff
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 4%

---


# FOUTmeldingscodes{#error-notification-codes}

Deze tabel bevat gedetailleerde informatie over meldingen van FOUTtypen.

<!--<a id="section_D29404228F5E4B818642CBA6A0D39546"></a>-->

De meeste fouten bevatten relevante metagegevens, bijvoorbeeld de URL van de bron die niet is gedownload. Sommige meldingen bevatten metagegevens om op te geven of het probleem is opgetreden in de hoofdvideo-inhoud, in de alternatieve audio-inhoud of in een advertentie.

<table frame="all" colsep="1" rowsep="1" id="table_8B61210A406A45ACBE37FC29729DDE22"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Code </th> 
   <th colname="2" class="entry"> Naam </th> 
   <th colname="3" class="entry"> InnerNotification </th> 
   <th colname="4" class="entry"> Metagegevenstoetsen </th> 
   <th colname="5" class="entry"> Opmerkingen </th> 
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
   <td colname="5">Zie ook 106000 (
     <span class="codeph"> NATIVE_ERROR</span>).
   </td> 
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
   <td colname="3"> <p>Geen </p> </td> 
   <td colname="4"><span class="codeph"> BESCHRIJVING  </span> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101004  </span> </td> 
   <td colname="2"><span class="codeph"> CONTENT_ERROR  </span> </td> 
   <td colname="3"><span class="codeph"> DOWNLOAD_ERROR  </span> </td> 
   <td colname="4"> </td> 
   <td colname="5"> <p>Er is een fout opgetreden tijdens het downloaden van een fragment of segment (zowel video als audio). </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101006  </span> </td> 
   <td colname="2"><span class="codeph"> SECURITY_ERROR  </span> </td> 
   <td colname="3"> </td> 
   <td colname="4"><span class="codeph"> URL  </span> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101008</span> </td> 
   <td colname="2"><span class="codeph"> PAUSE_ERROR  </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"> <span class="codeph"> BESCHRIJVING  </span> </td> 
   <td colname="5"> <p>Er is een fout opgetreden tijdens het uitvoeren van een pauzebewerking. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101009  </span> </td> 
   <td colname="2"><span class="codeph"> ZOEKEN_FOUT  </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> NATIVE_ERROR_CODE  </span><span class="codeph"> DESIRED_SEEK_POSITION  </span><span class="codeph"> DESIRED_SEEK_PERIOD  </span> </td> 
   <td colname="5"> <p>Er is een fout opgetreden tijdens het uitvoeren van een zoekbewerking. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101102  </span> </td> 
   <td colname="2"><span class="codeph"> PERIOD_INFO_ERROR  </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> BESCHRIJVING  </span> </td> 
   <td colname="5"> <p>Er is een fout opgetreden bij het ophalen van informatie over een inhoudsperiode. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101103  </span> </td> 
   <td colname="2"><span class="codeph"> RETRIEVE_TIME_ERROR  </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> BESCHRIJVING  </span> </td> 
   <td colname="5"> <p>Er is een fout opgetreden bij het ophalen van de afspeelpositie. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101104  </span> </td> 
   <td colname="2"><span class="codeph"> GET_QOS_DATA_ERROR  </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> BESCHRIJVING  </span> </td> 
   <td colname="5"> <p>Er is een fout opgetreden bij het ophalen van de QOS-informatie. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101200  </span> </td> 
   <td colname="2"><span class="codeph"> DOWNLOAD_ERROR  </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> URL  </span> </td> 
   <td colname="5"> <p>Er is een fout opgetreden bij het downloaden van gegevens. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Ongeldige resource  </b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 102100  </span> </td> 
   <td colname="2"><span class="codeph"> RESOURCE_LOAD_ERROR  </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> BESCHRIJVINGS </span><span class="codeph"> MIDDELEN  </span> </td> 
   <td colname="5"> <p>Er is een fout opgetreden bij het laden van een resource-item. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 102101  </span> </td> 
   <td colname="2"><span class="codeph"> RESOURCE_PLACEMENT_ FAILED  </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> CONTENT_ID  </span> </td> 
   <td colname="5"> <p>Er is een fout opgetreden bij het plaatsen van een bron op de afspeeltijdlijn. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Ad-verwerking  </b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104000  </span> </td> 
   <td colname="2"><span class="codeph"> AD_RESOLVER_FAIL  </span> </td> 
   <td colname="3"><span class="codeph"> AD_METADATA_INVALID  </span><span class="codeph"> AD_RESOLVER_INITIALIZATION_FAIL  </span><span class="codeph"> AD_RESOLVER_RESOLVE_FAIL  </span><span class="codeph"> AD_RESOLVER_SERVER_UNREACHABLE  </span> </td> 
   <td colname="4"> Geen </td> 
   <td colname="5"> Geen </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104001  </span> </td> 
   <td colname="2"><span class="codeph"> AD_RESOLVER_METADATA_INVALID  </span> </td> 
   <td colname="3"> <p>Geen </p> </td> 
   <td colname="4"> </td> 
   <td colname="5"> <p>Oplossen van toevoegen is mislukt vanwege ongeldige indeling voor ad-metagegevens. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104003  </span> </td> 
   <td colname="2"><span class="codeph"> AD_RESOLVER_RESOLVE_FAIL  </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> NATIVE_ERROR_CODE  </span> </td> 
   <td colname="5"> <p>Advertenties zijn niet opgelost met de insteekmodule. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104005  </span> </td> 
   <td colname="2"><span class="codeph"> AD_INSERTION_FAIL  </span> </td> 
   <td colname="3">Geen</td> 
   <td colname="4"><span class="codeph"> PROPOSED_AD_BREAK</span> </td> 
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
   <td colname="4"><span class="codeph"> RUNTIME_</span> <span class="codeph"> CODERUNTIME_CODE_</span> <span class="codeph"> MESSAGERESOURCE_</span> <span class="codeph"> URLRESOURCE_</span> <span class="codeph"> TYPERESOURCE_ID</span> <p><b>DRM-gegevens:</b> </p> <span class="codeph"> DRM_ERROR_</span> <span class="codeph"> STRINGRUNTIME_SUBERROR_CODE</span> </td> 
   <td colname="5"> <p>De AVE-bibliotheek op laag niveau heeft een fout gegenereerd. </p> <p>Zie <a href="../../c-psdk-dhls-1.4-events-and-notifications/notification-codes/c-psdk-dhls-1.4-native-error-summary.md" format="html" scope="external"> Details voor NATIVE_ERROR berichten</a> voor informatie over de waarden voor deze meta-gegevenssleutels. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106001  </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_CREATION_ERROR  </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> BESCHRIJVING  </span> </td> 
   <td colname="5"> <p>Er is een fout opgetreden bij het instantiëren van de bibliotheek op laag niveau van AVE. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106002  </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_RELEASE_ERROR  </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> BESCHRIJVING  </span> </td> 
   <td colname="5"> <p>Er is een fout opgetreden bij het loslaten van de bibliotheek op laag niveau van AVE. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106003  </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_RESOURCES_RELEASE_ERROR  </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> BESCHRIJVING  </span> </td> 
   <td colname="5"> <p>Er is een fout opgetreden bij het vrijgeven van de GPU-bronnen die door de AVE-bibliotheek worden gebruikt. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106004  </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_RESET_ERROR  </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> BESCHRIJVING  </span> </td> 
   <td colname="5"> <p>Er is een fout opgetreden bij het opnieuw instellen van de AVE-bibliotheek. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106005  </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_SET_VIEW_ERROR  </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> BESCHRIJVING  </span> </td> 
   <td colname="5"> <p>Er is een fout opgetreden bij het koppelen van een weergave aan de AVE-bibliotheek. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Alternatieve audio</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 109000  </span> </td> 
   <td colname="2"><span class="codeph"> AUDIO_TRACK_ERROR  </span> </td> 
   <td colname="3"><span class="codeph"> DOWNLOAD_ERROR  </span> </td> 
   <td colname="4"><span class="codeph"> AUDIO_TRACK_NAME  </span><span class="codeph"> AUDIO_TRACK_LANGUAGE  </span> </td> 
   <td colname="5"> <p>Er is een fout opgetreden met betrekking tot een audiotrack. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Algemeen</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><span class="codeph"> 19999  </span> </td> 
   <td colname="2"><span class="codeph"> GENERIC_ERROR  </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"> Geen </td> 
   <td colname="5"> <p>Hiermee wordt een algemene foutgebeurtenis gemarkeerd. Niet daadwerkelijk uitgegeven door TVSDK. Het is slechts een teller voor het eind van de waaier van numerieke codes die aan de foutengebeurtenissen van TVSDK beantwoorden. </p> </td> 
  </tr> 
 </tbody> 
</table>

