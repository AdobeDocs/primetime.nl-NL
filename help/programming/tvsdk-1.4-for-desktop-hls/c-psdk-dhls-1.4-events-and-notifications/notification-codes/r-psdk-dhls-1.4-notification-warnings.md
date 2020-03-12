---
description: Deze lijst bewijst gedetailleerde informatie over WARN. type meldingen.
seo-description: Deze lijst bewijst gedetailleerde informatie over WARN. type meldingen.
seo-title: WAARSCHUWINGSmeldingscodes
title: WAARSCHUWINGSmeldingscodes
uuid: 1ce5be07-f5bf-443c-b907-9768633e1300
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# WAARSCHUWINGSmeldingscodes{#warning-notification-codes}

Deze lijst bewijst gedetailleerde informatie over WARN. type meldingen.

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
   <td colname="1"><b>Oplossen van advertentie </b> </td> 
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
   <td colname="5"> <p>De AVE-bibliotheek op laag niveau heeft een fout gegenereerd. </p> <p>Zie <a href="../../c-psdk-dhls-1.4-events-and-notifications/notification-codes/c-psdk-dhls-1.4-native-error-summary.md" format="html" scope="external"> Details voor de NATIVE_ERROR berichten</a> voor gedetailleerde informatie over de waarden voor deze meta-gegevensgebieden. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="4"><b>DRM</b> <p><span class="codeph"> NATIVE_SUBERROR_CODE</span> <span class="codeph"> DRM_ERROR_STRING</span> </p> </td> 
   <td colname="5">DRM-kleine foutcode en fouttekenreeks van de DRM-server. Zie <a href="../../c-psdk-dhls-1.4-events-and-notifications/notification-codes/c-psdk-dhls-1.4-native-error-summary.md" format="html" scope="external"> Details voor de NATIVE_ERROR berichten</a> voor gedetailleerde informatie over de waarden voor deze meta-gegevensgebieden.
   </td> 
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

