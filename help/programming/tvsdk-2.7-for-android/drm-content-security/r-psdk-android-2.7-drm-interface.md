---
description: Het belangrijkste client-side element van de Primetime DRM-oplossing is DRM Manager. De voorbeeldtoepassing die bij de Android-SDK wordt geleverd, bevat ook een DRMHelper-klasse die kan worden gebruikt om bepaalde DRM-bewerkingen gemakkelijker te implementeren.
seo-description: Het belangrijkste client-side element van de Primetime DRM-oplossing is DRM Manager. De voorbeeldtoepassing die bij de Android-SDK wordt geleverd, bevat ook een DRMHelper-klasse die kan worden gebruikt om bepaalde DRM-bewerkingen gemakkelijker te implementeren.
seo-title: Overzicht van de primaire DRM-interface
title: Overzicht van de primaire DRM-interface
uuid: d77a98c8-c1f5-4fe3-8d0b-3d21e288f228
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Overzicht van de primaire DRM-interface {#primetime-drm-interface-overview}

Het belangrijkste client-side element van de Primetime DRM-oplossing is DRM Manager. De voorbeeldtoepassing die bij de Android-SDK wordt geleverd, bevat ook een DRMHelper-klasse die kan worden gebruikt om bepaalde DRM-bewerkingen gemakkelijker te implementeren.

<!--<a id="section_4DD54E085AB345FE9BE00865E56B28DB"></a>-->

Primetime DRM biedt een schaalbare, efficiënte workflow voor het implementeren van inhoudsbeveiliging in TVSDK-toepassingen. U beschermt en beheert de rechten voor uw video-inhoud door een licentie te maken voor elk digitaal mediabestand.

Zie de DRM-voorbeeldspelercode in het TVSDK-pakket voor meer informatie.

Hier volgen de belangrijkste API-elementen voor het werken met DRM:

* Een verwijzing in de mediaspeler naar het DRM-beheerobject dat het DRM-subsysteem implementeert:

   ```java
   MediaPlayer.getDRMManager();
   ```

   >[!TIP]
   >
   >Deze API retourneert alleen een geldig `DRMManager` object nadat het `MediaPlayerEvent.DRM_METADATA` is geactiveerd. Als u roept `getDRMManager()` voordat deze gebeurtenis wordt geactiveerd, wordt mogelijk NULL geretourneerd.

* De hulpklasse, die nuttig is bij het implementeren van DRM-workflows. `DRMHelper`
* Een methode voor het laden van `DRMHelper` metagegevens, waarmee DRM-metagegevens worden geladen wanneer deze zich in een andere URL dan het medium bevinden.

   ```java
   public static void loadDRMMetadata(final DRMManager drmManager,  
      final String drmMetadataUrl,  
      final DRMLoadMetadataListener loadMetadataListener);
   ```

* Een `DRMHelper` methode om de DRM-metagegevens te controleren en te bepalen of verificatie vereist is.

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

<!--<a id="section_F58941D68EB94A5EBD1C7454D2A1B17A"></a>-->

Raadpleeg de [DRM-documentatie](https://helpx.adobe.com/primetime/user-guide.html)voor meer informatie over DRM.
