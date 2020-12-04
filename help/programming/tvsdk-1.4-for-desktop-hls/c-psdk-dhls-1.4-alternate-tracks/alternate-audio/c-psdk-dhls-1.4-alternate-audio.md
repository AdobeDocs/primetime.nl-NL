---
description: Met alternatief geluid (late binding) kunt u schakelen tussen beschikbare audiotracks voor een videotrack. Op deze manier kunnen gebruikers een taaltrack selecteren wanneer de video wordt afgespeeld.
seo-description: Met alternatief geluid (late binding) kunt u schakelen tussen beschikbare audiotracks voor een videotrack. Op deze manier kunnen gebruikers een taaltrack selecteren wanneer de video wordt afgespeeld.
seo-title: Alternatieve audio
title: Alternatieve audio
uuid: d7e61a2a-1985-4dba-9c6d-0e139ffde46a
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---


# Alternatieve audio{#alternate-audio}

Met alternatief geluid (late binding) kunt u schakelen tussen beschikbare audiotracks voor een videotrack. Op deze manier kunnen gebruikers een taaltrack selecteren wanneer de video wordt afgespeeld.

<!--<a id="section_E4F9DC28A2944BD08B4190A7F98A8365"></a>-->

Wanneer TVSDK de `MediaPlayerItem`-instantie voor de huidige video maakt, maakt deze een `AudioTrack`-item voor elke beschikbare audiotrack. Het punt bevat een `name` bezit, een koord dat typisch een user-herkenbare beschrijving van de taal van dat spoor bevat. Het item bevat ook informatie over of die track standaard moet worden gebruikt.

Wanneer het tijd is om de video af te spelen, kunt u om een lijst van beschikbare audiosporen vragen, naar keuze de gebruiker laten kiezen, en de video plaatsen om met het geselecteerde spoor te spelen.

Hoewel het zeldzaam is dat als een extra audiotrack beschikbaar wordt nadat `MediaPlayerItem` is gemaakt, door TVSDK een gebeurtenis `MediaPlayerItem.AUDIO_UPDATED` wordt geactiveerd.

## Toegevoegde API&#39;s {#section_87C42C30BA8C4F58A2DAB7CE07FCD3DE}

De volgende API&#39;s zijn toegevoegd ter ondersteuning van alternatieve audio:

`hasAlternateAudio`

Als de opgegeven media een andere audiotrack heeft dan de standaardtrack, retourneert deze booleaanse functie `true`. Als er geen alternatieve audiotrack is, retourneert de functie `false`.

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

