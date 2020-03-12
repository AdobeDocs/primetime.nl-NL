---
seo-title: Achtergrondaudio inschakelen
title: Achtergrondaudio inschakelen
uuid: 1e7319f5-ee16-47bd-bfd5-d3dcfe69bf4b
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Achtergrondaudio inschakelen {#enable-background-audio}

Om het afspelen van audio mogelijk te maken wanneer de toepassing zich op de achtergrond bevindt, moet de toepassing de API van MediaPlayer aanroepen met de waarde true als het argument wanneer de speler zich in de status PREPARED bevindt. `enableAudioPlaybackInBackground`

```
_mediaPlayer.enableAudioPlaybackInBackground(true);
```

De app moet het afspelen pauzeren wanneer deze de audio-focus verliest tijdens gebeurtenissen zoals het reageren op de telefoon, enz. Het volgende codefragment toont aan hoe te om `OnAudioFocusChangeListener`te uitvoeren:

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

