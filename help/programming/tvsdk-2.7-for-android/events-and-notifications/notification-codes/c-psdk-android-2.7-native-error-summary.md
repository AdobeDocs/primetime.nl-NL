---
seo-title: Details voor de melding NATIVE_ERROR
title: Details voor de melding NATIVE_ERROR
uuid: 750ee0e2-15d4-4602-9574-94015a6e1b57
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40
workflow-type: tm+mt
source-wordcount: '6888'
ht-degree: 2%

---


# Details voor de melding NATIVE_ERROR {#details-for-the-native-error-notification}

Wanneer TVSDK een native fout afhandelt, worden enkele of alle volgende waarden van metagegevenssleutels als tekenreeksen geretourneerd.

<table id="table_7F713B7A56024D8DA3C84E449D09CC91"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Sleutelnaam metagegevens </th> 
   <th colname="col2" class="entry"> Waarde metagegevens </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> NATIVE_ERROR_CODE</span> </td> 
   <td colname="col2"> <p>Native foutcode van de AVE. </p> <p>Deze codes vertegenwoordigen het volgende: 
     <ul id="ul_1F33D523DDFE4CE8B4F0DC279FF7E4F8"> 
      <li id="li_07A2D9BEE6364935A61EF3BD4AB6DE27">DRM-fouten (codes 3300 tot en met 3367). Deze zijn hetzelfde als de equivalente Flash Player-foutcodes </li> 
      <li id="li_433BA22DE3504AEEB623598BB4F939FA">Fouten bij het afspelen van video (-1 tot 89) </li> 
      <li id="li_B347CB151DB94DE0A1DDEB1B33D2DABA">Cryptografiefouten (300 tot 307) </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> NATIVE_ERROR</span> </td> 
   <td colname="col2">Korte beschrijving van de melding (bijvoorbeeld <span class="codeph"> AAXS_InvalidVoucher</span> of <span class="codeph"> DECODER_FAILED</span>). </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> BESCHRIJVING</span> </td> 
   <td colname="col2"> Lange beschrijving van het bericht (bewerking voor het oplossen van objecten is bijvoorbeeld mislukt). </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> PSDK_ERROR_CODE</span> </td> 
   <td colname="col2"><span class="codeph"> com.adobe.mediacore.</span> PSDKErrorCodenumeric-waarde als een tekenreeks (bijvoorbeeld "13"). </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> PSDK_ERROR</span> </td> 
   <td colname="col2"><span class="codeph"> com.adobe.mediacore.</span> PSDKErrorCodeas een tekenreeks (bijvoorbeeld  <span class="codeph"> kECNetworkError</span>). </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> WAARSCHUWING</span> </td> 
   <td colname="col2"> Beschrijving van de waarschuwing. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> FOUT</span> </td> 
   <td colname="col2"> Beschrijving van de fout. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>DRM</b> </td> 
   <td colname="col2"></td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> NATIVE_SUBERROR_CODE</span> </td> 
   <td colname="col2"> Kleine fout in de DRM-module. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> DRM_ERROR_STRING</span> </td> 
   <td colname="col2"> Beschrijving van de fout. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> DRM_ERROR_SERVER_URL</span> </td> 
   <td colname="col2"> URL van de DRM-server waarover TVSDK heeft geprobeerd te spreken. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>Fout bij laden van advertentiemanifest</b> </td> 
   <td colname="col2"></td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AD_URL</span> </td> 
   <td colname="col2"> URL van de inhoud die niet is geladen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AD_TYPE</span> </td> 
   <td colname="col2">Type van advertentie (een constante van <span class="codeph"> MediaResource.Type</span> enum). </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AD_DURATION</span> </td> 
   <td colname="col2"> Duur van advertentie in milliseconden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AD_ID</span> </td> 
   <td colname="col2"> Aan de advertentie toegewezen id. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>Bestandsfouten</b> </td> 
   <td colname="col2"></td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> DOWNLOAD_ERROR</span> </td> 
   <td colname="col2"> Beschrijving van de fout tijdens het downloaden van mediabestanden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> URL</span> </td> 
   <td colname="col2"> URL of bestand dat wordt gedownload. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> MANIFEST_ERROR</span> </td> 
   <td colname="col2"> Beschrijving van fout tijdens downloaden manifestbestand. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> CONTENT_ERROR</span> </td> 
   <td colname="col2">Beschrijving van de fout tijdens het downloaden van het fragment (bijvoorbeeld <span class="codeph"> ts</span>). </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>Audiotrackfouten</b> </td> 
   <td colname="col2"></td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AUDIO_TRACK_NAME</span> </td> 
   <td colname="col2"> Naam van de audiotrack die niet is geladen, zoals opgegeven in het manifest. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AUDIO_TRACK_LANGUAGE</span> </td> 
   <td colname="col2"> Taal van de audiotrack, zoals opgegeven in het manifest. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>Fouten zoeken</b> </td> 
   <td colname="col2"></td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> DESIRED_SEEK_PERIOD</span> </td> 
   <td colname="col2"> Id van de punt (geheel getal). </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> DESIRED_SEEK_POSITION</span> </td> 
   <td colname="col2"> <p>Gezochte positie (in milliseconden) (dubbel). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>Diversen</b> </td> 
   <td colname="col2"></td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AUDITUDE_ERROR_CODE</span> </td> 
   <td colname="col2"> Foutcode controle (nummer). </td> 
  </tr> 
 </tbody> 
</table>

## NATIVE_ERROR: DRM-waarden {#section_D240082B93D34902A18C3923C1C717B3}

De Video Encoder-interface van de Adobe-video-engine retourneert deze DRM-berichten in het metagegevensobject `NATIVE_ERROR`.

Wanneer u DRM-fouten rapporteert aan Adobe, moet u `NATIVE_SUBERROR_CODE` en `DRM_ERROR_STRING` opnemen voor hulp bij het oplossen van problemen.

