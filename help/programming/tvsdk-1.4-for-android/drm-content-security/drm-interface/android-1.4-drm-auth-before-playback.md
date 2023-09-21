---
description: Wanneer de DRM-metagegevens voor een video gescheiden zijn van de mediastream, moet u verificatie uitvoeren voordat u begint met afspelen.
title: DRM-verificatie vóór afspelen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# DRM-verificatie vóór afspelen {#drm-authentication-before-playback}

Wanneer de DRM-metagegevens voor een video gescheiden zijn van de mediastream, moet u verificatie uitvoeren voordat u begint met afspelen.

Een video-element kan een gekoppeld DRM-metagegevensbestand hebben. Bijvoorbeeld:

* &quot;url&quot;: &quot;ht<span></span>tps://www.domain.com/asset.m3u8&quot;
* &quot;drmMetadata&quot;: &quot;ht<span></span>tps://www.domain.com/asset.metadata&quot;

Wanneer dit het geval is, gebruik `DRMHelper` methoden om de inhoud van het DRM-metagegevensbestand te downloaden, te parseren en te controleren of DRM-verificatie nodig is.

1. Gebruiken `loadDRMMetadata` om de URL-inhoud van metagegevens te laden en de gedownloade bytes te parseren naar een `DRMMetadata`.

   Zoals elke andere netwerkverrichting, is deze methode asynchroon, creërend zijn eigen draad.

   ```java
   public static void loadDRMMetadata( 
       final DRMManager drmManager, 
       final String drmMetadataUrl,  
       final DRMLoadMetadataListener loadMetadataListener); 
   ```

   Bijvoorbeeld:

   ```java
   DRMHelper.loadDRMMetadata(drmManager, metadataURL, new DRMLoadMetadataListener());
   ```

1. Omdat de bewerking asynchroon is, is het een goed idee om de gebruiker hiervan bewust te maken. Anders zal hij zich afvragen waarom zijn afspelen niet begint. Geef bijvoorbeeld een draaischijf weer terwijl de DRM-metagegevens worden gedownload en geparseerd.
1. Implementeer de callbacks in de `DRMLoadMetadataListener`. De `loadDRMMetadata` roept deze gebeurtenismanagers (verzendt deze gebeurtenissen).

   ```java
   public interface  
    <b>DRMLoadMetadataListener</b> { 
    public void  
    <b>onLoadMetadataUrlStart</b>(); 
    /** 
     * @param authNeeded 
     * whether DRM authentication is needed. 
     * @param drmMetadata 
     * the parsed DRMMetadata obtained.    */ 
    public void  
    <b>onLoadMetadataUrlComplete</b>(boolean authNeeded, DRMMetadata drmMetadata); 
    public void  
    <b>onLoadMetadataUrlError</b>(); 
   }
   ```

   * `onLoadMetadataUrlStart` Hiermee wordt gedetecteerd wanneer het laden van de metagegevens-URL is gestart.
   * `onLoadMetadataUrlComplete` Hiermee wordt gedetecteerd wanneer de URL van de metagegevens is geladen.
   * `onLoadMetadataUrlError` geeft aan dat de metagegevens niet zijn geladen.

1. Wanneer het laden is voltooid, inspecteert u de `DRMMetadata` om te zien of DRM-verificatie nodig is.

   ```java
   public static boolean <b>isAuthNeeded</b>(DRMMetadata drmMetadata);
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
   ```

1. Als verificatie niet nodig is, begint u met afspelen.
1. Als verificatie nodig is, voert u de verificatie uit door de licentie aan te schaffen.

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

   In dit voorbeeld worden voor de eenvoud de naam en het wachtwoord van de gebruiker expliciet gecodeerd.

   ```java
   DRMHelper.performDrmAuthentication(drmManager, drmMetadata, DRM_USERNAME, DRM_PASSWORD,  
     new DRMAuthenticationListener() { 
       @Override 
       public void onAuthenticationStart() { 
           Log.i(LOG_TAG + "#onAuthenticationStart", "DRM authentication started."); 
           // Spinner is already showing. 
       } 
       @Override 
       public void onAuthenticationError(int major, int minor, String errorString, String serverErrorURL) {  
           Log.e(LOG_TAG + "#onAuthenticationError", "DRM authentication failed. " +  
             major + " 0x" + Long.toHexString(minor)); 
           showToast(getString(R.string.drmAuthenticationError));   
           showLoadingSpinner(false); 
       } 
       @Override 
       public void onAuthenticationComplete(byte[] authenticationToken) { 
           Log.i(LOG_TAG + "#onAuthenticationComplete", "Auth successful. Launching content."); 
           showLoadingSpinner(false); 
           startPlayerActivity(ASSET_URL); 
       } 
   }); 
   ```

1. Dit impliceert ook netwerkmededeling, daarom is dit ook een asynchrone verrichting. Gebruik een gebeurtenislistener om de verificatiestatus te controleren.

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
       public void onAuthenticationError(int major, int minor,  
         String errorString, String serverErrorURL); 
   } 
   ```

1. Start het afspelen als de verificatie is gelukt.
1. Als de verificatie niet is gelukt, meldt u dit aan de gebruiker en start u het afspelen niet.

De toepassing moet eventuele verificatiefouten afhandelen. Verificatie is mislukt voordat TVSDK wordt afgespeeld in een foutstatus. De status wordt gewijzigd in ERROR, er wordt een fout gegenereerd met de foutcode uit de DRM-bibliotheek en het afspelen wordt gestopt. Uw toepassing moet het probleem oplossen, de speler opnieuw instellen en de bron opnieuw laden.
