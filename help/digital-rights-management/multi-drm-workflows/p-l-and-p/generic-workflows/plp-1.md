---
description: U kunt de Offline verpakker van Adobe gebruiken om inhoud voor te bereiden voor om het even welke DRM oplossingen die door Primetime Cloud DRM, aangedreven door ExpressPlay worden gesteund.
seo-description: U kunt de Offline verpakker van Adobe gebruiken om inhoud voor te bereiden voor om het even welke DRM oplossingen die door Primetime Cloud DRM, aangedreven door ExpressPlay worden gesteund.
seo-title: Primetime Packager / Cloud DRM / TVSDK
title: Primetime Packager / Cloud DRM / TVSDK
uuid: e54a0e4d-c8ea-46d4-b1b0-bed8a680f8f5
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Primetime Packager / Cloud DRM / TVSDK {#primetime-packager-cloud-drm-tvsdk}

U kunt de Offline verpakker van Adobe gebruiken om inhoud voor te bereiden voor om het even welke DRM oplossingen die door Primetime Cloud DRM, aangedreven door ExpressPlay worden gesteund.

Bij deze set instructies wordt ervan uitgegaan dat u al een ExpressPlay-beheerdersaccount hebt ingesteld: [Primetime DRM Cloud, snel starten](../../../multi-drm-workflows/quick-start/quick-overview.md).
1. Kies de infrastructuur die u wilt gebruiken voor het verpakken van uw inhoud. Primetime Packager ondersteunt zowel opdrachtregelpakketten als op configuratie gebaseerde pakketten van inhoud voor gebruik met de DRM&#39;s FairPlay, Widevine en PlayReady. De volgende indelingen en codering worden momenteel ondersteund in TVSDK (met meer in voorbereiding):

   * DASH (CENC) / PlayReady, Windows - voor HTML5
   * HLS / FairPlay, Access - voor iOS

1. Kies een Key Management System (KMS):

   * KMS ( [ExpressPlay Key Storage](https://www.expressplay.com/developer/key-storage/)) van ExpressPlay gebruiken; dit systeem beheert uw inhoudstoetsen via de RESTful-API van ExpressPlay.

      of...

   * Stel uw eigen KMS in. Maak een database met inhoudssleutels die u kunt selecteren op basis van Content-ID.

      In beide gevallen beheert het KMS een voorraad inhoudssleutels, waarbij elke sleutel een bijbehorende Content-ID heeft.

1. Verpak uw inhoud. Met Primetime Packager kunt u een stuk inhoud verpakken voor een specifieke DRM-oplossing of voor meerdere DRM-oplossingen.

   De volgende voorbeeldopdrachten tonen enkele voorbeelden van inhoud verpakken voor verschillende DRM-oplossingen:

   * [Widevine met Primetime Packager](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf#page=19) (genereert MPD-bestand):

      ```
      java -jar OfflinePackager.jar \ 
        -in_path [ 
        <your_content.mp4>] \ 
        -out_type dash \ 
        -out_path [ 
        <your_out_file_path>] \ 
        -drm \ 
        -drm_sys WIDEVINE \ 
        -key_file_path "creds/widevine_key.bin" \ 
        -widevine_key_id [ 
        <some_keyID>] \ 
        -widevine_content_id [ 
        <some_content-ID] \ 
        -widevine_header provider:intertrust#content_id:2a
      ```

   * [FairPlay met Primetime Packager](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf#page=20) (genereert een M3U8-bestand):

      ```
      java -jar OfflinePackager.jar  
        -in_path [ 
        <your_content.mp4>]  
        -out_type hls  
        -out_path [ 
        <your_out_file_path>]  
        -drm  
        -drm_sys FAIRPLAY  
        -key_file_path "creds/fairplay_key.bin"  
        -key_url "user_provided_value"
      ```

      >[!NOTE]
      >
      >De `key_url` waarde wordt gekopieerd zoals in het M3U8-bestand.

1. Maak een &quot;storefront server&quot;.

       De storefront-server moet de volgende bewerkingen verwerken:
   
   1. Klantenselectie van inhoud. Deze implementatie moet een eindpunt voor cliënten omvatten om een inhoudstoken voor een specifieke inhoudsidentiteitskaart aan te vragen.
   1. Klantrechten
   1. Aanvragen voor een licentietoken (ExpressPlay) van de client ( [ExpressPlay-licentietoken aanvraag / reactieverwijzing](../../../multi-drm-workflows/license-token-req-resp-ref/license-req-resp-overview.md))

1. Maak uw client.

       De client moet een aanroep naar uw winkelserver bevatten. Adobe raadt aan dat de client de storefront aanroept nadat de gebruiker inhoud selecteert en nadat de gebruiker is geverifieerd. Geef vervolgens het token dat door ExpressPlay is geretourneerd, door aan de speler voor licentieaanvragen. Hier vindt u informatie over de implementatie van de DRM-component van uw spelers:
   
   * [TVSDK van browser voor HTML5](https://help.adobe.com/en_US/primetime/psdk/browser_tvsdk/index.html#PSDKs-reference-DRM_interface_overview)
   * [iOS](../../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-apple-fairplay-tvsdk.md)

1. Met het licentietoken in de hand kan de client nu de aanvraag-URL afleiden van het token en de licentieaanvraag indienen bij ExpressPlay, waarna de geselecteerde inhoud voor de gebruiker wordt afgespeeld.
