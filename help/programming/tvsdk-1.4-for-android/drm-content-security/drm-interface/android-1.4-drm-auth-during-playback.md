---
description: Voer verificatie uit tijdens het afspelen wanneer de DRM-metagegevens voor een video in de mediastream zijn opgenomen.
seo-description: Voer verificatie uit tijdens het afspelen wanneer de DRM-metagegevens voor een video in de mediastream zijn opgenomen.
seo-title: DRM-verificatie tijdens afspelen
title: DRM-verificatie tijdens afspelen
uuid: a1a63e3e-be34-49e1-96c4-ae266003b3d1
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---


# DRM-verificatie tijdens afspelen {#drm-authentication-during-playback}

Voer verificatie uit tijdens het afspelen wanneer de DRM-metagegevens voor een video in de mediastream zijn opgenomen.

Denk aan de functie voor het roteren van licenties, waarbij een element wordt gecodeerd met meerdere DRM-licenties. Telkens wanneer nieuwe DRM-metagegevens worden aangetroffen, gebruikt u `DRMHelper`-methoden om te controleren of DRM-metagegevens DRM-verificatie vereisen.

>[!NOTE]
>
>In deze zelfstudie worden domeingebonden licenties niet verwerkt. Ideaal gezien, alvorens playback te beginnen, controleer of u met een domein gebonden vergunning behandelt. Indien ja, voer domeinauthentificatie (indien nodig) uit en sluit zich aan bij het domein.

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

1. Gebruik `DRMMetadata` om te controleren of de authentificatie nodig is. Zo niet, niets doen; het afspelen wordt zonder onderbreking voortgezet.
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
