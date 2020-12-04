---
description: U kunt de functies van het DRM-systeem (Primetime Digital Rights Management) gebruiken om veilige toegang tot uw video-inhoud te bieden. U kunt ook DRM-oplossingen van derden gebruiken als alternatief voor de geïntegreerde Primetime DRM-oplossing met Adobe.
seo-description: U kunt de functies van het DRM-systeem (Primetime Digital Rights Management) gebruiken om veilige toegang tot uw video-inhoud te bieden. U kunt ook DRM-oplossingen van derden gebruiken als alternatief voor de geïntegreerde Primetime DRM-oplossing met Adobe.
seo-title: Overzicht van de primaire DRM-interface
title: Overzicht van de primaire DRM-interface
uuid: 71479464-8356-4732-9774-da9f6084e6ad
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---


# Overzicht {#primetime-drm-interface-overview}

U kunt de functies van het DRM-systeem (Primetime Digital Rights Management) gebruiken om veilige toegang tot uw video-inhoud te bieden. U kunt ook DRM-oplossingen van derden gebruiken als alternatief voor de geïntegreerde Primetime DRM-oplossing met Adobe.

<!--<a id="section_4DD54E085AB345FE9BE00865E56B28DB"></a>-->

Neem contact op met uw Adobe voor de meest actuele informatie over de beschikbaarheid van DRM-oplossingen van derden.

Het belangrijkste client-side element van het DRM-systeem (Primetime Digital Rights Management) is DRM Manager. De voorbeeldtoepassing die bij de Android-SDK wordt geleverd, bevat de klasse `DRMHelper` die aantoont hoe u bepaalde DRM-bewerkingen gemakkelijker kunt implementeren.

Primetime DRM biedt een schaalbare, efficiënte workflow voor het implementeren van inhoudsbeveiliging in TVSDK-toepassingen. U beschermt en beheert de rechten voor uw video-inhoud door een licentie te maken voor elk digitaal mediabestand.

Raadpleeg de DRM-voorbeeldspelercode in het TVSDK-pakket.

Dit zijn de belangrijkste API-elementen voor het werken met DRM:

* Een verwijzing in de mediaspeler naar het DRM-beheerobject dat het DRM-subsysteem implementeert:

   ```java
   MediaPlayer.getDRMManager();
   ```

   >[!TIP]
   >
   >Deze API retourneert alleen een geldig `DRMManager`-object nadat `MediaPlayerEvent.DRM_METADATA` is geactiveerd. Als u `getDRMManager()` roept alvorens deze gebeurtenis brandt, zou het ONGELDIG kunnen terugkeren.

* De hulpklasse `DRMHelper`, die nuttig is wanneer het uitvoeren van DRM werkschema&#39;s.

   U kunt `DRMHelper` in `ReferencePlayer` zien.

* Een `DRMHelper` methode van de meta-gegevenslader, die DRM meta-gegevens laadt wanneer het in een afzonderlijke URL van de media wordt gevestigd.

   ```java
   public static void loadDRMMetadata(final DRMManager drmManager,  
      final String drmMetadataUrl,  
      final DRMLoadMetadataListener loadMetadataListener);
   ```

* Een `DRMHelper` methode om de meta-gegevens te controleren DRM om te bepalen of de authentificatie nodig is.

   ```java
   /** 
   * Return whether authentication is needed for the provided 
   * DRMMetadata. 
   * 
   * @param drmMetadata 
   * The desired DRMMetadata on which to check whether auth is needed. 
   * @return whether authentication is required for the provided metadata 
   */ 
   public static boolean isAuthNeeded(DRMMetadata drmMetadata);
   ```

* `DRMHelper` methode om verificatie uit te voeren.

   ```java
   /** 
   * Helper method to perform DRM authentication. 
   * 
   * @param drmManager 
   * the DRMManager, used to perform the authentication. 
   * @param drmMetadata 
   * the DRMMetadata, containing the DRM specific information. 
   * @param authenticationListener 
   * the listener, on which the user can be notified about the 
   * authentication process status. 
   * @param authUser 
   * the DRM username provider by the user. 
   * @param authPass 
   * the DRM password provided by the user. 
   */ 
   public static void performDrmAuthentication(final DRMManager drmManager,  
   final DRMMetadata drmMetadata,  
   final String authUser,  
   final String authPass,  
   final DRMAuthenticationListener authenticationListener);
   ```

* Gebeurtenissen die uw toepassing op de hoogte stellen van verschillende DRM-activiteiten en -status.

<!--<a id="section_899BD9061D484E1BBA46E84617C36867"></a>-->

Aanvullende relevante API-elementen:

* [com.adobe.ave.drm.DRMManager](https://help.adobe.com/en_US/primetime/api/drm/com/adobe/ave/drm/DRMManager.html)
* [com.adobe.ave.drm.DRMMetdata](https://help.adobe.com/en_US/primetime/api/drm/com/adobe/ave/drm/DRMMetadata.html)
* [com.adobe.ave.drm.DRMPopolicy](https://help.adobe.com/en_US/primetime/api/drm/com/adobe/ave/drm/DRMPolicy.html)
* [com.adobe.ave.drm.DRMAuthenticationMethod](https://help.adobe.com/en_US/primetime/api/drm/com/adobe/ave/drm/DRMAuthenticationMethod.html)
* [com.adobe.ave.drm.DRMAuthenticationCompleteCallback](https://help.adobe.com/en_US/primetime/api/drm/com/adobe/ave/drm/DRMAuthenticationCompleteCallback.html)
* [com.adobe.ave.drm.DRMOperationErrorCallback](https://help.adobe.com/en_US/primetime/api/drm/com/adobe/ave/drm/DRMOperationErrorCallback.html)
* com.adobe.mediacore.drm.DRMAuthenticateListener

<!-- 
Comment Type: draft
(https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.4/com/adobe/mediacore/drm/DRMAuthenticateListener.html)

-->
<!--<a id="section_F58941D68EB94A5EBD1C7454D2A1B17A"></a>-->

Raadpleeg de [Adobe Primetime DRM-documentatie](https://helpx.adobe.com/primetime/user-guide.html) voor meer informatie over DRM.
