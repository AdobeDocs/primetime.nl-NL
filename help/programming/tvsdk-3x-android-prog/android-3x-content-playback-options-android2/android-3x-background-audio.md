---
title: Achtergrondaudio inschakelen
description: Achtergrondaudio inschakelen
copied-description: true
exl-id: 5bb72233-27d0-4968-b32c-c8d5ac5ac8c8
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '63'
ht-degree: 0%

---

# Achtergrondaudio inschakelen {#enable-background-audio}

Om het afspelen van audio in te schakelen wanneer de toepassing op de achtergrond wordt uitgevoerd, moet de toepassing `enableAudioPlaybackInBackground` API van MediaPlayer met true als argument wanneer de speler zich in de status PREPARED bevindt.

```
_mediaPlayer.enableAudioPlaybackInBackground(true);
```

De app moet het afspelen pauzeren wanneer deze de audio-focus verliest tijdens gebeurtenissen zoals het reageren op de telefoon, enz. Het volgende codefragment toont aan hoe te om uit te voeren `OnAudioFocusChangeListener`:

```
/** 
 * Register the AudioFocus Change listener to track Audio focus from device. 
 */ 
 AudioManager.OnAudioFocusChangeListener onAudioFocusChangeListener = new AudioManager.OnAudioFocusChangeListener(){ 
     @Override 
     public void onAudioFocusChange(int focusChange){ 
          switch(focusChange){ 
               case AudioManager.AUDIOFOCUS_GAIN: 
                    break; 
               case AudioManager.AUDIOFOCUS_LOSS_TRANSIENT_CAN_DUCK: 
                    /* lower output volume*/ 
                    break; 
               case AudioManager.AUDIOFOCUS_LOSS: 
               case AudioManager.AUDIOFOCUS_LOSS_TRANSIENT: 
                    if(_lastKnownStatus ==MediaPlayerStatus.PLAYING) 
                         _mediaPlayer.pause(); 
                    break; 
          } 
     } 
}; 
 
AudioManager audioManager = (AudioManager) getActivity().getApplicationContext().getSystemService(Context.AUDIO_SERVICE); 
audioManager.requestAudioFocus(onAudioFocusChangeListener, AudioManager.STREAM_MUSIC, AudioManager.AUDIOFOCUS_GAIN);
```
