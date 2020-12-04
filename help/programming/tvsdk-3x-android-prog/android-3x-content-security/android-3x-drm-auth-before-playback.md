---
description: Wanneer de DRM-metagegevens voor een video gescheiden zijn van de mediastream, moet u verifiëren voordat u begint met afspelen.
seo-description: Wanneer de DRM-metagegevens voor een video gescheiden zijn van de mediastream, moet u verifiëren voordat u begint met afspelen.
seo-title: DRM-verificatie vóór afspelen
title: DRM-verificatie vóór afspelen
uuid: be319b04-a506-4278-8275-db32cd3f18aa
translation-type: tm+mt
source-git-commit: e300238be5a2bddc7c6b9bd26682dcb4401959b1
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 1%

---


# DRM-verificatie vóór afspelen {#drm-authentication-before-playback}

Wanneer de DRM-metagegevens voor een video gescheiden zijn van de mediastream, moet u verifiëren voordat u begint met afspelen.

Een video-element kan bijvoorbeeld een gekoppeld DRM-metagegevensbestand hebben:

* `"url": "https://www.domain.com/asset.m3u8"`
* `"drmMetadata": "https://www.domain.com/asset.metadata"`

In dit voorbeeld kunt u `DRMHelper`-methoden gebruiken om de inhoud van het DRM-metagegevensbestand te downloaden, te parseren en te controleren of DRM-verificatie nodig is.

1. Gebruik `loadDRMMetadata` om de metagegevens-URL-inhoud te laden en de gedownloade bytes te parseren naar een `DRMMetadata`.

   >[!TIP]
   >
   >Deze methode is asynchroon en maakt een eigen thread.

   ```java
   public static void loadDRMMetadata( 
       final DRMManager drmManager, 
       final String drmMetadataUrl,  
       final DRMLoadMetadataListener loadMetadataListener); 
   ```

   Bijvoorbeeld:

   ```java
   DRMHelper.loadDRMMetadata(drmManager,  
                                      metadataURL,  
                                      new DRMLoadMetadataListener());
   ```

1. Melden aan de gebruiker dat deze bewerking asynchroon is, is het raadzaam de gebruiker hiervan op de hoogte te stellen.

   Als gebruikers niet weten dat de bewerking asynchroon is, vragen zij zich wellicht af waarom het afspelen nog niet is gestart. U kunt bijvoorbeeld een draaischijf weergeven terwijl de DRM-metagegevens worden gedownload en geparseerd.

1. Voer callbacks in `DRMLoadMetadataListener` uit.

   `loadDRMMetadata` roept deze gebeurtenismanagers.

   ```java
   public interface DRMLoadMetadataListener { 
   
       public void onLoadMetadataUrlStart(); 
   
       /** 
       * @param authNeeded 
       * whether DRM authentication is needed. 
       * @param drmMetadata 
       * the parsed DRMMetadata obtained.    */ 
       public void onLoadMetadataUrlComplete(boolean authNeeded, DRMMetadata drmMetadata); 
       public void onLoadMetadataUrlError(); 
   } 
   ```

   Hier zijn extra details over de managers:

   * `onLoadMetadataUrlStart` Hiermee wordt gedetecteerd wanneer het laden van de metagegevens-URL is gestart.
   * `onLoadMetadataUrlComplete` Hiermee wordt gedetecteerd wanneer de URL van de metagegevens is geladen.
   * `onLoadMetadataUrlError` geeft aan dat de metagegevens niet zijn geladen.

1. Wanneer het laden is voltooid, controleert u het object `DRMMetadata` om te bepalen of DRM-verificatie is vereist.

   ```java
   public static boolean isAuthNeeded(DRMMetadata drmMetadata);
   ```

   Bijvoorbeeld:

   ```java
   @Override 
   public void onLoadMetadataUrlComplete(boolean authNeeded, DRMMetadata drmMetadata) {  
       Log.i(LOG_TAG + "#onLoadMetadataUrlComplete",  
             "Loaded metadata URL contents. Auth needed:" + authNeeded + "."); 
       if (!authNeeded) { 
           // Auth is not required. Start player activity.     
           showLoadingSpinner(false);     
           startPlayerActivity(ASSET_URL); 
           return; 
       } 
   } 
   ```

1. Voer een van de volgende taken uit:

   * Als verificatie niet vereist is, begint u met afspelen.
   * Als verificatie vereist is, voltooit u de verificatie door de licentie aan te schaffen.

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
      */ 
      public static void performDrmAuthentication( 
           final DRMManager drmManager,  
           final DRMMetadata drmMetadata, 
           final String authUser,  
           final String authPass,  
           final DRMAuthenticationListener authenticationListener);
      ```

      In dit voorbeeld worden de naam en het wachtwoord van de gebruiker voor de eenvoud expliciet gecodeerd:

      ```java
      DRMHelper.performDrmAuthentication(drmManager,  
                                         drmMetadata,  
                                         DRM_USERNAME,  
                                         DRM_PASSWORD, new DRMAuthenticationListener() { 
          @Override 
          public void onAuthenticationStart() { 
              Log.i(LOG_TAG + "#onAuthenticationStart", "DRM authentication started."); 
              // Spinner is already showing. 
          } 
          @Override 
          public void onAuthenticationError(int major,  
                                            int minor,  
                                            String errorString,  
                                            String serverErrorURL) { 
              Log.e(LOG_TAG +  
                    "#onAuthenticationError",  
                    "DRM authentication failed. " +  
                    major + " 0x" + Long.toHexString(minor)); 
              showToast(getString(R.string.drmAuthenticationError));   
              showLoadingSpinner(false); 
          } 
          @Override 
          public void onAuthenticationComplete(byte[] authenticationToken) { 
              Log.i(LOG_TAG +  
                    "#onAuthenticationComplete", "Auth successful. Launching content."); 
              showLoadingSpinner(false); 
              startPlayerActivity(ASSET_URL); 
          } 
      }); 
      ```

1. Gebruik een gebeurtenislistener om de verificatiestatus te controleren.

   Dit proces impliceert netwerkmededeling, zodat is dit ook een asynchrone verrichting.

   ```java
   public interface DRMAuthenticationListener { 
       /** 
       * Called to indicate that DRM authentication has started. 
       */ 
       public void onAuthenticationStart(); 
       /** 
       * Called to indicate that DRM authentication has been successful. 
       * 
       * @param authenticationToken 
       * the obtained token, which can be stored locally. 
       */ 
       public void onAuthenticationComplete(byte[] authenticationToken); 
       /** 
       * Called to indicate that an error occurred while performing the DRM 
       * authentication. 
       * 
       * @param major 
       * the major code. 
       * @param minorC 
       * the minor code. 
       * @param errorString 
       * the exception thrown. 
       * @param serverErrorURL 
       * the URL of the server  
       * on which the error occurred 
       */ 
       public void onAuthenticationError(int major,  
                                         int minor,  
                                         String errorString,  
                                         String serverErrorURL); 
   } 
   ```

1. Start het afspelen als de verificatie is gelukt.
1. Als de verificatie niet is gelukt, meldt u dit aan de gebruiker en start u het afspelen niet.

   De toepassing moet eventuele verificatiefouten afhandelen. Verificatie is mislukt voordat TVSDK wordt afgespeeld in een foutstatus en het afspelen wordt gestopt. Uw toepassing moet het probleem oplossen, de speler herstellen en de bron opnieuw laden.
