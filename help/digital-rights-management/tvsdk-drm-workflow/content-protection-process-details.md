---
seo-title: Gegevens van het proces voor het verkrijgen van licenties
title: Gegevens van het proces voor het verkrijgen van licenties
uuid: 4825c49e-fa6f-4c98-9d21-a2743930ca2e
translation-type: tm+mt
source-git-commit: 3fdef12b717bb6f70ca27d9278de61d709f8349c

---


# Gegevens van het proces voor het verkrijgen van licenties {#license-acquisition-process-details}

Dit proces biedt een gedetailleerde weergave op API-niveau van de workflow voor met primetime DRM beveiligde inhoud:

1. Laad met een `URLLoader` object de bytes van het metagegevensbestand van de beveiligde inhoud.

   Stel dit object in op een variabele, zoals `metadata_bytes`. Alle inhoud die door Primetime DRM wordt beheerd, heeft Primetime DRM-metagegevens. Wanneer de inhoud is verpakt, kunnen deze metagegevens worden opgeslagen als een afzonderlijk metagegevensbestand ( [!DNL .metadata]) naast de inhoud. De metagegevens kunnen ook Base64-gecodeerd zijn en in de hoofdtekst van het videomanifestbestand worden ingevoegd. Zie Media-bestanden [in een](../protecting-content/packaging-media-overview/packaging-media-files.md)pakket plaatsen voor meer informatie.
   1. Verwijder zo nodig het uitroepteken `!` van het begin van de tekenreeks.
   1. Indien nodig voor HLS- of HDS-inhoud, decodeert u de opgenomen metagegevens in de tekenreeks Base64-codering naar binaire gegevens voordat u deze doorgeeft.
1. Maak een `DRMContentData` instantie.

   Plaats deze code in een blok try-catch:

   ```
   new DRMContentData(metadata_bytes)
   ```

   waarbij `metadata_bytes` het `URLLoader` object is verkregen in Stap 1.

   [iOS: DRMMetadata](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_metadata.html)

   [Android: DRMMetadata](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/index.html)

1. Maak listeners om te luisteren naar de berichten `DRMStatusEvent` en `DRMErrorEvent` te verzenden vanuit het `DRMManager` object.

   ```
   DRMManager.addEventListener(DRMStatusEvent.DRM_STATUS, onDRMStatus); 
   DRMManager.addEventListener(DRMErrorEvent.DRM_ERROR, onDRMError);
   ```

   Controleer in de `DRMStatusEvent` listener of de licentie geldig is (niet null). Ga in de `DRMErrorEvent` listener naar `DRMErrorEvents`. Zie De klasse *DRMStatusEvent* gebruiken en de klasse *DRMErrorEvent* gebruiken in deze handleiding.

