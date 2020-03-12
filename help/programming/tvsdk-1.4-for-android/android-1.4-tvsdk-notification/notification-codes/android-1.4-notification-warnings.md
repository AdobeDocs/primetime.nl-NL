---
description: Deze lijst bewijst gedetailleerde informatie over WARN type berichten.
seo-description: Deze lijst bewijst gedetailleerde informatie over WARN type berichten.
seo-title: WAARSCHUWINGSmeldingscodes
title: WAARSCHUWINGSmeldingscodes
uuid: 32b54e6c-f107-4e8e-aad6-34e1057719b0
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# WAARSCHUWINGSmeldingscodes {#warning-notification-codes}

Deze lijst bewijst gedetailleerde informatie over WARN type berichten.

<!--<a id="section_F25366B6703040E3ADA993C113618F01"></a>-->

De meeste waarschuwingen bevatten relevante metagegevens, bijvoorbeeld de URL van de bron die niet is gedownload. Sommige meldingen bevatten metagegevens om op te geven of het probleem is opgetreden in de hoofdvideo-inhoud, in de alternatieve audio-inhoud of in een advertentie.

<table frame="all" colsep="1" rowsep="1" id="table_C24772DF203B4DB2ACE6B475698C4C58"> 
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
   <td colname="1"><span class="codeph"> 200000 </span> </td> 
   <td colname="2"><span class="codeph"> PLAYBACK_OPERATION_FAIL </span> </td> 
   <td colname="3"><span class="codeph"> AUDIO_TRACK_ERROR </span><span class="codeph"> SEEK_ERROR </span> </td> 
   <td colname="4"><span class="codeph"> BESCHRIJVING </span> </td> 
   <td colname="5"> <p>Een afspeelbewerking is mislukt, maar het afspelen kan worden voortgezet. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Oplossen van advertentie</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 201000 </span> </td> 
   <td colname="2"><span class="codeph"> AD_RESOLVER_FAIL </span> </td> 
   <td colname="3"><span class="codeph"> AD_RESOLVER_RESOLVE_FAIL </span><span class="codeph"> RESOURCE_PLACEMENT_FAILED </span><span class="codeph"> AD_RESOLVER_METADATA_INVALID </span> </td> 
   <td colname="4"> <p>Geen </p> </td> 
   <td colname="5"> <p>De ad-resolver heeft de advertentie-inhoud niet opgelost/ingevoegd. Het afspelen kan worden voortgezet. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 201002</span> </td> 
   <td colname="2"><span class="codeph"> AD_ASSET_FAILED_TO_LOAD</span> </td> 
   <td colname="3"> <p>Geen </p> </td> 
   <td colname="4"><span class="codeph"> AD_ASSET, INTERNAL_ERROR</span> </td> 
   <td colname="5"> <p>Er is een fout opgetreden bij het laden van een advertentie. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 201003</span> </td> 
   <td colname="2"><span class="codeph"> AD_RESOLVER_RETURNED_NO_ADS</span> </td> 
   <td colname="3"> <p>Geen </p> </td> 
   <td colname="4"><span class="codeph"> INTERNAL_ERROR, AD_ID,DESCRIPTION</span> </td> 
   <td colname="5"> <p>Oplossen van advertentie is mislukt vanwege een ongeldige VAST-URL of omdat er geen advertentie is geretourneerd vanuit de VAST-wrapper. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Achtergrondmanifesten</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 204000 </span> </td> 
   <td colname="2"><span class="codeph"> BACKGROUND_MANIFEST_ WARNING</span> </td> 
   <td colname="3"> <p>Geen </p> </td> 
   <td colname="4"><span class="codeph"> BACKGROUND_MANIFEST_WARNING_ERROR</span><span class="codeph"> BACKGROUND_MANIFEST_WARNING_NAME</span> <span class="codeph"> DESCRIPTION</span> </td> 
   <td colname="5"> <p> Fout in downloaden achtergrondmanifest. Enig probleem bij het bijwerken van het achtergrondmanifest wordt verzonden als een TVSDK-waarschuwing en zorgt er niet voor dat het afspelen wordt gestopt. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 204001 </span> </td> 
   <td colname="2"><span class="codeph"> INVALID_SEEK_WARNING</span> </td> 
   <td colname="3"> <p>Geen </p> </td> 
   <td colname="4"><span class="codeph"> BESCHRIJVING</span> </td> 
   <td colname="5"> <p> </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Oorspronkelijk</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1" morerows="1"><span class="codeph"> 209100 </span> </td> 
   <td colname="2" morerows="1"><span class="codeph"> NATIVE_WARNING </span> </td> 
   <td colname="3" morerows="1"> <p>Geen </p> </td> 
   <td colname="4"><b>AVE</b> <p><span class="codeph"> NATIVE_ERROR_CODE </span><span class="codeph"> NATIVE_ERROR_NAME </span><span class="codeph"> DESCRIPTION </span> </p> </td> 
   <td colname="5"> <p>De AVE-bibliotheek op laag niveau heeft een fout gegenereerd. </p> <p>Zie <a href="../../../tvsdk-1.4-for-android/android-1.4-tvsdk-notification/notification-codes/native-error-summary/android-1.4-native-error-summary.md" format="html" scope="external"> Details voor de NATIVE_ERROR berichten</a> voor gedetailleerde informatie over de waarden voor deze meta-gegevensgebieden. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="4"><b>DRM</b> <p><span class="codeph"> NATIVE_SUBERROR_CODE</span> <span class="codeph"> DRM_ERROR_STRING</span> </p> </td> 
   <td colname="5"> DRM-kleine foutcode en fouttekenreeks van de DRM-server. Zie <a href="../../../tvsdk-1.4-for-android/android-1.4-tvsdk-notification/notification-codes/native-error-summary/android-1.4-native-error-summary.md" format="html" scope="external"> Details voor de NATIVE_ERROR berichten</a> voor gedetailleerde informatie over de waarden voor deze meta-gegevensgebieden.</td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>TimeRangeCollection</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 210000 </span> </td> 
   <td colname="2"><span class="codeph"> UNDEFINED_TIME_RANGES </span> </td> 
   <td colname="3"> <p>Geen </p> </td> 
   <td colname="4"> Geen </td> 
   <td colname="5"> De ad signalerende wijze wordt gedefinieerd als douanewaaiers maar er zijn geen waaiers bepaald. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 210001 </span> </td> 
   <td colname="2"><span class="codeph"> INVALID_TIME_RANGES </span> </td> 
   <td colname="3"> <p>Geen </p> </td> 
   <td colname="4"><span class="codeph"> BESCHRIJVING </span> </td> 
   <td colname="5"> <p> Een of meer tijdbereiken zijn ongeldig en worden genegeerd of gewijzigd. </p> <p> DESCRIPTION is een tekenreeks met een beschrijving van de ongeldige bereiken. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Steen, modus</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 280000 </span> </td> 
   <td colname="2"><span class="codeph"> TRICKPLAY_RATE_CHANGE_FAIL</span> </td> 
   <td colname="3"> <p>Geen </p> </td> 
   <td colname="4"><span class="codeph"> BESCHRIJVING</span> </td> 
   <td colname="5"> <p> Snelheidswijziging mislukt. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Algemeen</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><span class="codeph"> 299999 </span> </td> 
   <td colname="2"><span class="codeph"> GENERIC_WARNING </span> </td> 
   <td colname="3"> <p>Geen </p> </td> 
   <td colname="4"> <p>Geen </p> </td> 
   <td colname="5"> <p>Hiermee wordt een algemene waarschuwingsgebeurtenis gemarkeerd. Niet daadwerkelijk uitgegeven door TVSDK. Het is slechts een markering voor het einde van de reeks numerieke codes die overeenkomt met waarschuwingsgebeurtenissen. </p> </td> 
  </tr> 
 </tbody> 
</table>

>[OPMERKING!] addID en source (URL) kunnen worden opgehaald via PTAdAsset in de metagegevens van de melding met de `AD_ASSET` sleutel.
