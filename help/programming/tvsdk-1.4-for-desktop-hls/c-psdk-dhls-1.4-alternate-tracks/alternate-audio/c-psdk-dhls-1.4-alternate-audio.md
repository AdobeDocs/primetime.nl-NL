---
description: Met alternatief geluid (late binding) kunt u schakelen tussen beschikbare audiotracks voor een videotrack. Op deze manier kunnen gebruikers een taaltrack selecteren wanneer de video wordt afgespeeld.
seo-description: Met alternatief geluid (late binding) kunt u schakelen tussen beschikbare audiotracks voor een videotrack. Op deze manier kunnen gebruikers een taaltrack selecteren wanneer de video wordt afgespeeld.
seo-title: Alternatieve audio
title: Alternatieve audio
uuid: d7e61a2a-1985-4dba-9c6d-0e139ffde46a
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Alternatieve audio{#alternate-audio}

Met alternatief geluid (late binding) kunt u schakelen tussen beschikbare audiotracks voor een videotrack. Op deze manier kunnen gebruikers een taaltrack selecteren wanneer de video wordt afgespeeld.

<!--<a id="section_E4F9DC28A2944BD08B4190A7F98A8365"></a>-->

Wanneer TVSDK de `MediaPlayerItem` instantie voor de huidige video maakt, wordt voor elke beschikbare audiotrack een `AudioTrack` item gemaakt. Het item bevat een `name` eigenschap, een tekenreeks die doorgaans een door de gebruiker herkenbare beschrijving bevat van de taal van die track. Het item bevat ook informatie over of die track standaard moet worden gebruikt.

Wanneer het tijd is om de video af te spelen, kunt u om een lijst van beschikbare audiosporen vragen, naar keuze de gebruiker laten kiezen, en de video plaatsen om met het geselecteerde spoor te spelen.

Hoewel het zeldzaam is dat als er een extra audiotrack beschikbaar komt nadat deze de `MediaPlayerItem`gebeurtenis heeft gemaakt, TVSDK een `MediaPlayerItem.AUDIO_UPDATED` gebeurtenis start.

## Toegevoegde API&#39;s {#section_87C42C30BA8C4F58A2DAB7CE07FCD3DE}

De volgende API&#39;s zijn toegevoegd ter ondersteuning van alternatieve audio:

`hasAlternateAudio`

Als de opgegeven media een andere audiotrack heeft dan de standaardtrack, wordt deze booleaanse functie geretourneerd `true`. Als er geen alternatieve audiotrack is, wordt de functie geretourneerd `false`.

```
bool MediaPlayerItemImpl::hasAlternateAudio() const { 
    return _hasAlternateAudio; 
}
```

** `getAudioTracks`**

Deze functie retourneert een lijst met alle huidige beschikbare audiotracks in een opgegeven media.

```
virtual PSDKErrorCode getAudioTracks(PSDKImmutableArray<AudioTrack>*& out) const { 
    if (_audioTracks) { 
        out = _audioTracks; 
        out->addRef(); 
        return kECSuccess; 
    } 
    return kECDataNotAvailable; 
} 
```

`getSelectedAudioTrack`

Deze functie die de momenteel geselecteerde alternatieve audiotrack en eigenschappen zoals taal retourneert. De automatische selectie van tracks kan ook worden geëxtraheerd.

```
PSDKErrorCode MediaPlayerItemImpl::getSelectedAudioTrack(AudioTrack &out) const { 
    out = _currentAudioTrack; 
    return kECSuccess; 
}
```

`selectAudioTrack`

Deze functie selecteert een alternatieve audiotrack die moet worden afgespeeld.

```
PSDKErrorCode MediaPlayerItemImpl::selectAudioTrack(const AudioTrack &audioTrack) { 
    _lastPlayedAudioTrack = _currentAudioTrack; 
    if(_mediaPlayer && _mediaPlayer->_trickPlay) 
        return kECUnsupportedOperation; 
    _currentAudioTrack = audioTrack; 
    PSDKErrorCode result = kECSuccess; 
    if (_currentAudioTrack) { 
        media::TimeLine* timeline = NULL; 
        if (_mediaPlayer->_fragHttpStreamer) 
            _mediaPlayer->_fragHttpStreamer->GetTimeLine(&timeline); 
        if (timeline) { 
            for (int32_t i = timeline->GetFirstPeriodIndex(); i <= timeline->GetLastPeriodIndex(); i++){ 
                media::ErrorCode error = selectTrack(timeline,_mediaPlayer->_fragHttpStreamer, i, audioTrack.getName(), media::kSTTAudioIndex); 
                return _mediaPlayer->convertToPSDKError(error); 
            } 
        } 
    }   
    return result; 
}
```

