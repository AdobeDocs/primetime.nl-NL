---
description: Wanneer de DRM-metagegevens voor een video zijn opgenomen in de mediastream, kunt u verificatie uitvoeren tijdens het afspelen.
title: DRM-verificatie tijdens afspelen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# DRM-verificatie tijdens afspelen {#drm-authentication-during-playback}

Wanneer de DRM-metagegevens voor een video zijn opgenomen in de mediastream, kunt u verificatie uitvoeren tijdens het afspelen.

Bij het draaien van licenties wordt een element gecodeerd met meerdere DRM-licenties. Elke keer dat nieuwe DRM-metagegevens worden aangetroffen, wordt de `DRMHelper` methoden worden gebruikt om te controleren of DRM-verificatie vereist is voor de DRM-metagegevens.

>[!TIP]
>
>Voordat u begint met afspelen, bepaalt u of u te maken hebt met een domeingebonden licentie en of domeinverificatie vereist is. Als ja, voltooi de domeinauthentificatie en sluit zich aan bij het domein.

1. Wanneer nieuwe DRM-metagegevens worden aangetroffen in een element, wordt een gebeurtenis verzonden op de toepassingslaag.

   ```java
   mediaPlayer.addEventListener(MediaPlayerEvent.DRM_METADATA,  
                                drmMetadataInfoEventListener); 
   
   DRMMetadataInfoEventListener drmMetadataInfoEventListener =  
     new DRMMetadataInfoEventListener() { 
       @Override 
       public void onDRMMetadataInfo(DRMMetadataInfoEvent drmMetadataInfoEvent) { 
           ... 
       } 
   };
   ```

1. Gebruik de `DRMMetadata` om te controleren of verificatie nodig is.

   * Als verificatie niet vereist is, hoeft u niets te doen en wordt het afspelen zonder onderbreking voortgezet.
   * Als verificatie vereist is, voltooit u de DRM-verificatie.

     Aangezien deze bewerking asynchroon is en in een andere thread wordt afgehandeld, heeft deze geen invloed op de gebruikersinterface en het afspelen van video.

1. Als de verificatie mislukt, kan de gebruiker niet doorgaan met het weergeven van de video en het afspelen stoppen.

<!--<a id="example_939B95F831A245869F9248E2767F260C"></a>-->

Bijvoorbeeld:

```java
DRMMetadataInfoEventListener drmMetadataInfoEventListener =  
  new DRMMetadataInfoEventListener() { 
    @Override 
    public void onDRMMetadataInfo(DRMMetadataInfoEvent drmMetadataInfoEvent) { 
        final DRMMetadataInfo drmMetadataInfo =  
          drmMetadataInfoEvent.getDRMMetadataInfo(); 
 
        if (drmMetadataInfo == null ||  
          !DRMHelper.isAuthNeeded(drmMetadataInfo.getDRMMetadata())) { 
            return; 
        } 
 
        // Perform DRM auth. 
        // Possible logic might take into consideration a threshold between the  
        // current player time and the DRM metadata start time. For the time being,  
        // we resolve it as soon as we receive the DRM metadata. 
 
        DRMManager drmManager = _mediaPlayer.getDRMManager(); 
        if (drmManager == null) { 
            return; 
        } 
 
        SharedPreferences sharedPreferences =  
          PreferenceManager.getDefaultSharedPreferences(getActivity()); 
        String authUser = sharedPreferences.getString(PrimetimeReference.SETTINGS_DRM_USERNAME,  
          getResources().getString(R.string.drmUsername)); 
        String authPass = sharedPreferences.getString(PrimetimeReference.SETTINGS_DRM_PASSWORD,  
          getResources().getString(R.string.drmPassword)); 
 
        DRMHelper.performDrmAuthentication(drmManager, drmMetadataInfo.getDRMMetadata(),  
          authUser, authPass, new DRMAuthenticationListener() { 
 
            @Override 
            public void onAuthenticationStart() { 
                ... 
            } 
 
            @Override 
            public void onAuthenticationError(int major,  
                                              int minor,  
                                              String erroString,  
                                              String serverErrorURL) { 
                if (getActivity() == null) { 
                    return; 
                } 
                _handler.post(new Runnable() { 
                    @Override 
                    public void run() { 
                        showToast(getString(R.string.drmAuthenticationError)); 
                        getActivity().finish(); 
                    } 
                }); 
            } 
 
            @Override 
            public void onAuthenticationComplete(byte[] authenticationToken) { 
            } 
 
        }); 
    } 
}; 
```
