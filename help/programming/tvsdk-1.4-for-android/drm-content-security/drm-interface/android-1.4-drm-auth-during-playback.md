---
description: Voer verificatie uit tijdens het afspelen wanneer de DRM-metagegevens voor een video in de mediastream zijn opgenomen.
title: DRM-verificatie tijdens afspelen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# DRM-verificatie tijdens afspelen {#drm-authentication-during-playback}

Voer verificatie uit tijdens het afspelen wanneer de DRM-metagegevens voor een video in de mediastream zijn opgenomen.

Denk aan de functie voor het roteren van licenties, waarbij een element wordt gecodeerd met meerdere DRM-licenties. Elke keer dat nieuwe DRM-metagegevens worden aangetroffen, gebruikt u `DRMHelper` methoden om te controleren of DRM-metagegevens DRM-verificatie vereisen.

>[!NOTE]
>
>In deze zelfstudie worden domeingebonden licenties niet verwerkt. In het ideale geval moet u, voordat u begint met afspelen, controleren of u te maken hebt met een domeingebonden licentie. Indien ja, voer domeinauthentificatie (indien nodig) uit en sluit zich aan bij het domein.

1. Wanneer nieuwe DRM-metagegevens worden aangetroffen in een element, wordt een gebeurtenis verzonden op de toepassingslaag.

   ```java
   mediaPlayer.addEventListener(MediaPlayerEvent.DRM_METADATA,  
                                drmMetadataInfoEventListener); 
   
   DRMMetadataInfoEventListener drmMetadataInfoEventListener =  
     new DRMMetadataInfoEventListener() { 
           @Override 
           public void onDRMMetadataInfo(DRMMetadataInfoEvent drmMetadataInfoEvent) { 
           } 
   };
   ```

1. Gebruik de `DRMMetadata` om te controleren of verificatie nodig is. Als dat niet het geval is, doet u niets. Het afspelen gaat zonder onderbreking door.
1. Anders voert u DRM-verificatie uit. Aangezien deze bewerking asynchroon is en in een andere thread wordt afgehandeld, heeft deze geen invloed op de gebruikersinterface en het afspelen van video.
1. Als de verificatie mislukt, kan de gebruiker de video niet verder weergeven en wordt het afspelen gestopt. Anders wordt het afspelen zonder onderbreking voortgezet.

```java
DRMMetadataInfoEventListener drmMetadataInfoEventListener =  
  new DRMMetadataInfoEventListener() { 
    @Override 
    public void onDRMMetadataInfo(DRMMetadataInfoEvent drmMetadataInfoEvent) { 
        final DRMMetadataInfo drmMetadataInfo = drmMetadataInfoEvent.getDRMMetadataInfo(); 
 
        if (drmMetadataInfo == null || !DRMHelper.isAuthNeeded(drmMetadataInfo.getDRMMetadata())) { 
            return; 
        } 
 
        // Perform DRM auth. 
        // Possible logic might take into consideration a threshold between the current player time and the 
        // DRM metadata start time. For the time being, we resolve it as soon as we receive the DRM metadata. 
 
        DRMManager drmManager = _mediaPlayer.getDRMManager(); 
        if (drmManager == null) { 
            return; 
        } 
 
        SharedPreferences sharedPreferences = PreferenceManager.getDefaultSharedPreferences(getActivity()); 
        String authUser = sharedPreferences.getString(PrimetimeReference.SETTINGS_DRM_USERNAME,  
          getResources().getString(R.string.drmUsername)); 
          String authPass = sharedPreferences.getString(PrimetimeReference.SETTINGS_DRM_PASSWORD,  
          getResources().getString(R.string.drmPassword)); 
 
        DRMHelper.performDrmAuthentication(drmManager, drmMetadataInfo.getDRMMetadata(),  
          authUser, authPass, new DRMAuthenticationListener() { 
 
            @Override 
            public void onAuthenticationStart() { 
            } 
 
            @Override 
            public void onAuthenticationError(int major, int minor, String erroString, String serverErrorURL) { 
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
