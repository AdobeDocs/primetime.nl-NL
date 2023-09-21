---
description: Het belangrijkste client-side element van de Primetime DRM-oplossing is DRM Manager. De voorbeeldtoepassing die bij de Android-SDK wordt geleverd, bevat ook een DRMHelper-klasse die kan worden gebruikt om bepaalde DRM-bewerkingen gemakkelijker te implementeren.
title: Overzicht van de primaire DRM-interface
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# Overzicht van de primaire DRM-interface {#primetime-drm-interface-overview}

Het belangrijkste client-side element van de Primetime DRM-oplossing is DRM Manager. De voorbeeldtoepassing die bij de Android-SDK wordt geleverd, bevat ook een `DRMHelper` klasse die kan worden gebruikt om bepaalde DRM-bewerkingen gemakkelijker te implementeren.

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
  >Deze API retourneert een geldige `DRMManager` alleen na het `MediaPlayerEvent.DRM_METADATA` wordt afgegaan. Als u `getDRMManager()` voordat deze gebeurtenis wordt geactiveerd, wordt mogelijk NULL geretourneerd.

* De `DRMHelper` hulpklasse, die nuttig is bij het implementeren van DRM-workflows.
* A `DRMHelper` methode voor het laden van metagegevens, waarmee DRM-metagegevens worden geladen wanneer deze zich in een andere URL dan het medium bevinden.

  ```java
  public static void loadDRMMetadata(final DRMManager drmManager,  
     final String drmMetadataUrl,  
     final DRMLoadMetadataListener loadMetadataListener);
  ```

* A `DRMHelper` methode om de DRM-metagegevens te controleren en te bepalen of verificatie vereist is.

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

Voor meer informatie over DRM, zie [DRM-documentatie](https://helpx.adobe.com/primetime/user-guide.html).
