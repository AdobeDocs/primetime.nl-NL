---
description: Met alternatieve audio kunt u schakelen tussen beschikbare audiotracks voor een videotrack. Gebruikers kunnen hun voorkeurstaal selecteren wanneer de video wordt afgespeeld.
title: Alternatieve audio
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Overzicht {#alternate-audio-overview}

Met alternatieve audio kunt u schakelen tussen beschikbare audiotracks voor een videotrack. Gebruikers kunnen hun voorkeurstaal selecteren wanneer de video wordt afgespeeld.

<!--<a id="section_E4F9DC28A2944BD08B4190A7F98A8365"></a>-->

Als TVSDK de opdracht `MediaPlayerItem` instantie voor de huidige video, wordt een `AudioTrack` item voor elke beschikbare audiotrack. Het item bevat een `name` eigenschap, die een tekenreeks is die doorgaans een door de gebruiker herkenbare beschrijving van de taal van die track bevat. Het item bevat ook informatie over of die track standaard moet worden gebruikt. Wanneer het tijd is om de video af te spelen, kunt u om een lijst van beschikbare audiosporen vragen, naar keuze toestaan de gebruiker selecteert een spoor, en de video plaatsen om met het geselecteerde spoor te spelen.

>[!TIP]
>
>Als er na TVSDK een extra audiotrack beschikbaar komt, wordt de optie `MediaPlayerItem`, wordt TVSDK geactiveerd `MediaPlayerItem.AUDIO_TRACK_UPDATED` gebeurtenis.

## Toegevoegde API&#39;s {#section_87C42C30BA8C4F58A2DAB7CE07FCD3DE}

De volgende API&#39;s zijn toegevoegd ter ondersteuning van alternatieve audio:

**`hasAlternateAudio`**

Als de opgegeven media een andere audiotrack heeft dan de standaardtrack, wordt deze booleaanse functie geretourneerd `true`. Als er geen alternatieve audiotrack is, wordt de functie geretourneerd `false`.

```java
boolean hasAlternateAudio();
```

**`getAudioTracks`**

Deze functie retourneert een lijst met alle huidige beschikbare audiotracks in een opgegeven media.

```java
List<AudioTrack> getAudioTracks();
```

**`getSelectedAudioTrack`**

Deze functie die de momenteel geselecteerde alternatieve audiotrack en eigenschappen zoals taal retourneert. De automatische selectie van tracks kan ook worden geëxtraheerd.

```java
AudioTrack getSelectedAudioTrack();
```

**`selectAudioTrack`**

Deze functie selecteert een alternatieve audiotrack die moet worden afgespeeld.

```java
void selectAudioTrack(AudioTrack audioTrack);
```

Bijvoorbeeld:

```java
private void onPrepared() { 
    // Select the AA track in PREPARED State 
    boolean hasAlternateAudio = _mediaPlayer.getCurrentItem().hasAlternateAudio(); 
    if(hasAlternateAudio) { 
        AudioTrack selectedAudioTrack =  
          _mediaPlayer.getCurrentItem().getSelectedAudioTrack(); 
 
        if (selectedAudioTrack == null) {  
            // Selecting default audio track  
            // If index is 1 it will select alternate audio track  
            selectedAudioTrack = _mediaPlayer.getCurrentItem().getAudioTracks().get(0);  
        } 
    } 
    _mediaPlayer.getCurrentItem().selectAudioTrack(selectedAudioTrack); 
} 
```
