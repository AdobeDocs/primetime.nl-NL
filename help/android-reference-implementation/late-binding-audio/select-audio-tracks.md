---
title: Audiotracks selecteren
description: Audiotracks selecteren
copied-description: true
exl-id: d4a7260a-82dd-4b57-8037-b91815d9b954
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 0%

---

# Audiotracks selecteren{#select-the-audio-tracks}

Als u audiotracks wilt selecteren voor audio die laat wordt gekoppeld, implementeert u [IAAConfig](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IAAConfig.html).

| Aan... | Bellen... |
|---|---|
| Een lijst met beschikbare AA-tracks ophalen | [getAudioTracks()](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/AAManager.html#getAudioTracks()) |
| Huidige geselecteerde track ophalen | [getSelectedAudioTrack()](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/AAManager.html#getSelectedAudioTrack()) |
| Een AA-track selecteren | [selectAlternateAudioTrack()](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/AAManager.html#selectAlternateAudioTrack(int)) |

In het volgende codevoorbeeld ziet u hoe de voorbeeldimplementatie de audiotracks van de TVSDK ophaalt en de geselecteerde track toewijst aan het bijbehorende media-item:

```java
/** 
 * Displays a chooser dialog, allowing the user to select the desired 
 * alternate audio track. 
 */ 
private void displayAlternateAudioDialog() { 
    PrimetimeReference.logger.i(LOG_TAG + "#selectAlternateAudio", 
      "Displaying alternate audio chooser dialog."); 
    final int selectedAlternateAudio = aaManager.getSelectedAudioTrackIndex(); 
    if (selectedAlternateAudio != AAManagerOn.INVALID_AUDIO_TRACK) { 
        final String items[] = aaManager.getAudioTracks(); 
        new AlertDialog.Builder(getActivity()) 
          .setTitle(R.string.PlayerControlAADialogTitle) 
          .setSingleChoiceItems(items, selectedAlternateAudio, 
          new DialogInterface.OnClickListener() { 
              public void onClick(DialogInterface dialog, int whichButton) { 
                  boolean result =  
                    aaManager.selectAlternateAudioTrack(whichButton); 
                  if (result) { 
                      PrimetimeReference.logger.i(LOG_TAG 
                                                  + "#selectAlternateAudio", 
                                                  "Audio track selection successful"); 
                  } else { 
                      PrimetimeReference.logger.i(LOG_TAG 
                                            + "#selectAlternateAudio", 
                                            "Audio track selection failed"); 
                  } 
                  // Dismiss dialog. 
                  dialog.cancel(); 
              } 
          }).setNegativeButton(R.string.PlayerControlCCDialogCancel, 
                               new DialogInterface.OnClickListener() { 
              public void onClick(DialogInterface dialog, 
                                    int whichButton) { 
                                // Just cancel the dialog. 
              } 
          }).show(); 
 
    } else { 
        PrimetimeReference.logger.i(LOG_TAG + "#selectAlternateAudioFailed", 
                "Unable to detect the currently selected audio track."); 
        Toast.makeText(getActivity(), 
                "Unable to detect the currently selected audio track", 
                Toast.LENGTH_SHORT).show(); 
    } 
} 
```
