---
description: Deze tabel bevat gedetailleerde informatie over meldingen van FOUTtypen.
seo-description: Deze tabel bevat gedetailleerde informatie over meldingen van FOUTtypen.
seo-title: FOUTmeldingscodes
title: FOUTmeldingscodes
uuid: cc21473d-924e-475d-96ea-352233f664ef
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

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
   <td colname="1"><b>Afspelen</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101000 </span> </td> 
   <td colname="2"><span class="codeph"> PLAYBACK_ERROR </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> BESCHRIJVING</span> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101004 </span> </td> 
   <td colname="2"><span class="codeph"> CONTENT_ERROR</span> </td> 
   <td colname="3"><span class="codeph"> DOWNLOAD_ERROR</span> </td> 
   <td colname="4"> </td> 
   <td colname="5"> Er is een fout opgetreden tijdens het downloaden van een fragment of segment (zowel video als audio). </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101008 </span> </td> 
   <td colname="2"><span class="codeph"> ZOEKEN_FOUT </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> NATIVE_ERROR_CODE </span><span class="codeph"> DESIRED_SEEK_POSITION </span><span class="codeph"> DESIRED_SEEK_PERIOD </span> </td> 
   <td colname="5"> Er is een fout opgetreden tijdens het uitvoeren van een zoekbewerking. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101009 </span> </td> 
   <td colname="2"><span class="codeph"> PAUSE_ERROR </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> BESCHRIJVING</span> </td> 
   <td colname="5"> Er is een fout opgetreden tijdens het uitvoeren van een pauzebewerking. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101102 </span> </td> 
   <td colname="2"><span class="codeph"> PERIOD_INFO_ERROR </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> BESCHRIJVING </span> </td> 
   <td colname="5"> Er is een fout opgetreden bij het ophalen van informatie over een inhoudsperiode. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101103 </span> </td> 
   <td colname="2"><span class="codeph"> RETRIEVE_TIME_ERROR </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> BESCHRIJVING </span> </td> 
   <td colname="5"> Er is een fout opgetreden bij het ophalen van de afspeelpositie. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101104 </span> </td> 
   <td colname="2"><span class="codeph"> GET_QOS_DATA_ERROR </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> BESCHRIJVING </span> </td> 
   <td colname="5"> Er is een fout opgetreden bij het ophalen van de QOS-informatie. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101200 </span> </td> 
   <td colname="2"><span class="codeph"> DOWNLOAD_ERROR </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> URL </span> </td> 
   <td colname="5"> Er is een fout opgetreden bij het downloaden van gegevens. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Ongeldige resource</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 102100 </span> </td> 
   <td colname="2"><span class="codeph"> RESOURCE_LOAD_ERROR </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> BESCHRIJVINGS </span><span class="codeph"> BRONNEN </span> </td> 
   <td colname="5"> Er is een fout opgetreden bij het laden van een resource-item. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 102101 </span> </td> 
   <td colname="2"><span class="codeph"> RESOURCE_PLACEMENT_ FAILED </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> CONTENT_ID </span> </td> 
   <td colname="5"> Er is een fout opgetreden bij het plaatsen van een bron op de afspeeltijdlijn. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Ad-verwerking</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104000 </span> </td> 
   <td colname="2"><span class="codeph"> AD_RESOLVER_FAIL </span> </td> 
   <td colname="3"><span class="codeph"> AD_METADATA_INVALID </span><span class="codeph"> AD_RESOLVER_INITIALIZATION_FAIL </span><span class="codeph"> AD_RESOLVER_RESOLVE_FAIL </span><span class="codeph"> AD_RESOLVER_SERVER_UNREACHABLE </span> </td> 
   <td colname="4"> Geen </td> 
   <td colname="5"> Geen </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104001 </span> </td> 
   <td colname="2"><span class="codeph"> AD_RESOLVER_METADATA_INVALID </span> </td> 
   <td colname="3"> <p>Geen </p> </td> 
   <td colname="4"><span class="codeph"> BESCHRIJVING</span> </td> 
   <td colname="5"> Oplossen van toevoegen is mislukt vanwege ongeldige indeling voor ad-metagegevens. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104003 </span> </td> 
   <td colname="2"><span class="codeph"> AD_RESOLVER_RESOLVE_FAIL </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> NATIVE_ERROR_CODE </span> </td> 
   <td colname="5"> Advertenties zijn niet opgelost met de insteekmodule. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104005 </span> </td> 
   <td colname="2"><span class="codeph"> AD_INSERTION_FAIL </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> PROPOSED_AD_BREAK</span> </td> 
   <td colname="5"> Oplossingsfase van advertentie is mislukt. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Oorspronkelijk</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106000 </span> </td> 
   <td colname="2"><span class="codeph"> NATIVE_ERROR </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"> <span class="codeph"> NATIVE_ERROR_CODE </span> <span class="codeph"> NATIVE_ERROR_NAME </span><span class="codeph"> DESCRIPTION </span> <span class="codeph"> -BESCHRIJVING</span> <p><b>DRM-gegevens:</b> </p> <span class="codeph"> DRM_ERROR_STRING</span> <span class="codeph"> NATIVE_SUBERROR_CODE</span> </td> 
   <td colname="5"> <p>De AVE-bibliotheek op laag niveau heeft een fout gegenereerd. </p> <p>Zie <a href="../../../tvsdk-1.4-for-android/android-1.4-tvsdk-notification/notification-codes/native-error-summary/android-1.4-native-error-summary.md" format="html" scope="external"> Details voor de NATIVE_ERROR berichten</a> voor informatie over de waarden voor deze meta-gegevenssleutels. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106001 </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_CREATION_ERROR </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> BESCHRIJVING </span> </td> 
   <td colname="5"> Er is een fout opgetreden bij het instantiëren van de bibliotheek op laag niveau van AVE. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106002 </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_RELEASE_ERROR </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> BESCHRIJVING </span> </td> 
   <td colname="5"> Er is een fout opgetreden bij het loslaten van de bibliotheek op laag niveau van AVE. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106003 </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_RESOURCES_RELEASE_ERROR </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> BESCHRIJVING </span> </td> 
   <td colname="5"> Er is een fout opgetreden bij het vrijgeven van de GPU-bronnen die door de AVE-bibliotheek worden gebruikt. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106004 </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_RESET_ERROR </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> BESCHRIJVING </span> </td> 
   <td colname="5"> Er is een fout opgetreden bij het opnieuw instellen van de AVE-bibliotheek. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106005 </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_SET_VIEW_ERROR </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> BESCHRIJVING</span> </td> 
   <td colname="5"> Er is een fout opgetreden bij het koppelen van een weergave aan de AVE-bibliotheek. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Configuratie</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 107000 </span> </td> 
   <td colname="2"><span class="codeph"> SET_VOLUME_ERROR </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> BESCHRIJVINGSVOLUME </span> </td> 
   <td colname="5"> Er is een fout opgetreden bij het instellen van het volumeniveau. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 107001 </span> </td> 
   <td colname="2"><span class="codeph"> SET_BUFFER_TIME_ERROR </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION </span><span class="codeph"> PLAY_BUFFER_TIME </span> </td> 
   <td colname="5"> Er is een fout opgetreden bij het wijzigen van de bufferparameters. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 107002 </span> </td> 
   <td colname="2"><span class="codeph"> SET_CC_VISIBILITY_ ERROR </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> BESCHRIJVING</span> </td> 
   <td colname="5"> Er is een fout opgetreden bij het wijzigen van de zichtbaarheid van de CC-tracks. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 107003 </span> </td> 
   <td colname="2"><span class="codeph"> SET_CC_STYLING_ ERROR </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> BESCHRIJVING</span> </td> 
   <td colname="5"> Er is een fout opgetreden tijdens het wijzigen van de opmaakopties voor de CC-tracks. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 107004 </span> </td> 
   <td colname="2"><span class="codeph"> SET_ABR_PARAMETERS_ERROR </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> BESCHRIJVING </span> </td> 
   <td colname="5"> Er is een fout opgetreden bij het wijzigen van de ABR-besturingsparameters. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 107005 </span> </td> 
   <td colname="2"><span class="codeph"> SET_BUFFER_PARAMETERS_ERROR </span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION </span><span class="codeph"> INITIAL_BUFFER_TIME </span><span class="codeph"> PLAY_BUFFER_TIME </span> </td> 
   <td colname="5"> Er is een fout opgetreden bij het wijzigen van de bufferbesturingsparameters. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Alternatieve audio</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 109000 </span> </td> 
   <td colname="2"><span class="codeph"> AUDIO_TRACK_ERROR </span> </td> 
   <td colname="3"><span class="codeph"> DOWNLOAD_ERROR </span> </td> 
   <td colname="4"><span class="codeph"> AUDIO_TRACK_NAME </span><span class="codeph"> AUDIO_TRACK_LANGUAGE </span> </td> 
   <td colname="5"> Er is een fout opgetreden met betrekking tot een audiotrack. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Algemeen</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><span class="codeph"> 199999 </span> </td> 
   <td colname="2"><span class="codeph"> GENERIC_ERROR</span> </td> 
   <td colname="3"> Geen </td> 
   <td colname="4"> Geen </td> 
   <td colname="5"> Hiermee wordt een algemene foutgebeurtenis gemarkeerd. Niet daadwerkelijk uitgegeven door TVSDK. Dit is slechts een markering voor het einde van het bereik van numerieke codes die overeenkomen met TVSDK-foutgebeurtenissen. </td> 
  </tr> 
 </tbody> 
</table>