1. Laad de licentie die vereist is om de inhoud af te spelen.
Probeer eerst een lokaal opgeslagen licentie te laden om de inhoud af te spelen:

   ```
   DRMManager.loadvoucher(drmContentData, LoadVoucherSetting.LOCAL_ONLY)
   ```

   [Android: DRMManager.verwervingLicense()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#acquireLicense(com.adobe.ave.drm.DRMMetadata,%20com.adobe.ave.drm.DRMAcquireLicenseSettings,%20com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMLicenseAcquiredCallback))

   [iOS: verwervingLicense:](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a52accb5ed5b49d6e5d91277d78279f1b)

   Nadat het laden is voltooid, wordt het `DRMManager` object verzonden `DRMStatusEvent.DRM_Status`.

1. Controleer het `DRMVoucher` object.


   Als het `DRMVoucher` object niet null is, is de licentie geldig. Ga naar Stap 9.

   [Android: DRMLicenseAcquiredCallback](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMLicenseAcquiredCallback.html)

   [iOS: DRMLicenseAcquired](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/_d_r_m_interface_8h.html#afe5a9e3a003f312ee268d9b00927fa6d)
1. Controleer de authentificatiemethode die door het beleid voor deze inhoud wordt vereist.

   Gebruik de `DRMContentData.authenticationMethod` eigenschap.
   1. Als de authentificatiemethode is, ga naar Stap 9. `ANONYMOUS` 

      [Android: DRMAuthenticationMethod](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/index.html?com/adobe/ave/drm/DRMLicenseAcquiredCallback.html)

      [iOS: DRMAuthenticationMethod](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/_d_r_m_interface_8h.html#a2003f29af93898b52a4123c2dd92c457)
   1. Als de verificatiemethode is `USERNAME_AND_PASSWORD`, moet uw toepassing een mechanisme bieden waarmee de gebruiker referenties kan invoeren.

      Geef de gebruikersgegevens door aan de licentieserver om de gebruiker te verifiëren:

      ```
      DRMManager.authenticate( metadata.serverURL, metadata.domain, username, password)
      ```

      De `DRMManager` verzendt a `DRMAuthenticationErrorEvent` als de authentificatie ontbreekt, of a `DRMAuthenticationCompleteEvent` als de authentificatie slaagt. Maak listeners voor deze gebeurtenissen.

      [Android: authenticate()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#authenticate(com.adobe.ave.drm.DRMMetadata,%20java.lang.String,%20java.lang.String,%20java.lang.String,%20java.lang.String,%20com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMAuthenticationCompleteCallback))

      [iOS: authenticeren:](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a169c1441f196a834094a8e0f5ecb4aca)

      >[!NOTE]
      >
      >Adobe raadt u aan een veiliger mechanisme te gebruiken om referenties te verstrekken. Zie [KeyGenParameterSpec voor referentie](https://developer.android.com/reference/android/security/keystore/KeyGenParameterSpec.html).

   1. Als de authentificatiemethode is `UNKNOWN`, moet u een methode van de douaneauthentificatie gebruiken.

      In dit geval heeft de inhoudsprovider ervoor gekozen de verificatie offline uit te voeren, zonder gebruik te maken van de Primetime API&#39;s. De procedure van de douaneauthentificatie moet een authentificatietoken veroorzaken die tot de `DRMManager.setAuthenticationToken()` methode kan worden overgegaan.

      [Android: setAuthenticationToken()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#setAuthenticationToken(com.adobe.ave.drm.DRMMetadata,%20java.lang.String,%20byte[],%20com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMOperationCompleteCallback))

      [iOS: setAuthenticationToken:](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a17884b5d9bcc5b0b39503f61140f9b09)

      >[!NOTE]
      >
      >U kunt ook aangepaste gegevens van de client naar de licentieserver verzenden, ongeacht de verificatiemethode. `.setAuthenticationToken()` Dit is een overbelasting van de API, aangezien dit mechanisme de enige manier is om dynamische aangepaste gegevens van de client naar de licentieserver te verzenden op het moment dat de licentie wordt aangeschaft. Deze methode voor het transport van aangepaste gegevens wordt uitgebreid besproken in verschillende forumartikelen in de [Primetime DRM-forums (Adobe Access) ](https://forums.adobe.com/community/adobe_access).

1. Als de verificatie mislukt, moet uw toepassing terugkeren naar stap 6.

   Zorg ervoor dat uw toepassing een mechanisme heeft om herhaalde mislukte verificaties af te handelen en te beperken. Zo kunt u na drie pogingen een bericht weergeven voor de gebruiker dat de verificatie is mislukt en dat de inhoud niet kan worden afgespeeld.
1. Als u het opgeslagen token wilt gebruiken in plaats van de gebruiker te vragen referenties in te voeren, stelt u het token in met de `DRMManager.setAuthenticationToken()` methode.

   Vervolgens downloadt u de licentie van de licentieserver en speelt u de inhoud af zoals in stap 6.
   1. **Optioneel:** Als de verificatie slaagt, kunt u het verificatietoken vastleggen. Dit is een bytearray die in het geheugen is opgeslagen.

      Hiermee wordt dit token opgehaald bij de `DRMAuthenticationCompleteEvent.token` eigenschap. U kunt het verificatietoken opslaan en gebruiken, zodat de gebruiker niet herhaaldelijk referenties voor deze inhoud hoeft in te voeren. De licentieserver bepaalt de geldige periode van het verificatietoken.

      [Android: OperationComplete()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMOperationCompleteCallback.html)

      [iOS: DRMOperationComplete](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/_d_r_m_interface_8h.html#a5f2392ec6661b51bf7b0df71cd514731)
1. Als de verificatie is gelukt, downloadt u de licentie van de licentieserver:

   ```
   DRMManager.loadvoucher( 
      drmContentData, 
      LoadVoucherSetting.FORCE_REFRESH)
   ```

   Nadat het laden is voltooid, wordt het `DRMManager` object verzonden `DRMStatusEvent.DRM_STATUS`. Luister naar deze gebeurtenis en wanneer deze wordt verzonden, kunt u de inhoud afspelen.  Speel de video door een voorwerp te creëren Primetime en dan zijn `play()` methode te roepen:

   ```
   stream = new Primetime(connection); 
   stream.addEventListener(DRMStatusEvent.DRM _STATUS, drmStatusHandler); 
   stream.addEventListener(DRMErrorEvent.DRM_ERROR, drmErrorHandler); 
   stream.addEventListener(NetStatusEvent.NET_STATUS, netStatusHandler); 
   stream.client = new CustomClient(); 
   video.attachPrimetime(stream); 
   stream.play(videoURL);
   ```

   [Android: verwervingLicense()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#acquireLicense(com.adobe.ave.drm.DRMMetadata,%20com.adobe.ave.drm.DRMAcquireLicenseSettings,%20com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMLicenseAcquiredCallback))

   [iOS: verwervingLicense:](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a52accb5ed5b49d6e5d91277d78279f1b)