>[!TIP]
>
>Deze lijst bevat specifiek voor TVSDK bestemde informatie over de fouten. Voor volledige beschrijvingen, zie [de Verwijzing van de ActionScript van de Fouten van de ActionScript runtime voor Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/runtimeErrors.html#3300).

<table id="table_CD59A859865F4FFDBAA249C89C74770A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Waarde voor metagegevenssleutel NATIVE_- ERROR_CODE </th> 
   <th colname="col2" class="entry"> Waarde voor metagegevenssleutel NATIVE_ERROR_NAME </th> 
   <th colname="col3" class="entry"> Betekenis </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> 3300 </td> 
   <td colname="col2"><span class="codeph"> AXS_InvalidVoucher</span> </td> 
   <td colname="col3"> 
    <ul id="ul_516E4CB32D624B22892DDB9266CB04CA"> 
     <li id="li_348FC0F38B11417994119B61C9244076">Wat de software van de distributeur moet doen: 
      <ul id="ul_7AFD45CF92454BA4927783FAA628FBC4"> 
       <li id="li_0D9CCE61612643648C12DCDDD252E52A">Als u Google Chrome gebruikt en u bevindt zich in de Incognito-modus en uw Flash Player-versie is lager dan 11.6, kan deze fout optreden. <p>We raden de speler aan het versienummer van de browser te controleren en de gebruiker aan te raden de modus Incognito af te sluiten. </p> </li> 
       <li id="li_1DC6B755BD0840D48BEC92568FD330BA">Vraag de licentie opnieuw aan. <p>Als het verzoek succesvol is, te hoeven u niet om te registreren of te stijgen. Als de aanvraag mislukt is, registreert u de inhoud die de fout heeft veroorzaakt. <span class="codeph"> </span> subErrorIdcontains a line error if present. </p> </li> 
      </ul> </li> 
     <li id="li_060B5D60C9BB419CBFA7B062FBCF2632">Wat de distributeur moet doen: 
      <ul id="ul_FADB29DBF0DA4A0E8E54134AEB7DCD8A"> 
       <li id="li_FC5B1C04D21E4AECB0EBD9ADD3198504">Als pogingen mislukken op andere configuraties dan Chrome met Flash lager dan versie 11.6, kan er een fout zijn opgetreden in het pakket. </li> 
       <li id="li_A720ECE591254021879B335B81B1F76D">Controleer of het probleem specifiek is voor bepaalde inhoud en herverpakking. </li> 
      </ul> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3301 </td> 
   <td colname="col2"><span class="codeph"> AXS_AuthenticationFailed</span> </td> 
   <td colname="col3"> <p>De server kon de client niet verifiëren of autoriseren. </p> 
    <ul id="ul_BE77AC1848FB4C09B6318359ACF1B8EE"> 
     <li id="li_6FB37D317D174E8488C5070D20CD241C">De software van de distributeur zou om het even welke actie moeten ondernemen noodzakelijk om de geloofsbrieven van de gebruiker te herstellen of de gebruiker te begeleiden om toegang tot de inhoud te verkrijgen. </li> 
     <li id="li_BE071D59805B42D38E3E7650BC936417">De distributeur moet bevestigen dat het autorisatie- en authenticatiemechanisme van de distributeur correct werkt. <p>Als de distributeurs niet van plan zijn om de authentificatie of vergunningseigenschappen te gebruiken, zouden zij moeten controleren of het beleid van de beledigende inhoud authentificatie vereist en het Diagnose beleid/vergunningsdiscrepanties zien. </p> </li> 
    </ul> <p>Zie <a href="https://forums.adobe.com/thread/1277149" format="https" scope="external"> DRM-fout 3301 oorzaken en resolutie</a> voor meer informatie over deze foutcode. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3302 </td> 
   <td colname="col2"><span class="codeph"> AXS_RequireSSL</span> </td> 
   <td colname="col3"> <p>Bij Access 4.0 en hoger wordt deze fout gegenereerd in iOS wanneer de URL van de externe sleutel geen HTTPS als schema gebruikt. HTTPS is vereist. </p> 
    <ul id="ul_3D47777BBCA14B67B107FBBE3E37E40C"> 
     <li id="li_7F7BBB27AE754CC39ABAAF9269739C49">Als de distributeur een versie gebruikt die ouder is dan Access v4, of de versie ten minste 4 maar het platform niet iOS is, moet de software van de distributeur de fout registreren. <p>De fout wordt alleen gegenereerd op iOS. </p> </li> 
     <li id="li_D83C427D2A0D47408F723EF7195070B6">Als de software van de distributeur minstens versie 4 van de Toegang van Adobe is, en het platform is iOS, moeten de verdelers de verre zeer belangrijke server URL veranderen die zij aan HTTPS gebruiken. <p>Als zij slechts HTTP gebruikten, zouden de distributeurs een server kunnen moeten opzetten HTTPS. Anders, moeten de distributeurs de geregistreerde informatie aan Adobe voorleggen en de kwestie escaleren. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3303 </td> 
   <td colname="col2"><span class="codeph"> AXS_ContentExpired</span> </td> 
   <td colname="col3"> <p>De inhoud die u bekijkt, is verlopen volgens de regels die door de inhoudsprovider zijn ingesteld. subErrorId bevat een client-specifieke fout of regelfout. </p> <p> 
     <ul id="ul_1E4B3B8AE87A4E79997553BB2A0E52B9"> 
      <li id="li_EE3F2EEBF73743B9A38E4FCB7531E275">De software van de distributeur zou moeten proberen om vergunning van de server eens opnieuw te verwerven om te bepalen of een nieuwe niet-verlopen vergunning beschikbaar is. <p>Als er geen licentie beschikbaar is of de licentie is verlopen, stelt u de gebruiker in staat nieuwe licentie aan te schaffen of informeert u de gebruiker dat de inhoud niet kan worden gecontroleerd.Als de inhoud is verpakt met een beleid dat een verlopen-/einddatum heeft, rapporteren de logboeken van de licentieserver een <span class="codeph"> PolicyEvaluationException</span> en geven deze aan dat de einddatum van het beleid is verlopen (code 303). Controleer de logbestanden van de server om te controleren. </p> <p>Indien mogelijk, zouden de klanten het beleid moeten controleren dat zij tijdens verpakking gebruikten om te zien of het is verlopen. Het Java-opdrachtregelprogramma is: 
        <code>
         java&nbsp;-jar&nbsp;libs/AdobePolicyManager.jar&nbsp;&nbsp;&nbsp;detail&nbsp;demo.pol
        </code> </p> </li> 
      <li id="li_50DBE680D8F04E7DA3E29C65A93188E7">De distributeur zou moeten bevestigen of de data van de vergunningsvervaldatum zoals bedoeld worden gevormd. </li> 
     </ul> </p> <p>Voor meer informatie over deze foutencode, zie <a href="https://forums.adobe.com/thread/1300813" format="https" scope="external"> 3303 (Verlopen Inhoud) met AMS/FMS gebruikend een Levende Stroom?</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3304 </td> 
   <td colname="col2"><span class="codeph"> AXS_AuthorizationFailed</span> </td> 
   <td colname="col3">Zie <a href="https://forums.adobe.com/thread/1277149" format="https" scope="external"> DRM-fout 3301 oorzaken en resolutie</a> voor meer informatie over deze foutcode. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3305 </td> 
   <td colname="col2"><span class="codeph"> AXS_ServerConnectionFailed</span> </td> 
   <td colname="col3"> <p>Er is een time-out opgetreden voor de verbinding met de licentie- of domeinservers vanwege netwerkvertraging of de client die offline is. Normaal bevat subErrorId HTTP return code. </p> 
    <ul id="ul_938C7D8F07F64B4FA71A09DDF37E2E64"> 
     <li id="li_6648EA0049094E369BD9AE9CCA6B148D">De software van de verdeler zou een netwerkverbinding aan een bekende goede server moeten proberen. <p>Als de poging mislukt, vraagt u de gebruiker opnieuw verbinding te maken met het netwerk. Als de poging succesvol is, registreer het. </p> </li> 
     <li id="li_2ECA2C04BA08449DA3AD79A52EFAA229">De distributeur moet controleren of er licenties en domeinservers in gebruik zijn die online en zichtbaar zijn vanaf het netwerk van de client. </li> 
    </ul> <p>Zie <a href="https://forums.adobe.com/thread/1284947" format="https" scope="external"> DRM 3305 [ServerConnectionFailed] oorzaken en resolutie</a> voor meer informatie over deze foutcode. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3306 </td> 
   <td colname="col2"><span class="codeph"> AXS_ClientUpdateRequire</span> </td> 
   <td colname="col3"> Gebruik een nieuwere versie van TVSDK voor Android. <p>De huidige client kan de gevraagde actie niet uitvoeren, maar een bijgewerkte client kan de aanvraag mogelijk voltooien. </p> <p>Dit kan verschillende oorzaken hebben: 
     <ul id="ul_2EC4D42D5273439FA1AFDA1A2578B3D6"> 
      <li id="li_FCA926F5FAED4E7190BE855545AB6ACF">Er is een gedeeld domein gebruikt dat niet beschikbaar is op deze client. Dit is waarschijnlijk het geval wanneer het afspelen werkt op Chrome, maar niet op een andere browser en andersom. <p> <p>Tip: Chrome gebruikt een andere PHDS/PHLS-sleutel dan de andere browsers gebruiken. Zie <a href="https://adobeprimetime.zendesk.com/agent/tickets/2891" format="https" scope="external"> https://adobeprimetime.zendesk.com/agent/tickets/2891</a> voor meer informatie. </p> </p> </li> 
      <li id="li_3B633FB699234DCEA136E9BE3CC3386D">De toepassing probeert meerdere DRMS-sessies toe te voegen wanneer deze worden uitgevoerd op een iOS-versie die ouder is dan 5.0. </li> 
      <li id="li_F7ED993AF0B941A7A27216B4D587A999">De metagegevens hebben een versie van 3 of hoger als alleen versie 2 wordt ondersteund. </li> 
     </ul> </p> 
    <ul id="ul_EE4AE6AD4F1745A5B5623E53B599DB62"> 
     <li id="li_7A83869D4262443DA35FA1DF8D3097DD">De software van de distributeur moet de gebruiker waarschuwen en de bewerking afbreken. <p>Als de software een manier heeft om te bepalen of een verbetering beschikbaar is, richt de gebruiker aan die verbetering op de aangewezen manier voor het platform. </p> </li> 
     <li id="li_AF9C2711FDE54DA196EB9D2864632000">Als de kwestie wegens een gedeeld domein voorkomt, zal de verdeler met Adobe voor bijgewerkte runtime of een bibliotheek moeten controleren. <p>Voor Flash runtime, kan de verdeler de verbetering in hun toepassing direct dwingen. In het geval van een bibliotheek, zal de verdeler een bijgewerkte bibliotheek moeten verkrijgen, hun toepassing herbouwen en het opstellen aan hun gebruikers. </p> <p>Als het probleem optreedt als gevolg van meerdere DRMS-sessies, moet de distributeur zijn toepassing bijwerken om het iOS-versienummer te controleren voordat er meerdere DRMS-sessies kunnen worden toegevoegd. Of ze kunnen de distributie van hun toepassing beperken tot iOS v5 en hoger. </p> <p>als de kwestie voorkomt omdat de meta-gegevensversie hoger is dan versie 2, is de kwestie waarschijnlijk bedorven meta-gegevens. Ze kunnen proberen de metagegevens opnieuw op te bouwen en de resultaten te bekijken. Als zij het probleem blijven zien, registreer de kwestie en escaleer aan Adobe. </p> </li> 
    </ul> <p>Zie <a href="https://forums.adobe.com/thread/1266675" format="https" scope="external"> Een 3306 DRMErrorEvent-foutcode corrigeren</a> voor meer informatie over deze foutcode. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3307 </td> 
   <td colname="col2"><span class="codeph"> AXS_InternalFailed</span> </td> 
   <td colname="col3"> <p>Dit vertegenwoordigt over het algemeen een insect in de code van de Toegang van Adobe en is onverwacht, tenzij er een bekende bug, zoals hieronder is. subErrorId bevat een client-specifieke fout of regelfout. </p> 
    <ul id="ul_79F4A9655A2148519B1E9509C41F78C3"> 
     <li id="li_0E093AB4D6BD489B852279E6C1525A15">Als de browser Chrome is in Windows en de Flash-versie 11.6 is (SWF-versie 19 of hoger), moet de software van de distributeur ervan uitgaan dat de gebruiker op de infobar <span class="uicontrol"> Deny</span> heeft gedrukt en hetzelfde behandelt als 3368. </li> 
     <li id="li_0215D1089B344861A2C0A73E1067CFEF">Als 3307 voorkomt wanneer browser niet Chrome is of de versie van Flash niet 11.6 is, zou de verdeler aan Adobe moeten stijgen. </li> 
    </ul> <p>Belangrijk: <span class="codeph"> 3307:1107296344 (FailedToGetBrokerHandle)</span> zou met browser van Chrome versies 24-28 kunnen gebeuren. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3308 </td> 
   <td colname="col2"><span class="codeph"> AXS_WrongLicenseKey</span> </td> 
   <td colname="col3"> <p>Deze fout treedt op wanneer de licentie die wordt gebruikt de verkeerde sleutel bevat om de inhoud te decoderen. subErrorId bevat een client-specifieke fout of regelfout. </p> <p>Er lijken slechts twee manieren te zijn om deze bug te genereren: 
     <ul id="ul_1C955BD74C7843809D1B5A0CDCA5ED7B"> 
      <li id="li_18F0A7FDA6584887AD9DB3EDE54080D8">De klant heeft de standaard Adobe-tooling voor het genereren van licenties gewijzigd (bijvoorbeeld het Java-framework van de licentieserver). <p>In dit geval bevat de licentie een ongeldige sleutel die mogelijk niet overeenkomt met enige inhoud. </p> </li> 
      <li id="li_21D04ED1F1FA464785BC297D385766FF">De klant heeft meerdere licenties met dezelfde licentie-id uitgegeven. <p>In dit geval zijn er meerdere licenties die beschikbaar zijn op de client en overeenkomen met de metagegevens van de inhoud. De toegangscode heeft de verkeerde voor gebruik geselecteerd. </p> </li> 
     </ul> </p> 
    <ul id="ul_64AEE62BE36946F290067CF475A36ECA"> 
     <li id="li_9EEB2B11A4DA41E78C5840D8FAA81F0D">De software van de distributeur zou moeten proberen om vergunning van de server opnieuw te verwerven. 
      <ul id="ul_ACADC5518B054D0A853AEED2B675DB23"> 
       <li id="li_394835C8731048A5BF7D9370AC12448C">Als er geen licentie beschikbaar is of als de licentie is verlopen, geeft u een workflow voor de gebruiker om een nieuwe licentie aan te schaffen of informeert u de gebruiker dat de inhoud niet kan worden gecontroleerd en geregistreerd. </li> 
       <li id="li_3FE50518BE53405F9563FA620F7EAD5F">Als dit een domeingebonden inhoud (voor AIR) was, geef dan een manier op waarop de gebruiker zich bij het domein kan aansluiten. </li> 
      </ul> </li> 
     <li id="li_C80B353C1AEA4E9398241420CB491E84">De distributeur moet: 
      <ul id="ul_B5C50009374C4EED9B2B050B48F5F0F6"> 
       <li id="li_D5E6B760E0BC4B5C949ED1544B398838">Verifieer dat zij niet de delen van de vergunning van de server van de Vergunning van de Toegang hebben aangepast. </li> 
       <li id="li_AA8F4E4B6DDD40BA8807C0920A92186B">Controleer of ze unieke licentie-id's voor alle licenties uitgeven. </li> 
       <li id="li_A2C53FE779AC4FDDB65E00A2C4F43EC4">Escaleer de kwestie met Adobe. </li> 
      </ul> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3309 </td> 
   <td colname="col2"><span class="codeph"> AXS_CorruptedAdditionalHeader  </span> </td> 
   <td colname="col3"> <p>Dit gebeurt als de header groter is dan 65536 bytes. </p> 
    <ul id="ul_82C0F688519B4F43A764D59A891F1903"> 
     <li id="li_E66AC9149A0649E88A79C5289C12C395">De software van de distributeur zou moeten registreren welk stuk van inhoud de fout veroorzaakte. </li> 
     <li id="li_1C5916A33E7B4DC9968105B9BD20A727">De distributeur moet bevestigen dat de fout met specifieke inhoud kan worden gereproduceerd. Onderbroken inhoud opnieuw verpakken. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3310 </td> 
   <td colname="col2"><span class="codeph"> AXS_AppIDMismatch  </span> </td> 
   <td colname="col3">De Android-toepassing komt niet overeen met de toepassing die wordt gebruikt. <p>De juiste AIR-toepassing of Flash SWF wordt niet gebruikt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3311 </td> 
   <td colname="col2"><span class="codeph"> AXS_AppVersionMismatch  </span> </td> 
   <td colname="col3"> Niet in gebruik. Dit probleem wordt mogelijk nog steeds gegenereerd door de stapel versie 1.x in AIR. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3312 </td> 
   <td colname="col2"><span class="codeph"> AAXS_LicenseIntegrity  </span> </td> 
   <td colname="col3"> Als u dit wilt verhelpen, downloadt u de licentie opnieuw van de server. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3313 </td> 
   <td colname="col2"><span class="codeph"> AAXS_WriteMicrosafeFailed  </span> </td> 
   <td colname="col3"> <p>Dit probleem doet zich voor wanneer het systeem niet naar het bestandssysteem kan schrijven. <span class="codeph"> </span> subErrorIdcontains a client-specific error or line error. </p> <p>In Microsoft Windows kan fout 3313 worden gegenereerd door de Flash Player-insteekmodule Active X of NPAPI wanneer de gecodeerde inhoud een licentie-id of een beleids-id heeft die te lang is. Dit komt door de maximale padlengte in Windows. (Dit probleem treedt niet op bij de Pepper-plug-in.) </p> <p>Zie watson 3549660 </p> 
    <ul id="ul_DFD527D1E1224A439766DF7BED878E3B"> 
     <li id="li_FAF8FD98A4E8478CA7A92F770676ADFC">De software van de distributeur moet de gebruiker vragen te bevestigen dat zijn gebruikersmap niet is vergrendeld of zich op een vol of vergrendeld volume bevindt. </li> 
     <li id="li_6D1136EA750A459BBECEEE5F73F527BB">Als de distributeur AIR in plaats van Flash gebruikt, kan het probleem worden veroorzaakt door een beperking van de padlengte. <p>Distributeurs moeten de naam van hun AIR-toepassing tot een redelijke beperking beperken. Publiceer ook opnieuw inhoud met een kortere <span class="codeph"> licenseID</span> en een <span class="codeph"> policyID</span>. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3314 </td> 
   <td colname="col2"><span class="codeph"> AXS_CorruptedDRMMetadata  </span> </td> 
   <td colname="col3"> <p>Deze fout geeft vaak aan dat de inhoud is verpakt met PKI-testkaarten en dat de speler is gemaakt met PKI-productie of andersom. subErrorId bevat een client-specifieke fout of regelfout. </p> 
    <ul id="ul_A122EF304CAF48A8B4DA1E3F4413E29B"> 
     <li id="li_A9A1A5B23E884C22A71E2DE7535FEB3B">De software van de distributeur zou moeten registreren welk stuk van inhoud de fout veroorzaakte. </li> 
     <li id="li_7AD7F13A4B1B4998A7E49664E7645815">De distributeur moet bevestigen dat de fout met specifieke inhoud kan worden gereproduceerd. <p>Mogelijk moet u verbroken inhoud opnieuw verpakken. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3315 </td> 
   <td colname="col2"><span class="codeph"> AAXS_PermissionDenied  </span> </td> 
   <td colname="col3"> <p>Er zijn bekende fouten waarin deze foutcode wordt gegenereerd wanneer een 3305-teken is bedoeld. Zie <a href="https://forums.adobe.com/thread/1284947" format="https" scope="external"> DRM 3305 [ServerConnectionFailed] oorzaken en resolutie</a> voor meer informatie. </p> <p>Extern SWF-bestand dat door AIR wordt geladen, heeft geen toegang tot de Flash Access-functionaliteit. Deze foutcode kan ook worden gegenereerd als tijdens de netwerktoegang een beveiligingsfout optreedt. De voorbeelden omvatten de bestemmingsserver niet de cliënt om te verbinden door crossdomain.xml te gebruiken, of crossdomain.xml is niet bereikbaar. </p> <p>Zie <a href="https://forums.adobe.com/thread/1266592" format="https" scope="external"> DRM-fout 3315 mogelijke oorzaak en resolutie</a> voor meer informatie. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3316 </td> 
   <td colname="col2"><span class="codeph"> AXS_NOTUSED_MOVED  </span> </td> 
   <td colname="col3"> Was <span class="codeph"> ADOBECPSHIM_MinorErr_MissingAdobeCPModule</span>. Verplaatst naar 3344 vanwege een conflict met Flash-foutcode. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3317 </td> 
   <td colname="col2"><span class="codeph"> AAXS_LoadAdobeCPFailed  </span> </td> 
   <td colname="col3"> <p>Belangrijk:  Dit is een zeldzame fout en komt gewoonlijk niet voor in een productieomgeving. </p> <p>Als de fout voorkomt, kunt u één van het volgende doen: 
     <ul id="ul_BC435E61623444BB98A86216531DC892"> 
      <li id="li_FA433D0758B642D2AFDCF04906B3FE18">Als u AIR gebruikt, installeert u deze opnieuw. </li> 
      <li id="li_F08D9AAFF46244F8842DEE5FD9CBBE0A">Als u Flash Player gebruikt, download opnieuw <span class="codeph"> AdobeCP</span> modules. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3318 </td> 
   <td colname="col2"><span class="codeph"> AXS_IncompatibleAdobeCPVersion  </span> </td> 
   <td colname="col3"> Niet van toepassing op Android. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3319 </td> 
   <td colname="col2"><span class="codeph"> AXS_MissingAdobeCPGetAPI  </span> </td> 
   <td colname="col3"> Niet van toepassing op Android. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3320 </td> 
   <td colname="col2"><span class="codeph"> AAXS_HostAuthenticateFailed  </span> </td> 
   <td colname="col3"> Niet van toepassing op Android. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3321 </td> 
   <td colname="col2"><span class="codeph"> AXS_I15nFailed  </span> </td> 
   <td colname="col3"> <p>Het provisioning van de client met toetsen is mislukt. subErrorId bevat een client-specifieke, serverspecifieke of regelfout. </p> 
    <ul id="ul_98D919B9060A441AACB6106F6D8E8DA7"> 
     <li id="li_DCAB00A8AC4A426CBBD377374B3F71AE">De software van de distributeur moet de bewerking ten minste één keer opnieuw proberen. <p>Als u Google Chrome in Windows gebruikt, geeft u uitleg over het toestaan van toegang voor insteekmodules die zich niet in een sandbox bevinden. Zie <a href="https://helpx.adobe.com/adobe-access/kb/error-3321.html" format="html" scope="external"> Toegang tot sandbox van Google Chrome geweigerd</a> voor meer informatie. </p> </li> 
     <li id="li_7FB7681FE32D444BB1BDBA3E5953A2C3">De distributeur moet een van de volgende taken uitvoeren: 
      <ul id="ul_486B64F187C44AE3B4775953A6142836"> 
       <li id="li_095B1D4CD051427CB2BFA7082B454056">Als de fout op verschillende platformen consistent is, moet u het probleem met Adobe doorverwijzen. </li> 
       <li id="li_0C6EB7B912FA41E59657216498DA3515">Als de fout zich beperkt tot Chrome in Windows, raadpleegt u de gebruiker om toegang tot de niet-sandbox plug-in toe te staan. </li> 
      </ul> <p>Distributeurs dienen hun SWF-bestand bij te werken naar versie 19 of hoger en bij de Chrome-specifieke fout 3321 treedt een fout van 3368 op. Fout 3368 kan specifieker door de software van de verdeler worden behandeld. Deze wijziging is geïntroduceerd in Chrome Stable Channel versie 26.0.1410.43. </p> <p>Tip: Fout <span class="codeph"> 3321:1090519056</span> zou met versies 11.1 tot en met 11.6 van Flash Player kunnen gebeuren. We raden u aan een upgrade uit te voeren naar de nieuwste versie van Flash Player. </p> </li> 
    </ul> <p>Zie <a href="https://forums.adobe.com/thread/1277138" format="https" scope="external"> DRM-fout 3321 Oorzaken en resolutie</a> voor meer informatie. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>Fouten in wereldwijde winkelbeschadiging</b> </td> 
   <td colname="col2"> </td>
   <td colname="col3"> </td>
  </tr> 
  <tr> 
   <td colname="col1"> 3322 </td> 
   <td colname="col2"><span class="codeph"> AXS_DeviceBindingFailed  </span> </td> 
   <td colname="col3"> <p>Het apparaat lijkt niet overeen te komen met de configuratie die aanwezig was toen het werd geïnitialiseerd. subErrorId bevat een client-specifieke of line fout. </p> <p>De software van de distributeur moet een van de volgende taken uitvoeren: 
     <ul id="ul_444401051A2E407B95BC44491E9BB71C"> 
      <li id="li_93493EA05DB44CB1AEC368663F1ABA8D"> <p>Als het apparaat geen Flash Player gebruikt en AIR, iOS gebruikt, enzovoort, roept u <span class="codeph"> DRMManager.resetDRMVouchers()</span> aan. </p> <p>Als de kwestie op iOS in een ontwikkelingsfase voorkomt, vraag de ontwikkelaar om te bevestigen of de kwestie wanneer het schakelen tussen bouwstijlen wordt waargenomen die van derde werden gedownload, pre-versiedistributiesystemen (bijvoorbeeld, HockeyApp) en een lokale bouwstijl van Xcode. De attributen van een vorige installatie worden niet volledig beschreven wanneer het schakelen tussen een bouwstijl die van HockeyApp en een bouwstijl van Xcode wordt verdeeld. Deze situatie zou de fout 3322 kunnen veroorzaken. </p> <p>Om dit probleem op te lossen, moet de ontwikkelaar de oudere build van het apparaat verwijderen voordat de nieuwe build wordt geïnstalleerd. </p> </li> 
      <li id="li_A5C9633F11584C788A2D9A23CC18FA6D">Als het apparaat Flash Player gebruikt, en het onbruikbaar van 3322 of 3346 foutencodes is, zie de instructies van Adobe over hoe te om uw DRM vergunningsopslag op <a href="https://forums.adobe.com/message/5535907#5535907" format="https" scope="external"> DRM Fout 3322/3346/3368 in Chrome programmatically terug te stellen (Info-Bar Problems)</a>. </li> 
     </ul> </p> <p>Deze fout treedt naar verwachting niet vaak op. In bedrijfsomgevingen die zwervende profielen gebruiken, als een gebruiker inhoud die door DRM wordt beschermd, de kans dat fout 3322 voorkomt stijgt aangezien de gebruiker zich bij verschillende machines aanmeldt. Indien mogelijk, zou de verdeler moeten proberen om deze informatie van gebruiker te krijgen. </p> <p>Als de fout vaak voorkomt, escaleer aan Adobe. U moet Adobe op de hoogte stellen of het opnieuw instellen van de licentieopslag het probleem heeft opgelost (of niet) en u moet de Adobe vertellen welke browsers de fout veroorzaken. </p> <p>Raadpleeg de volgende artikelen voor meer informatie: 
     <ul id="ul_C468409D1EA046178CA7F54DCDCB84EA"> 
      <li id="li_20C8CA3853574CE486F21E7A3667DAB9"><a href="https://forums.adobe.com/message/5520902" format="https" scope="external"> https://forums.adobe.com/message/5520902</a> </li> 
      <li id="li_6E6F1BD6FE7843449B3E2F06F342EFF7"><a href="https://forums.adobe.com/message/5535911" format="https" scope="external"> https://forums.adobe.com/message/5535911</a> </li> 
      <li id="li_2BE40E513A0C4BAD900C7B69FEF5D690"><a href="https://forums.adobe.com/message/5748618" format="https" scope="external"> https://forums.adobe.com/message/5748618</a> </li> 
      <li id="li_9C2BD122E3874E2893DD43E082A877E0"><a href="https://forums.adobe.com/message/6061165" format="https" scope="external"> https://forums.adobe.com/message/6061165</a> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3323 </td> 
   <td colname="col2"><span class="codeph"> AXS_CorruptGlobalStateStore  </span> </td> 
   <td colname="col3"> <p>Bestanden die door de DRM-client worden gebruikt, zijn onverwacht gewijzigd. subErrorId bevat een client-specifieke of line fout. </p> 
    <ul id="ul_96EA771046CA4B2B9FAE24D493F43FF2"> 
     <li id="li_D2693CD8EFEF46108828BA17E3F54FF6">De software van de distributeur zou de gebruiker moeten begeleiden om op de zelfde manier terug te stellen zoals voor 3322. </li> 
     <li id="li_0149B82436B64E28AC2B8C9B0EB09898">Als de GlobalStore een lager percentage dan de verwachte foutsnelheid van de harde schijven van uw gebruikersbasis heeft, moet u het probleem doorverwijzen naar Adobe. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3324 </td> 
   <td colname="col2"><span class="codeph"> AXS_MachineTokenInvalid  </span> </td> 
   <td colname="col3"> Lokale DRM-opslag voor deze toepassing opnieuw instellen. Roep DRMManager.resetDRM aan. <p>De licentieserver kan mogelijk geen verbinding maken met de CRL-server (Certificate Revocation List) om de CRL-bestanden te vernieuwen, of de clientcomputer vraagt om een licentie/verificatie die door de licentieserver is ingetrokken. </p> <p>In de serverlogboeken, is foutcode 111 MachineTokenInvalid. Op clientniveau wordt foutcode 111 echter vertaald naar foutcode 3324. </p> <p>De beheerder van de DRM-licentieserver moet controleren of de licentieserver van de klant ooit de Adobe CRL-bestanden heeft kunnen ophalen. Als de klant Tomcat gebruikt, kan de klant de map <span class="filepath"> tomcat/temp/</span> controleren om te zien of er 4 CRL-bestanden zijn. </p> 
    <ul id="ul_23B7F1A104AF49E79EA87DB8E15E337E"> 
     <li id="li_855D87F251184FE688A8D5FA0F6C9EF5">Als de bestanden zich in deze map bevinden, dubbelklikt u op de bestanden in Windows Verkenner en in de CRL-viewertoepassing om te bepalen of een van de bestanden is verlopen. </li> 
     <li id="li_58EC4EDA2B5146188A0FF7B33C91E2FD">Als er geen dossiers in tomcat/temp/ zijn, dan kan men veronderstellen deze vergunningsserver nooit de server van Adobe CRL wegens een firewall/het verpletteren van kwestie heeft kunnen bereiken. </li> 
    </ul> <p>Voor meer informatie, zie <a href="https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_secure_deployment_guidelines.pdf" format="http" scope="external"> de regels van de Firewall</a>. </p> <p>Als de CRL-bestanden niet beschikbaar zijn of verlopen zijn, moet u bevestigen of de licentieserver kan worden bereikt. Open een netwerksniffer op de de vergunningsserver van de klant, herstart de server, en heb een cliëntpoging om een vergunning van de server te vragen. U kunt het netwerkverkeer waarnemen om te zien of de vraag aan de volgende URL eindpunten succesvol is: <p>Tip:  U kunt ook de volgende CRL-URL's in een browser invoeren om te zien of u elk bestand handmatig kunt downloaden. </p> 
     <ul id="ul_9B65C7ABBDEC4AC9BF3755FFD3587971"> 
      <li id="li_6867A9050E8D421C9138AC853D1784C9"><a href="https://crl2.adobe.com/Adobe/FlashAccessIndividualizationCA.crl" format="http" scope="external"> crl2.adobe.com/Adobe/FlashAccessIndividualizationCA.crl</a> </li> 
      <li id="li_6431689260554EAFAFDA2EC31798DCB5"><a href="https://crl2.adobe.com/Adobe/FlashAccessIntermediateCA.crl" format="http" scope="external"> crl2.adobe.com/Adobe/FlashAccessIntermediateCA.crl</a> </li> 
      <li id="li_2939674D0F854ADEB67E45FD216288A2"><a href="https://crl2.adobe.com/Adobe/FlashAccessRootCA.crl" format="http" scope="external"> crl2.adobe.com/Adobe/FlashAccessRootCA.crl</a> </li> 
      <li id="li_96386E00BE9D4CB99D100057A5F7C6DD">crl3.adobe.com/AdobeSystemsIncorporated FlashAccessRuntime/LatestCRL.crl</li> 
     </ul> </p> <p>Als de firewallregels open zijn en er geen huidige 3324 fouten zijn, zou er een tijdelijke netwerkkwestie kunnen zijn geweest. Controleer de serverlogboeken van de klant, die waarschijnlijk in de map <span class="codeph"> /tomcat/logs/</span> staan, om te bepalen of er een fout is opgetreden toen de licentieserver probeerde de certificaatintrekkingslijsten op te halen. <p>Belangrijk:  Een fout zou kunnen voorkomen wanneer een groot aantal (of een uitbarsting) cliënten een fout 3324 aan een tijdelijke netwerkkwestie melden wanneer het vernieuwen van een CRL- dossier. Toen het netwerkprobleem werd opgelost, werden de 3324 kwesties ook opgelost. </p> </p> <p>Als alle 4 van de CRL dossiers in <span class="filepath"> tomcat/temp/</span> folder bestaan, en de cliënten krijgen nog 3324 foutencodes, zouden er de kwesties van de dossiertoegang tot de CRL dossiers kunnen zijn. U kunt dit probleem oplossen door de logbestanden te bekijken en de bestaande CRL-bestanden te wissen. </p> <p>Als er geen serverproblemen optreden, vraagt u de gebruiker om de versie opnieuw in te stellen zoals beschreven in 3322. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>Fouten in serverwinkelbeschadiging</b> </td> 
   <td colname="col2"> </td>
   <td colname="col3"> </td>
  </tr> 
  <tr> 
   <td colname="col1"> 3325 </td> 
   <td colname="col2"><span class="codeph"> AXS_CorruptServerStateStore  </span> </td> 
   <td colname="col3"> <p>Bestanden die door de DRM-client worden gebruikt, zijn onverwacht gewijzigd. <span class="codeph"> </span> subErrorIdcontains a client-specific or line error. </p> 
    <ul id="ul_860D2402DA61460AB0D938F1116F6D64"> 
     <li id="li_CF368C43452B4265B62ADA3E223894BA">De software van de distributeur zou de verrichting opnieuw moeten proberen, omdat AdobeCP de beledigende serveropslag intern heeft geschrapt, en een herpoging zou moeten slagen. Als het opnieuw proberen ontbreekt, registreer de kwestie. </li> 
     <li id="li_51A5803A1F754970BB4EBD6494F5DC96">Als het aantal pogingen daalt met een snelheid die hoger is dan de verwachte foutsnelheid van de harde schijven van uw gebruikersbasis, moet u het probleem doorverwijzen naar Adobe. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3326 </td> 
   <td colname="col2"><span class="codeph"> AXS_StoreTamperingDetected  </span> </td> 
   <td colname="col3"> Roep <span class="codeph"> DRMManager.resetDRM</span> aan. <p>Het licentiearchief is beschadigd of beschadigd en kan niet meer worden gebruikt. </p> <p>De software van de distributeur moet de gebruiker begeleiden bij het opnieuw instellen op dezelfde manier als beschreven in 3322. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3327 </td> 
   <td colname="col2"><span class="codeph"> AXS_ClockTamperingDetected  </span> </td> 
   <td colname="col3"> Verbeter de klok of verkrijg opnieuw <span class="codeph"> Authn/Lic/Domain</span> vergunning. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>Verificatie-/licentie-/domeinserverfouten</b> </td> 
   <td colname="col2"> </td>
   <td colname="col3"> </td>
  </tr> 
  <tr> 
   <td colname="col1"> 3328 </td> 
   <td colname="col2"><span class="codeph"> AXS_ServerErrorTryAgain  </span> </td> 
   <td colname="col3"> <p>Dit is een serverfout waarbij de server het verzoek van de client niet kon voltooien. Deze fout kan voorkomen wanneer, bijvoorbeeld, de server bezig is, HTTP/500, de server niet de noodzakelijke sleutel heeft om het verzoek te decrypteren, etc. </p> <p>Op de cliënt, is er geen manier om te bepalen wat verkeerd ging. De klant dient de logboeken van de Adobe Access-server, die gewoonlijk <span class="codeph"> AdobeFlashAccess.log</span> worden genoemd, te controleren om te bepalen wat er fout is gegaan. Het logbestand bevat altijd een beschrijvende stacktracering die het probleem aangeeft. <span class="codeph"> </span> subErrorIdcontains a server-specific or line error. </p> <p>De distributeur zou serverlogboeken moeten bekijken om te identificeren welke server deze fout verzendt. Voor 3328 fouten die subfoutcode 101 hebben, kan de server de aanvraag niet decoderen. De klant moet valideren dat de licentie-/transportservercertificaten die op de licentieserver zijn geïnstalleerd, overeenkomen met en overeenkomen met de certificaten die tijdens het verpakken worden gebruikt. </p> <p>Bovendien moeten klanten die de Implementatie van de Verwijzing gebruiken, ervoor zorgen dat er geen typos in <span class="codeph"> flashaccess-refimpl.properties</span> dossier is waar de primaire en extra certificaten worden gespecificeerd. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3329 </td> 
   <td colname="col2"><span class="codeph"> AXS_ApplicationSpecificError  </span> </td> 
   <td colname="col3"> <p>De toepassingsspecifieke subfoutcode is niet bekend bij Flash Access. <span class="codeph"> </span> subErrorIdcontains a server-specific fout van de uitgevers aangepaste vergunningsserver. De server heeft een fout geretourneerd in de toepassingsspecifieke naamruimte. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 330 </td> 
   <td colname="col2"><span class="codeph"> AXS_NeedAuthentication  </span> </td> 
   <td colname="col3"> <p>Deze fout treedt op wanneer de inhoud is geconfigureerd om clients te vragen om verificatie voordat de licenties worden opgehaald. </p> 
    <ul id="ul_712D29B8B5A6401FB014C4A283918E32"> 
     <li id="li_2D56905EB50D4FDEAD69CA8EAE38AD1A">De software van de distributeur zou de gebruiker voor authentiek moeten verklaren en dan de vergunning opnieuw verkrijgen. <p>Als uw service geen verificatie wil gebruiken, registreert u de identificatie van de inhoud die deze fout veroorzaakt. </p> </li> 
     <li id="li_B3BCF899B8BE41C7A4F7CF84B0503483">Deze fout zou geen escalatie moeten vereisen, tenzij de inhoud niet verondersteld wordt om authentificatie te vereisen. <p>In dit geval moet u de desbetreffende inhoud opnieuw verpakken met een juist beleid. Als de inhoud op de juiste wijze is verpakt, raadpleegt u Verschillen in beleid/licenties opsporen. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <b>Fouten in licentiecontrole die hierboven niet zijn beschreven</b> </td> 
   <td colname="col2"> </td>
   <td colname="col3"> </td>
  </tr> 
  <tr> 
   <td colname="col1"> 331 </td> 
   <td colname="col2"><span class="codeph"> AXS_ContentNotyetValid  </span> </td> 
   <td colname="col3"> <p>De verkregen licentie is nog niet geldig. U lost dit probleem op door te controleren of de klok van de client niet correct is ingesteld. Als u de klok van de client wilt instellen, moet u de inhoud opnieuw verpakken of de configuratie van de licentieserver wijzigen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 332 </td> 
   <td colname="col2"><span class="codeph"> AXS_CachedLicenseExpired  </span> </td> 
   <td colname="col3"> Licentie opnieuw verkrijgen van de server. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3333 </td> 
   <td colname="col2"><span class="codeph"> AXS_PlaybackWindowExpired  </span> </td> 
   <td colname="col3"> <p>U moet gebruikers laten weten dat ze deze inhoud pas kunnen afspelen nadat het beleid is verlopen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 334 </td> 
   <td colname="col2"><span class="codeph"> AXS_InvalidDRMPlatform  </span> </td> 
   <td colname="col3"> <p>Dit platform wordt niet toegestaan om de inhoud te spelen omdat, bijvoorbeeld, de inhoudsleverancier de Toegang van Adobe heeft gevormd om inhoud aan de Toegang van Adobe te ontkennen op een platform of een gedeelde domein-gebonden vergunning verbindend aan een gedeeld domeinteken dat voor een verschillende verdeling wordt bedoeld. </p> <p>CDM kan deze fout genereren als de inhoud niet in het pakket is opgenomen met behulp van een geschikte (CDM-functie gecodeerde) pakketcertificering. </p> <p>Als de inhoud is verpakt met een onjuist PHDS/PHLS-certificaat, werkt de inhoud mogelijk in Chrome, maar niet in andere browsers (of andersom). <p>Tip:  Dit komt doordat Chrome verschillende PHDS/PHLS-certificaten gebruikt. </p>Om te bevestigen welk certificaat wordt gebruikt, stort de details van de inhoudsmeta-gegevens en zoek <i>ontvankelijke certificaten</i>. Zie <a href="https://adobeprimetime.zendesk.com/agent/tickets/2891" format="https" scope="external"> https://adobeprimetime.zendesk.com/agent/tickets/2891</a> voor meer informatie. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 335 </td> 
   <td colname="col2"><span class="codeph"> AXS_InvalidDRMVersion  </span> </td> 
   <td colname="col3"> Voer een upgrade uit naar de nieuwste versie van de TVSDK voor Android. <p>Voer een van de volgende taken uit om dit probleem op te lossen: 
     <ul id="ul_BF1742948BC9461CB8686DE70124D3CD"> 
      <li id="li_690D440C94CC45A0AE55EC319B1C4C23">AIR upgraden </li> 
      <li id="li_CDD20251C881466E88BE7BBB53D61EBC">Voer voor Flash Player een upgrade uit op de AdobeCP-module en probeer het afspelen opnieuw. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 336 </td> 
   <td colname="col2"><span class="codeph"> AXS_InvalidRuntimePlatform  </span> </td> 
   <td colname="col3"> <p>Dit platform is niet toegestaan om de inhoud af te spelen omdat, bijvoorbeeld, de inhoudsprovider Access heeft geconfigureerd om inhoud aan FP/AIR op een platform te weigeren. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 337 </td> 
   <td colname="col2"><span class="codeph"> AXS_InvalidRuntimeVersion  </span> </td> 
   <td colname="col3"> Voer een upgrade uit naar de nieuwste versie van TVSDK voor Android. <p>Dit gebeurt als de inhoud of de server is geconfigureerd om het afspelen van een bepaalde versie van de Flash- of AIR-runtimes te weigeren. </p> 
    <ul id="ul_B0732D941256483CABBDD30C9BF43249"> 
     <li id="li_72782B1D638F48C0B87084689FB9C798">Als de gebruiker zich op een werkend systeem bevindt waarop Flash kan worden bevorderd, zou de software van de verdeler de gebruiker moeten vragen om Flash te bevorderen en opnieuw te proberen. Anders wordt de gebruiker geadviseerd een andere machine te gebruiken. </li> 
     <li id="li_1E3FD93CE39E43F2B7D961299B1211DA">Als fout 3337s wordt vermoed, bepaal of het voor specifieke inhoud voorkomt en herverpak die inhoud. Als de inhoud op de juiste wijze is verpakt, raadpleegt u Verschillen in beleid/licentie voor diagnose </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 338 </td> 
   <td colname="col2"><span class="codeph"> AXS_UnknownConnectionType  </span> </td> 
   <td colname="col3"> <p>Kan het verbindingstype niet detecteren en het beleid vereist dat u Uitvoerbeveiliging inschakelt. Dit probleem wordt alleen verwacht als de inhoud in een pakket is geplaatst en digitale of analoge uitvoerbeveiliging vereist. </p> <p>Een kwestie in versies van Flash Player ouder dan versie 11.8.800.168 veroorzaakte fout 3338 om af en toe op inhoud voor te komen waarvoor het beleid erop wees dat de inhoudsbescherming <span class="codeph"> GEBRUIK ALS BESCHIKBAAR </span> is. Dit probleem is opgelost in versie 11.8.800.168 en hoger. </p> 
    <ul id="ul_4B6CA26A53F84838B5B95400925464D4"> 
     <li id="li_CBD890F467E449EBB5116E1561252058">De software van de verdeler selecteert een variant van de inhoud die outputbescherming niet vereist (bijvoorbeeld de variant van SD van een stroom HD). <p>Als fout 3338 op <span class="codeph"> USE_IF_AVAILABLE </span> inhoud voorkomt, controleer op spelerversienummer. Als de versie van de speler lager is dan 11.8.800.168, raadt u de gebruiker aan een upgrade van Flash Player uit te voeren. Als fout 3338 op versies boven 11.8.800.168 voorkomt, registreer welke inhoud de fout veroorzaakte. </p> </li> 
     <li id="li_62886C1D96264B129928A7E29E6C70E1">De distributeur zou moeten controleren welke inhoud deze fout veroorzaakt en bevestigen dat het beleid van de inhoud <span class="codeph"> NO_PROTECTION</span> of <span class="codeph"> USE_IF_AVAILABLE</span> voor analoge en digitale output plaatst. <p>Als inhoud per ongeluk is verpakt met <span class="codeph"> NO_OUTPUT</span> of <span class="codeph"> REQUIRED</span>, moet u de inhoud opnieuw verpakken. Zie Verschillen tussen beleid en licenties voor diagnose als de inhoud op de juiste wijze is verpakt. Doorbreek anders naar Adobe. </p> </li> 
    </ul> <p>Voor meer informatie, zie <a href="https://forums.adobe.com/message/5518688" format="https" scope="external"> Onverwachte 338 fouten krijgen wanneer uw beleid DRM aan USE_IF_AVAILABLE wordt geplaatst?</a> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 339 </td> 
   <td colname="col2"><span class="codeph"> AXS_NoAnalogPlaybackAllowed  </span> </td> 
   <td colname="col3"> Kan niet afspelen op het analoge apparaat. Sluit een digitaal apparaat aan om het probleem op te lossen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3340 </td> 
   <td colname="col2"><span class="codeph"> AXS_NoAnalogProtectionAvail  </span> </td> 
   <td colname="col3"> Kan inhoud niet afspelen omdat het aangesloten analoge externe weergaveapparaat (monitor/tv) niet de juiste mogelijkheden heeft (het apparaat heeft bijvoorbeeld geen Macrovision of ACP). </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3341 </td> 
   <td colname="col2"><span class="codeph"> AXS_NoDigitalPlaybackAllowed  </span> </td> 
   <td colname="col3"> Kan inhoud niet afspelen op een digitaal apparaat. <p>Belangrijk:  Dit probleem kan zich niet voordoen in een productieomgeving, omdat uitgevers van inhoud het afspelen van digitale inhoud niet mogen uitschakelen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3342 </td> 
   <td colname="col2"><span class="codeph"> AXS_NoDigitalProtectionAvail  </span> </td> 
   <td colname="col3"> Het aangesloten digitale externe weergaveapparaat (monitor/tv) heeft niet de juiste mogelijkheden. Het apparaat heeft bijvoorbeeld geen HDCP. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3343 </td> 
   <td colname="col2"><span class="codeph"> AAXS_IntegrityVerificationFailed  </span> </td> 
   <td colname="col3"> <p>Niet van toepassing op Android. </p> <p>Deze fout treedt momenteel in eerste instantie op nadat een nieuwe versie van Flash is uitgebracht. Het komt voor omdat Flash bevorderd terwijl Flash open was, die Flash in een slechte staat zet tot browser opnieuw begint. </p> 
    <ul id="ul_A0AC4A77550E40409A04BD33748EA987"> 
     <li id="li_F41C1ABD838D41ABB0DF65093E664A29">De software van de distributeur moet de volgende taken uitvoeren: 
      <ul id="ul_79B2AB1372074D448F129851AA24F985"> 
       <li id="li_B93EDD263D78434FAF198A01938D3508">Het is raadzaam alle browsers te sluiten of af te sluiten en deze vervolgens opnieuw te openen. </li> 
       <li id="li_ADFBCFA66AD849E18DB390455458528E">Controleer of de versie van Flash actueel is. <p>Als de versie niet actueel is, raadt u de klant aan een upgrade uit te voeren, alle tabbladen in de browser te sluiten en opnieuw te openen. </p> </li> 
      </ul> </li> 
     <li id="li_281B54582B5949AEA7D166246917EE41">Als er een fout optreedt nadat de browser opnieuw is gestart, gaat u naar Adobe. <p>Wanneer een nieuwe versie wordt vrijgegeven, adviseren wij dat u Adobe Support contacteert om te zien of de kwestie van achtergrondupdates is opgelost. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3344 </td> 
   <td colname="col2"><span class="codeph"> AXS_MissingAdobeCPModule  </span> </td> 
   <td colname="col3"> Niet van toepassing op Android. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3345 </td> 
   <td colname="col2"><span class="codeph"> AXS_DRMNoAccessError  </span> </td> 
   <td colname="col3"> <p>Niet van toepassing op Android. </p> <p>Deze fout treedt op wanneer een deel van Flash of AIR niet correct is geïnstalleerd. </p> <p>De software van de distributeur zou één van het volgende moeten doen: 
     <ul id="ul_D1188E2D4FDF4BD89A04F5629D75D981"> 
      <li id="li_B33FBCA5D4534D668B86A5E93DB3A809">Vraag de gebruiker om AIR te verwijderen en opnieuw te installeren. </li> 
      <li id="li_B7D2388E9FA84C26AF1C87B48AF9EF16">Voor Flash Player, roep <span class="codeph"> System.update</span>. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3346 </td> 
   <td colname="col2"><span class="codeph"> AXS_MigrationFailed  </span> </td> 
   <td colname="col3"> 
    <ul id="ul_518AD4931CC64EB3A962DD451E6C5067"> 
     <li id="li_3C44F0740B08490E9C62D89C40B57DC2">De software van de distributeur zou één van het volgende moeten doen: 
      <ul id="ul_7D90526684BF4EB2BBADCF598AA13086"> 
       <li id="li_D15B4BEDAF7340F6B9BC886DF6E346EC">Als AIR, roep <span class="codeph"> DRMManager.resetDRMVouchers()</span> </li> 
       <li id="li_40A51D35408249CFA28DBC49FDA3408B">Als Flash onbruikbaar is wegens fouten 3322 of 3346 foutencode, zouden de gebruikers naar <a href="https://forums.adobe.com/message/5535907#5535907" format="http" scope="external"> https://forums.adobe.com/message/5535907#5535907</a> moeten gaan en de instructies van het Adobe artikel volgen om hun DRM vergunningsopslag programmatically terug te stellen. </li> 
      </ul> </li> 
     <li id="li_0464471E4A094C80BF2986694341921A">Als deze fout vaak optreedt, moet de distributeur de gegevens over de versie van de frequentiespeler en de browserversie aan Adobe verstrekken. </li> 
    </ul> <p>Raadpleeg de volgende forumartikelen voor meer informatie: 
     <ul id="ul_44E0077FEAA749CC9549BF3846065304"> 
      <li id="li_2BE3B2443380415DA73B7AA3B6547B31"><a href="https://forums.adobe.com/message/5520902" format="https" scope="external"> DRM-fout 3322/3346/3368 in Chrome (problemen op de Infobalk)</a> </li> 
      <li id="li_4E5C7414756644E1AB78BE7B8112228C"><a href="https://forums.adobe.com/message/5535911" format="https" scope="external"> 3322- of 3346-fout na hardwarewijziging</a> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3347 </td> 
   <td colname="col2"><span class="codeph"> AXS_InsufficientDeviceCapabilites  </span> </td> 
   <td colname="col3"> <p>De belangrijkste betekenis van deze fout is dat de licentie een beperking heeft waaraan het DRM-certificaat van de client kan voldoen. De volgende "hardwaremogelijkheden" worden gedefinieerd wanneer het DRM-certificaat van de client wordt uitgegeven: 
     <ul id="ul_1EB6F1469C244CF0BA52C212495C053D"> 
      <li id="li_646043CE045C4DE2BBC939E1F4963DFE"><b>Toegankelijke bus voor andere gebruikers</b>. Als <b>true</b>, stromen de gedecrypteerde media nooit over een bus of in hoofdgeheugen waar een toepassing tot het kan toegang hebben. <p>Als <b>false</b>, kan inhoud na decryptie voor de toepassing toegankelijk zijn. </p> </li> 
      <li id="li_02AAECAF4D35447BA10554541B46DE67"><b>Hardware Root of Trust</b>. Als <b>true</b>, is alle software die tijdens het opstarten op het apparaat is geladen, gevalideerd op basis van een sleutel of samenvatting die alleen beschikbaar is in de hardware. <p>Beide beperkingen worden op de client gecontroleerd wanneer de licentie wordt geopend op basis van het DRM-certificaat voor de client en de fout onmiddellijk optreedt. Deze beperkingen kunnen ook aan de serverzijde worden gecontroleerd alvorens de vergunning uit te geven. </p> </li> 
     </ul> </p> <p>De secundaire betekenis van deze fout is dat de licentie het beleid "Jailbreak Enforcement" heeft en dat er een jailbreak op het apparaat is gedetecteerd. Deze controle wordt periodiek uitgevoerd aan de clientzijde en kan niet worden gecontroleerd aan de serverzijde. </p> <p>De distributeurs kunnen het beleid bijwerken en de beperkingen verwijderen. Voor het beleid van het apparatenvermogen, geef het bevel van de beleidsupdate met <span class="codeph"> - devCapabilitiesV1</span> vlag en geen argumenten uit. Stel <span class="codeph"> policy.enfordJailbreak=false</span> in voor jailbreak-handhaving. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3348 </td> 
   <td colname="col2"><span class="codeph"> AXS_HardStopIntervalExpired  </span> </td> 
   <td colname="col3"> Hard stopinterval verlopen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3349 </td> 
   <td colname="col2"><span class="codeph"> AXS_ServerVersionTooHigh  </span> </td> 
   <td colname="col3"> De server wordt uitgevoerd in een versie die hoger is dan de hoogste versie die door de client wordt ondersteund. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3350 </td> 
   <td colname="col2"><span class="codeph"> AXS_ServerVersionTooLow  </span> </td> 
   <td colname="col3"> De server wordt uitgevoerd in een versie die lager is dan de minimale versie die door de client wordt ondersteund. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3351 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DomainTokenInvalid  </span> </td> 
   <td colname="col3"> Domeintoken was ongeldig. Registreer u opnieuw bij het domein om dit probleem op te lossen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3352 </td> 
   <td colname="col2"><span class="codeph"> AXS_DomainTokenTooOld  </span> </td> 
   <td colname="col3"> Het domeinteken is ouder dan het token dat door de licentie wordt vereist. Registreer u opnieuw bij het domein om het probleem op te lossen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3353 </td> 
   <td colname="col2"><span class="codeph"> AXS_DomainTokenTooNew  </span> </td> 
   <td colname="col3"> Het domeintoken is nieuwer dan het token dat door de licentie wordt vereist. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3354 </td> 
   <td colname="col2"><span class="codeph"> AXS_DomainTokenExpired  </span> </td> 
   <td colname="col3"> Domeintoken is verlopen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3355 </td> 
   <td colname="col2"><span class="codeph"> AXS_DomainJoinFailed  </span> </td> 
   <td colname="col3"> Domeinverbinding mislukt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3356 </td> 
   <td colname="col2"><span class="codeph"> AXS_NoCorrespondingRoot  </span> </td> 
   <td colname="col3"> Er is geen hoofdlicentie voor een V3-bladlicentie gevonden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3357 </td> 
   <td colname="col2"><span class="codeph"> AXS_NoValidEmbeddedLicense  </span> </td> 
   <td colname="col3"> Er is geen geldige ingesloten licentie gevonden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3358 </td> 
   <td colname="col2"><span class="codeph"> AXS_NoACPProtectionAvail  </span> </td> 
   <td colname="col3"> Kan niet afspelen omdat het aangesloten analoge apparaat geen ACS-bescherming heeft. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3359 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoCGMSAProtectionAvail  </span> </td> 
   <td colname="col3"> Kan niet afspelen omdat het aangesloten analoge apparaat geen CGMS-A-beveiliging heeft. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3360 </td> 
   <td colname="col2"><span class="codeph"> AXS_DomainRegistrationRequired  </span> </td> 
   <td colname="col3"> Voor inhoud is domeinregistratie vereist. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3361 </td> 
   <td colname="col2"><span class="codeph"> AXS_NotRegisteredToDomain  </span> </td> 
   <td colname="col3"> Machine is niet geregistreerd bij het domein voor de opgegeven metagegevens. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3362 </td> 
   <td colname="col2"><span class="codeph"> AXS_OperationTimeoutError  </span> </td> 
   <td colname="col3"> Asynchrone bewerking duurde langer dan <span class="codeph"> maxOperationTimeout</span>. Alleen geretourneerd door iOS DRMNative Framework. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3363 </td> 
   <td colname="col2"><span class="codeph"> AXS_UnsupportedIOSPlaylistError  </span> </td> 
   <td colname="col3"> De doorgegeven M3U8-afspeellijst bevatte niet-ondersteunde inhoud. Alleen geretourneerd door iOS DRMNative Framework. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3364 </td> 
   <td colname="col2"><span class="codeph"> AXS_NoDeviceId  </span> </td> 
   <td colname="col3"> <p>Het framework heeft de apparaat-id aangevraagd, maar de geretourneerde waarde is leeg. </p> <p>De gebruiker moet het selectievakje <span class="uicontrol"> Id's voor beveiligde inhoud toestaan</span> niet inschakelen in Chrome-instellingen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3365 </td> 
   <td colname="col2"><span class="codeph"> AXS_IncognitoModeNotAllowed  </span> </td> 
   <td colname="col3"> <p>Deze combinatie browser/platform staat het afspelen op Incognito niet toe met DRM beveiligd. </p> <p>De software van de distributeur zou de gebruiker moeten adviseren om de wijze van Incognito weg te gaan of een verschillende browser te gebruiken. Zie <a href="https://forums.adobe.com/thread/1266622" format="https" scope="external"> DRM-fout 3365 oorzaak en resolutie</a> voor meer informatie. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3366 </td> 
   <td colname="col2"><span class="codeph"> AXS_BadParameter  </span> </td> 
   <td colname="col3"> <p>De hostruntime heeft de toegangsbibliotheek aangeroepen met een ongeldige parameter. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3367 </td> 
   <td colname="col2"><span class="codeph"> AXS_BadSignature  </span> </td> 
   <td colname="col3"> m3u8 manifest ondertekenen is mislukt. Alleen geretourneerd door iOS DRMNative Framework of AVE. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3368 </td> 
   <td colname="col2"><span class="codeph"> AXS_UserSettingsNoAccess</span> </td> 
   <td colname="col3"> <p>De gebruiker heeft de bewerking geannuleerd of heeft instellingen ingevoerd die de toegang tot het systeem blokkeren. </p> <p>Deze fout wordt alleen gegenereerd wanneer de SWF-versie 19 of hoger is. Voor achterwaartse compatibiliteit wordt 3321 gegenereerd wanneer het SWF-bestand versie 18 of eerder is. </p> <p>De software van de distributeur moet de gebruiker begeleiden bij een uitleg van de manier waarop toegang tot niet-sandbox-plug-ins kan worden toegestaan. Zie <a href="https://helpx.adobe.com/adobe-access/kb/error-3321.html" format="html" scope="external"> unsandbox-toegang van Google Chrome geweigerd</a> en <a href="https://forums.adobe.com/message/5520902" format="https" scope="external"> DRM-fout 3322/3346/3368 in Chrome (Info-Bar Problems)</a> voor meer informatie. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3369 </td> 
   <td colname="col2"><span class="codeph"> AXS_InterfaceNotAvailable</span> </td> 
   <td colname="col3"> <p>Een vereiste browserinterface is niet beschikbaar. Dit probleem treedt alleen op bij Pepper. De Flash-plug-in en de browserversie komen mogelijk niet overeen. </p> <p>De software van de distributeur zou de gebruiker moeten begeleiden om ervoor te zorgen dat zij de recentste geïnstalleerde versie van browser hebben. </p> <p> Als de incidentie van deze fout toeneemt en overeenkomt met een browserupdate die wordt uitgebracht, gaat u naar Adobe. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3370 </td> 
   <td colname="col2"><span class="codeph"> AXS_ContentIdSettingsNoAccess</span> </td> 
   <td colname="col3"> <p>De gebruiker heeft de instelling <span class="uicontrol"> Id's voor beveiligde inhoud toestaan</span> uitgeschakeld. </p> <p>Tip:  Deze fout is opgetreden bij Pepper-versies 13.0.0.x of hoger. </p> <p>De software van de distributeur zou de gebruiker moeten begeleiden om <span class="uicontrol"> toe te laten herkenningstekens voor beschermde inhoud</span> plaatsen. </p> <p>Het de verrichtingenteam van de verdeler zou de gebruiker moeten begeleiden om <span class="uicontrol"> toe te laten herkenningstekens voor beschermde inhoud</span> plaatsen. </p> <p>Zie <a href="https://forums.adobe.com/message/6518323#6518323" format="https" scope="external"> https://forums.adobe.com/message/6518323#6518323</a> voor meer informatie. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3371 </td> 
   <td colname="col2"><span class="codeph"> AXS_</span><span class="codeph"> NoOPConstraintInPixelConstraints</span> </td> 
   <td colname="col3"> <p>Onjuiste resolutie op basis van uitvoerbeschermingsbeperkingen in de licentie. </p> <p>De software van de distributeur zou een foutenmelding moeten tonen. Vraag de gebruiker om het probleem aan de verdeler met een inhoudstitel te melden. </p> <p>De distributeur moet inhoud opnieuw verpakken met een geldig beleid. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3372 </td> 
   <td colname="col2"><span class="codeph"> AXS_ResolutionLargerThanMaxResolution</span> </td> 
   <td colname="col3"> <p>De resolutie van de inhoud is groter dan de maximale resolutie die is opgegeven in de beperking voor uitvoerbeveiliging. </p> <p>Als het de verrichtingenteam van de verdeler deze fout in hun logboeken ziet, zouden zij het op resolutie-gebaseerde beleid van de outputbescherming moeten herzien, en indien nodig, herverpakken de inhoud. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3373 </td> 
   <td colname="col2"><span class="codeph"> AXS_MinorErr_DisplayResolutionLargerThanConstam</span> </td> 
   <td colname="col3"> <p>De resolutie van de inhoud is groter dan de resolutie die wordt opgegeven door de momenteel actieve beperking voor uitvoerbeveiliging. </p> <p>Als het de verrichtingenteam van de verdeler deze fout in hun logboeken ziet, zouden zij het op resolutie-gebaseerde beleid van de outputbescherming moeten herzien, en indien nodig, herverpakken de inhoud. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3374 </td> 
   <td colname="col2"><span class="codeph"> AAXS_MinorErr_ClientCommProcessFailed</span> </td> 
   <td colname="col3"> <p>Mislukt tijdens client-side communicatie verwerking, bijvoorbeeld bij genereren van aanvragen, verwerking van reacties, slecht autetoken, enzovoort. </p> <p>Als het de verrichtingenteam van de verdeler deze fout in hun logboeken ziet, zouden zij het op resolutie-gebaseerde beleid van de outputbescherming moeten herzien, en indien nodig, herverpakken inhoud. </p> </td> 
  </tr> 
 </tbody> 
</table>

## NATIVE_ERROR: Afspeelwaarden van video {#section_7079501250C2487499639F92EC774525}

De Video Encoder-interface van de AVE retourneert deze meldingen voor het afspelen van video in het metagegevensobject `NATIVE_ERROR`.

<table id="table_5EEB1F60E5854452A8B0BABBE9B32651"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Waarde voor metagegevenssleutel NATIVE_ERROR_CODE </th> 
   <th colname="col2" class="entry"> Waarde voor metagegevenssleutel NATIVE_ERROR_NAME </th> 
   <th colname="col3" class="entry"> Beschrijving </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> -1 </td> 
   <td colname="col2"><span class="codeph"> END_OF_PERIOD</span> </td> 
   <td colname="col3"> Einde van periode. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 0 </td> 
   <td colname="col2"><span class="codeph"> SUCCES</span> </td> 
   <td colname="col3"> Bewerking gelukt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 1 </td> 
   <td colname="col2"> <span class="codeph"> ASYNC_OPERATION_IN_PROGRESS</span> </td> 
   <td colname="col3"> Asynchrone bewerking. Het verzoek om een bewerking is uitgevoerd. Informatie over succes/fout is later beschikbaar. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 2 </td> 
   <td colname="col2"><span class="codeph"> EOF</span> </td> 
   <td colname="col3"> Bewerking niet mogelijk vanwege bestandseinde (EOF). </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 1 </td> 
   <td colname="col2"><span class="codeph"> DECODER_FAILED</span> </td> 
   <td colname="col3"> De decoder is mislukt bij uitvoering. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 4 </td> 
   <td colname="col2"><span class="codeph"> DEVICE_OPEN_ERROR</span> </td> 
   <td colname="col3"> Kan hardwaredecoder niet openen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 5 </td> 
   <td colname="col2"><span class="codeph"> FILE_NOT_FOUND  </span> </td> 
   <td colname="col3"> De bron kan niet worden gevonden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 6 </td> 
   <td colname="col2"><span class="codeph"> GENERIC_ERROR  </span> </td> 
   <td colname="col3"> Algemene fout. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 7 </td> 
   <td colname="col2"><span class="codeph"> IRRECOVERABLE_ERROR  </span> </td> 
   <td colname="col3"> Een foutvoorwaarde waarvan de video-engine niet kan worden hersteld. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 8 </td> 
   <td colname="col2"><span class="codeph"> LOST_CONNECTION_RECOVERABLE  </span> </td> 
   <td colname="col3"> Netwerkfout, probeert te herstellen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 9 </td> 
   <td colname="col2"><span class="codeph"> NO_FIXED_SIZE  </span> </td> 
   <td colname="col3"> De grootte van de bron kan niet worden bepaald. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 10 </td> 
   <td colname="col2"><span class="codeph"> NOT_IMPLEMENTED  </span> </td> 
   <td colname="col3"> Functie niet geïmplementeerd. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 11 </td> 
   <td colname="col2"><span class="codeph"> OUT_OF_MEMORY  </span> </td> 
   <td colname="col3"> Onvoldoende geheugen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 12 </td> 
   <td colname="col2"><span class="codeph"> PARSE_ERROR  </span> </td> 
   <td colname="col3"> Fout bij het parseren van het mediabestand. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 13 </td> 
   <td colname="col2"><span class="codeph"> SIZE_UNKNOWN  </span> </td> 
   <td colname="col3"> De bron heeft een grootte, maar het is onbekend. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 14 </td> 
   <td colname="col2"><span class="codeph"> UNDER_FLOW  </span> </td> 
   <td colname="col3"> Onderstroomvoorwaarde. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 15 </td> 
   <td colname="col2"><span class="codeph"> UNSUPPORTED_CONFIG  </span> </td> 
   <td colname="col3"> Configuration is not supported. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 16 </td> 
   <td colname="col2"><span class="codeph"> UNSUPPORTED_OPERATION  </span> </td> 
   <td colname="col3"> Bewerking wordt niet ondersteund. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 17 </td> 
   <td colname="col2"><span class="codeph"> WAITING_FOR_INIT  </span> </td> 
   <td colname="col3"> Nog niet geïnitialiseerd. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 18 </td> 
   <td colname="col2"><span class="codeph"> INVALID_PARAMETER  </span> </td> 
   <td colname="col3"> Ongeldige parameter. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 19 </td> 
   <td colname="col2"><span class="codeph"> INVALID_OPERATION</span> </td> 
   <td colname="col3"> Bewerking niet toegestaan. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 20 </td> 
   <td colname="col2"><span class="codeph"> OP_ONLY_ALLOWED_IN_PAUSED_STATE</span> </td> 
   <td colname="col3"> De bewerking is alleen toegestaan tijdens het pauzeren. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 21 </td> 
   <td colname="col2"><span class="codeph"> OP_INVALID_WITH_AUDIO_ONLY_FILE</span> </td> 
   <td colname="col3"> Bewerking kan niet worden gebruikt voor bestanden met alleen audio. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 22 </td> 
   <td colname="col2"><span class="codeph"> PREVIOUS_STEP_SEEK_IN_PROGRESS</span> </td> 
   <td colname="col3"> De vorige zoekbewerking wordt nog uitgevoerd. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 23 </td> 
   <td colname="col2"><span class="codeph"> SOURCE_NOT_SPECIFIED  </span> </td> 
   <td colname="col3"> Bron niet opgegeven. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 24 </td> 
   <td colname="col2"><span class="codeph"> RANGE_ERROR</span> </td> 
   <td colname="col3"> De opgegeven waarde ligt buiten het bereik. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 25 </td> 
   <td colname="col2"><span class="codeph"> INVALID_SEEK_TIME</span> </td> 
   <td colname="col3"> Ongeldige zoektijd. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 26 </td> 
   <td colname="col2"><span class="codeph"> FILE_STRUCTURE_INVALID</span> </td> 
   <td colname="col3"> Het opgegeven bestand voldoet niet aan de verwachte syntaxis. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 27 </td> 
   <td colname="col2"><span class="codeph"> COMPONENT_CREATION_FAILURE</span> </td> 
   <td colname="col3"> Een essentieel onderdeel kan niet worden gemaakt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 28 </td> 
   <td colname="col2"><span class="codeph"> DRM_INIT_ERROR</span> </td> 
   <td colname="col3"> Kan DRM-context niet maken. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 29 </td> 
   <td colname="col2"><span class="codeph"> CONTAINER_NOT_SUPPORTED  </span> </td> 
   <td colname="col3"> Containertype wordt niet ondersteund. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 30 </td> 
   <td colname="col2"><span class="codeph"> SEEK_FAILED</span> </td> 
   <td colname="col3"> Seek is mislukt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 31 </td> 
   <td colname="col2"><span class="codeph"> CODEC_NOT_SUPPORTED</span> </td> 
   <td colname="col3"> Niet-ondersteunde codec. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 32 </td> 
   <td colname="col2"><span class="codeph"> NETWORK_UNAVAILABLE</span> </td> 
   <td colname="col3"> Netwerk is niet beschikbaar. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 33 </td> 
   <td colname="col2"><span class="codeph"> NETWORK_ERROR</span> </td> 
   <td colname="col3"> Fout die gegevens van het Netwerk krijgt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 34 </td> 
   <td colname="col2"><span class="codeph"> OVERLOOP</span> </td> 
   <td colname="col3"> Overloop. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 35 </td> 
   <td colname="col2"><span class="codeph"> VIDEO_PROFILE_NOT_SUPPORTED</span> </td> 
   <td colname="col3"> Niet-ondersteund videoprofiel. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 36 </td> 
   <td colname="col2"><span class="codeph"> PERIOD_NOT_LOADED</span> </td> 
   <td colname="col3"> Er is geprobeerd een bewerking uit te voeren in een wachttijd of een periode die nog niet is geladen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 37 </td> 
   <td colname="col2"><span class="codeph"> INVALID_REPLACE_DURATION</span> </td> 
   <td colname="col3"> De opgegeven vervangingsduur is ongeldig of loopt voorbij het einde van de stream. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 38 </td> 
   <td colname="col2"><span class="codeph"> CALLED_FROM_WRONG_THREAD</span> </td> 
   <td colname="col3"> API kan niet worden geroepen van de verkeerde draad. Meestal geldt dit voor API-elementen die alleen vanuit de hoofdthread moeten worden aangeroepen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 39 </td> 
   <td colname="col2"><span class="codeph"> FRAGMENT_READ_ERROR</span> </td> 
   <td colname="col3"> Fout bij lezen van fragment. Geen failover aanwezig. De engine probeert het volgende fragment te lezen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 40 </td> 
   <td colname="col2"><span class="codeph"> GEABORTEERD</span> </td> 
   <td colname="col3"> De bewerking is afgebroken door een expliciete aanroep Afbreken of Vernietig. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 41 </td> 
   <td colname="col2"><span class="codeph"> UNSUPPORTED_HLS_VERSION</span> </td> 
   <td colname="col3"> Kan deze versie van HLS-media niet afspelen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 42 </td> 
   <td colname="col2"><span class="codeph"> CANNOT_FAIL_OVER</span> </td> 
   <td colname="col3"> Kan niet negeren. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 43 </td> 
   <td colname="col2"><span class="codeph"> HTTP_TIME_OUT</span> </td> 
   <td colname="col3"> Er is een time-out opgetreden tijdens het downloaden van HTTP. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 44 </td> 
   <td colname="col2"><span class="codeph"> NETWORK_DOWN  </span> </td> 
   <td colname="col3"> De netwerkverbinding van de gebruiker is verbroken. Het afspelen kan op elk moment worden gestopt en wordt hervat wanneer de verbinding beschikbaar is. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 45 </td> 
   <td colname="col2"><span class="codeph"> NO_USABLE_BITRATE_PROFILE</span> </td> 
   <td colname="col3"> Geen bruikbaar bitsnelheidprofiel gevonden in de stream. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 46 </td> 
   <td colname="col2"><span class="codeph"> BAD_MANIFEST_SIGNATURE</span> </td> 
   <td colname="col3"> Het manifest heeft een slechte handtekening. De manifestondertekeningstest is mislukt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 47 </td> 
   <td colname="col2"><span class="codeph"> CANNOT_LOAD_PLAYLIST</span> </td> 
   <td colname="col3"> Kan een afspeellijst niet laden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 48 </td> 
   <td colname="col2"><span class="codeph"> REPLACEMENT_FAILED</span> </td> 
   <td colname="col3"> Vervanging opgegeven in een API voor invoegen is mislukt. Dit betekent dat de invoeging is gelukt, maar dat de vervanging niet heeft plaatsgevonden. Vervanging kan mislukken als het te vervangen manifest uit de tijdlijn is verwijderd. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 49 </td> 
   <td colname="col2"><span class="codeph"> SWITCH_TO_ASYMMETRIC_PROFILE</span> </td> 
   <td colname="col3"> DRM schakelt over naar een asymmetrisch profiel. Van alle profielen wordt verwacht dat ze in de duur zijn uitgelijnd. Als dat niet het geval is, wordt deze waarschuwing gegenereerd en kan het afspelen schokken. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 50 </td> 
   <td colname="col2"><span class="codeph"> LIVE_WINDOW_MOVED_BACKWARD</span> </td> 
   <td colname="col3"> Van een actief venster wordt alleen de volgende verplaatsing verwacht. Als dat niet het geval is, wordt deze waarschuwing gegenereerd en wordt het venster niet gelezen. Hierdoor kan het afspelen schokken (of stoppen/lang pauzeren) veroorzaken. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 51 </td> 
   <td colname="col2"><span class="codeph"> CURRENT_PERIOD_EXPIRED</span> </td> 
   <td colname="col3"> Live venster wordt na de huidige periode verplaatst. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 52 </td> 
   <td colname="col2"><span class="codeph"> CONTENT_LENGTH_MISMATCH</span> </td> 
   <td colname="col3"> De lengte van de inhoud die door de HTTP-server wordt gerapporteerd, komt niet overeen met de werkelijke mediagrootte. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 53 </td> 
   <td colname="col2"><span class="codeph"> PERIOD_HOLD</span> </td> 
   <td colname="col3"> De mediaslezer kan geen verdere informatie lezen omdat deze de tijd heeft bereikt die door de setHoldAt API is ingesteld. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 54 </td> 
   <td colname="col2"><span class="codeph"> LIVE_HOLD  </span> </td> 
   <td colname="col3">De mediaslezer kan geen segmenten laden omdat het einde van het live venster is bereikt. Het laden van segmenten wordt hervat wanneer de server nieuwe media aan het live venster toevoegt. Deze status wordt meestal bereikt als: 
    <ul id="ul_FCFF658EDA4144E59970B317D6DEB624"> 
     <li id="li_2F6EEEB782D54CD999BC7CC7C0B78B48">De bufferTime<span class="codeph"> is te hoog (gelijk aan of hoger dan de live vensterduur).</span> </li> 
     <li id="li_25CE97115ED64E44AA89977FB5F0DCF7">Een combinatie van een of meer API voor invoegen/wissen heeft meer media vervangen dan er zijn toegevoegd. </li> 
     <li id="li_1B14716B2157492AB1859306D1250523">De volgende periode is een live periode met een media-vervanging die in behandeling is (vanwege de API-aanroep InsertBy) </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 55 </td> 
   <td colname="col2"><span class="codeph"> BAD_MEDIA_INTERLEAVING  </span> </td> 
   <td colname="col3"> De audio- en video-interleave in de media is niet correct uitgevoerd. Dit is een verpakkingsfout. De waarschuwing wordt verzonden wanneer het verschil groter is dan twee seconden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 56 </td> 
   <td colname="col2"><span class="codeph"> DRM_NOT_AVAILABLE</span> </td> 
   <td colname="col3"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 57 </td> 
   <td colname="col2"><span class="codeph"> PLAYBACK_NOT_AUZED</span> </td> 
   <td colname="col3"> Het afspelen van HLS is niet ingeschakeld in de Flash Player. Zie AuthorizedFeatures.enableHLSPlayback. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 58 </td> 
   <td colname="col2"><span class="codeph"> BAD_MEDIA_SAMPLE_FOUND</span> </td> 
   <td colname="col3"> De decoder heeft een ongeldig monster ontvangen dat niet kan worden gedecodeerd. Dit is meestal geen fatale fout, maar geeft aan dat er wellicht glitches in de audio/video voorkomen. Te veel exemplaren van deze fout geven een onjuiste codering of een ongeldig bestand aan. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 59 </td> 
   <td colname="col2"><span class="codeph"> RANGE_SPANS_READ_HEAD</span> </td> 
   <td colname="col3"> Nadat het afspelen is gestart, mag het bereik Invoegen/Vervangen niet de leeskop bevatten. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 60 </td> 
   <td colname="col2"><span class="codeph"> POSTROLL_WITH_LIVE_NOT_ALLOWED</span> </td> 
   <td colname="col3"> Invoegingen achteraf zijn niet toegestaan op live media. Ze zijn echter wel toegestaan nadat de server de media als voltooid heeft gemarkeerd. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 61 </td> 
   <td colname="col2"><span class="codeph"> INTERNAL_ERROR</span> </td> 
   <td colname="col3"> Een zeer zeldzame kwestie die nooit zou mogen voorkomen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 62 </td> 
   <td colname="col2"><span class="codeph"> SPS_PPS_FOUND_OUTSIDE_AVCC</span> </td> 
   <td colname="col3"> De stream volgt niet de verpakkingsaanbeveling om H264 SPS/PPS altijd in een AVCC te plaatsen. Problemen met zoeken en afspelen kunnen worden gezien. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 63 </td> 
   <td colname="col2"><span class="codeph"> PARTIAL_REPLACEMENT</span> </td> 
   <td colname="col3"> De in een API voor invoegen opgegeven vervanging is slechts gedeeltelijk uitgevoerd. Dit gebeurt wanneer replaceDuration zich over de chronologieduur uitstrekt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 64 </td> 
   <td colname="col2"><span class="codeph"> RENDITION_M3U8_ERROR</span> </td> 
   <td colname="col3"> Er is een fout opgetreden bij het laden van de afspeellijst van de vertoning. Dit is alleen voor AVE, niet voor Flash Player. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 65 </td> 
   <td colname="col2"><span class="codeph"> NULL_OPERATION</span> </td> 
   <td colname="col3"> Bewerking doet niets. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 66 </td> 
   <td colname="col2"><span class="codeph"> SEGMENT_SKIPPED_ON_FAILURE</span> </td> 
   <td colname="col3"> Segment kan niet worden afgespeeld en wordt overgeslagen als de toepassing mislukt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 67 </td> 
   <td colname="col2"><span class="codeph"> INCOMPATIBLE_RENDER_MODE</span> </td> 
   <td colname="col3"> Niet-compatibele rendermodus. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 68 </td> 
   <td colname="col2"><span class="codeph"> PROTOCOL_NOT_SUPPORTED  </span> </td> 
   <td colname="col3"> Het webprotocol dat in de URL wordt gebruikt, wordt niet ondersteund. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 69 </td> 
   <td colname="col2"><span class="codeph"> PARSE_ERROR_INCOMPATIBLE_VERSION</span> </td> 
   <td colname="col3"> Fout bij parseren van mediabestand. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 70 </td> 
   <td colname="col2"><span class="codeph"> MANIFEST_FILE_UNEXPECTEDLY_CHANGED</span> </td> 
   <td colname="col3"> Manifest-bestand is op een onverwachte manier gewijzigd. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 71 </td> 
   <td colname="col2"><span class="codeph"> CANNOT_SPLIT_TIMELINE</span> </td> 
   <td colname="col3"> Kan geen splitsingsbewerking op een tijdlijn uitvoeren. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 72 </td> 
   <td colname="col2"><span class="codeph"> CANNOT_ERASE_TIMELINE</span> </td> 
   <td colname="col3"> Kan geen wisbewerking op een tijdlijn uitvoeren. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 73 </td> 
   <td colname="col2"><span class="codeph"> DID_NOT_GET_NEXT_FRAGMENT</span> </td> 
   <td colname="col3"> Het volgende fragment is niet opgehaald. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 74 </td> 
   <td colname="col2"><span class="codeph"> NO_TIMELINE</span> </td> 
   <td colname="col3"> Geen tijdlijn aanwezig in een interne gegevensstructuur. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 75 </td> 
   <td colname="col2"><span class="codeph"> LISTENER_NOT_FOUND</span> </td> 
   <td colname="col3"> Geen listener gevonden in een interne gegevensstructuur. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 76 </td> 
   <td colname="col2"><span class="codeph"> AUDIO_START_ERROR</span> </td> 
   <td colname="col3"> Kan audio niet starten. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 77 </td> 
   <td colname="col2"><span class="codeph"> NO_AUDIO_SINK</span> </td> 
   <td colname="col3"> Er is geen audioband aanwezig in een interne gegevensstructuur. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 78 </td> 
   <td colname="col2"><span class="codeph"> FILE_OPEN_ERROR</span> </td> 
   <td colname="col3"> Kan bestand niet openen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 79 </td> 
   <td colname="col2"><span class="codeph"> FILE_WRITE_ERROR</span> </td> 
   <td colname="col3"> Kan niet naar een bestand schrijven. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 80 </td> 
   <td colname="col2"><span class="codeph"> FILE_READ_ERROR</span> </td> 
   <td colname="col3"> Kan niet lezen uit een bestand. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 81 </td> 
   <td colname="col2"><span class="codeph"> ID3PARSE_ERROR</span> </td> 
   <td colname="col3"> Er is een fout opgetreden bij het parseren van ID3-gegevens. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 82 </td> 
   <td colname="col2"><span class="codeph"> SECURITY_ERROR  </span> </td> 
   <td colname="col3"> Het laden van de inhoud is mislukt vanwege beveiligingsbeperkingen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 83 </td> 
   <td colname="col2"><span class="codeph"> TIMELINE_TOO_SHORT</span> </td> 
   <td colname="col3"> De tijdlijnduur is te kort. Als dit een live stream is, kan er vaak bufferen optreden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 84 </td> 
   <td colname="col2"><span class="codeph"> AUDIO_ONLY_STREAM_START</span> </td> 
   <td colname="col3"> De stream is overgeschakeld naar een alleen-audio stream. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 85 </td> 
   <td colname="col2"><span class="codeph"> AUDIO_ONLY_STREAM_END</span> </td> 
   <td colname="col3"> De stream is overgeschakeld van alleen-audio naar een stream met video. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 87 </td> 
   <td colname="col2"><span class="codeph"> KEY_NOT_FOUND  </span> </td> 
   <td colname="col3"> Kan sleutel niet vinden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 88 </td> 
   <td colname="col2"><span class="codeph"> INVALID_KEY</span> </td> 
   <td colname="col3"> De sleutel is ongeldig. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 89 </td> 
   <td colname="col2"> <span class="codeph"> KEY_SERVER_NOT_FOUND</span> </td> 
   <td colname="col3"> Sleutelserver retourneert geen sleutel. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 90 </td> 
   <td colname="col2"> <span class="codeph"> MAIN_MANIFEST_UPDATE_TO_BE_HANDLED</span> </td> 
   <td colname="col3"> Kan belangrijkste manifestupdate niet behandelen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 91 </td> 
   <td colname="col2"> <span class="codeph"> UNREPORTED_TIME_DISCONTINUITY_FOUND</span> </td> 
   <td colname="col3"> Ongemelde tijddiscontinuïteit (PTS) gevonden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 92 </td> 
   <td colname="col2"> <span class="codeph"> UNMATCHED_AV_DISCONTINUITY_FOUND</span> </td> 
   <td colname="col3"> Niet-overeenkomende audio- en videodiscontinuïteit gevonden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 93 </td> 
   <td colname="col2"><span class="codeph"> TRICKPLAY_ENDED_DUE_TO_ERROR</span> </td> 
   <td colname="col3">Er is een fout opgetreden tijdens het afspelen van media in de <i>truc-modus</i>. De modus Steen afspelen wordt beëindigd en de stream wordt gepauzeerd. Roep <span class="codeph"> Play()</span> aan om de media in de normale modus af te spelen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 95 </td> 
   <td colname="col2"><span class="codeph"> LIVE_WINDOW_MOVED_AHEAD</span> </td> 
   <td colname="col3"> De speler bevindt zich buiten het livevenster en moet voorwaarts proberen in te halen. </td> 
  </tr> 
 </tbody> 
</table>

## NATIVE_ERROR: Cryptowaarden {#section_39365E545CAC49B9A4D4678657BB2155}

De cryptomodule van de Adobe video-engine retourneert deze meldingen in het metagegevensobject `NATIVE_ERROR`.

| Waarde voor metagegevenssleutel NATIVE_ERROR_CODE | Waarde voor metagegevenssleutel NATIVE_ERROR_NAME | Betekenis |
|---|---|---|
| 300 | `CRYPTO_ALGORITHM_NOT_SUPPORTED` | Algorithm being used is not supported. |
| 301 | `CRYPTO_ERROR_CORRUPTED_DATA` | Gegevens zijn beschadigd. |
| 302 | `CRYPTO_ERROR_BUFFER_TOO_SMALL` | Buffer te klein. |
| 303 | `CRYPTO_ERROR_BAD_CERTIFICATE` | Ongeldig certificaat. |
| 304 | `CRYPTO_ERROR_DIGEST_UPDATE` | Samenvattingsupdate. |
| 305 | `CRYPTO_ERROR_DIGEST_FINISH` | Samenvatting voltooid. |
| 306 | `CRYPTO_ERROR_BAD_PARAMETER` | Onjuiste parameter. |
