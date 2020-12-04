---
seo-title: Details voor de melding NATIVE_ERROR
title: Details voor de melding NATIVE_ERROR
uuid: 18c4da57-59de-41a8-a2ea-fef800565207
translation-type: tm+mt
source-git-commit: d2b8cb67c54fadb8e0e7d2bdc15e393fdce8550e
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---


# Details voor de melding NATIVE_ERROR {#details-for-the-native-error-notification}

Wanneer TVSDK een native fout afhandelt, worden enkele of alle volgende sleutelwaarden voor metagegevens ingesteld.

<table id="table_86A21619515B435DBB65DC4DFBB64B29"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Sleutelnaam metagegevens </th> 
   <th colname="col2" class="entry"> Waarde metagegevens </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> NATIVE_ERROR_CODE  </span> </td> 
   <td colname="col2"> 
    <pre>
      Native foutcode van de AVE. 
    </pre> Deze codes vertegenwoordigen het volgende: 
    <ul id="ul_330C626DE27B45A09E8851CC24768A07"> 
     <li id="li_0845A9BBB55545BDB49BD4F4802C0E54">DRM-fouten (codes 3300 tot en met 3367). Deze zijn hetzelfde als de equivalente Flash Player-foutcodes. </li> 
     <li id="li_98A571480C154CF0AE1DC101FF0834C4">Fouten bij het afspelen van video (-1 tot en met 89). </li> 
     <li id="li_D7C19955DEF94DA88B822C8C57D6D2F4">Cryptografiefouten (300 tot 307). </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> NATIVE_ERROR_NAME  </span> </td> 
   <td colname="col2"> Een tekenreeks die de naam van de fout bevat; bijvoorbeeld <span class="codeph"> AAXS_InvalidVoucher </span> of <span class="codeph"> DECODER_FAILED </span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> NATIVE_SUBERROR_CODE  </span> </td> 
   <td colname="col2"> Voor DRM-fouten worden ook subfoutcodes geretourneerd. Deze codes komen overeen met de <span class="codeph"> DRMErrorEvents </span> subfoutcode die door de Flash Player wordt geretourneerd. Wanneer het melden van fouten aan Adobe, omvat deze numerieke waarde voor het oplossen van problemenhulp. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> DRM_ERROR_STRING  </span> </td> 
   <td colname="col2"> Voor DRM, is dit uw koord van de douanefout van uw DRM serverplaatsing, als u om het even welk bepaalde. Neem dit ook op wanneer u fouten aan Adobe rapporteert. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> BESCHRIJVING  </span> </td> 
   <td colname="col2"> Tekenreeksbeschrijving van de fout. Meestal de URL van het medium. </td> 
  </tr> 
 </tbody> 
</table>

TVSDK ontvangt deze foutcodes en -tekenreeksen van de video-engine.

>[!IMPORTANT]
>
>Zie [Referentie DRM-foutbericht voor DRM-client](https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_client_error_message_reference.pdf) voor een volledige lijst met Adobe Primetime DRM-clientfoutcodes.