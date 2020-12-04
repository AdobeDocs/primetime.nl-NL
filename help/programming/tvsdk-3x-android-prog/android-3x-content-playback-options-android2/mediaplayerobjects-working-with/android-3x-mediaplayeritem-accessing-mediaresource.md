---
description: Met de methoden in de MediaPlayerItem-klasse kunt u informatie ophalen over de inhoudsstroom die wordt vertegenwoordigd door een geladen MediaResource.
seo-description: Met de methoden in de MediaPlayerItem-klasse kunt u informatie ophalen over de inhoudsstroom die wordt vertegenwoordigd door een geladen MediaResource.
seo-title: Methoden van MediaPlayerItem voor toegang tot MediaResource-informatie
title: Methoden van MediaPlayerItem voor toegang tot MediaResource-informatie
uuid: 46845583-0a76-4411-a8bc-0a16ebfe8e6e
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---


# Methoden van MediaPlayerItem voor de toegang tot MediaResource-informatie {#mediaplayeritem-methods-for-accessing-mediaresource-information}

Met de methoden in de MediaPlayerItem-klasse kunt u informatie ophalen over de inhoudsstroom die wordt vertegenwoordigd door een geladen MediaResource.

| Methode | Beschrijving |
|--- |--- |
| **Labels toevoegen** |  |
| List`<String>` getAdTags() | Bevat de lijst met advertentietags die worden gebruikt voor het plaatsingsproces. |
| **Live stream** |  |
| boolean isLive(); | True if the stream is live; false als het om VOD gaat. |
| **DRM beveiligd** |  |
| boolean isProtected(); | True if the stream is protected DRM. |
| List`<DRMMetadataInfo>` getDRMMetadataInfos(); | Hiermee worden alle DRM-metagegevensobjecten weergegeven die in het manifest zijn aangetroffen. |
| **Ondertiteling** |  |
| boolean hasClosedCaptions(); | True if closed-caption tracks are available. |
| List`<ClosedCaptionsTrack>` getClosedCationsTracks(); | Bevat een lijst met beschikbare Closed Caption-tracks. |
| ClosedCaptionsTrack get SelectedClosedCaptionsTrack(); | Hiermee wordt de huidige gesloten bijschrifttrack opgehaald die is geselecteerd met SelectClosedCaptionsTrack. |
| selectClosedCaptionsTrack ( ClosedCaptionsTrack closedCaptionsTrack) | Hiermee stelt u een Closed Caption-track in als de huidige Closed Caption-track. |
| **Alternatieve audiotracks** |  |
| boolean hasAlternateAudio(); | True als de stream alternatieve audiotracks heeft. Opmerking:  De hoofdaudiotrack (standaard) maakt ook deel uit van de lijst met alternatieve audiotracks.  TVSDK voor Android beschouwt de hoofdaudiotrack als een van de items in de alternatieve audiotracklijst. Daarom is het enige geval waarin MediaPlayerItem.hasAlternateAudio false retourneert, wanneer de stream helemaal geen audio heeft. Als de inhoud slechts één audiospoor heeft, keert deze methode waar terug, en `MediaPlayerItem.getAudioTracks` keert een lijst met één enkel element (het gebrek audiospoor) terug. |
| List`<AudioTrack>` getAudioTracks(); | Geeft een lijst met beschikbare alternatieve audiotracks. |
| AudioTrack getSelectedAudioTrack(); | Hiermee wordt de audiotrack opgehaald die is geselecteerd met selectAudioTrack. |
| selectAudioTrack ( AudioTrack AudioTrack ) | Hiermee selecteert u een audiotrack als huidige audiotrack. |
| **Timed metadata** |  |
| boolean hasTimedMetadata(); | True if the stream has associated timed metadata. |
| List`<TimedMetadata>` getTimedMetadata(); | Bevat een lijst met de metagegevensobjecten met tijdslimiet die aan de stream zijn gekoppeld. |
| **Meerdere profielen (bitsnelheden)** |
| boolean isDynamic(); | True if the stream is a multiple bit rate (MBR) stream. |
| List`<Profile>` getProfiles(); | Verstrekt een lijst van de bijbehorende profielen van het beetjetarief. Voor elk profiel kunt u de bitsnelheid en de hoogte en breedte van het profiel ophalen. |
| Profiel getSelectedProfile() | Hiermee wordt het geselecteerde profiel opgehaald. |
| **Steen spelen** |  |
| boolean isTrickPlaySupported(); | True if the player supports fast forward, rewind, and resume. |
| List`< Float>` getAvailablePlaybackRates() | Verstrekt de lijst van beschikbare playbacktarieven in de context van de truc-speleigenschap. |
| Float getSelectedPlaybackRate() | Hiermee wordt de momenteel geselecteerde afspeelsnelheid opgehaald. |
| MediaPlayerItemConfig getConfig() | Retourneert de instantie MediaPlayerItemConfig die aan dit item is gekoppeld. |
| **Mediabron** |  |
| MediaResource getResource(); | Retourneert de mediabron die aan dit item is gekoppeld. |
| int getResourceId() | Retourneert de media-id die aan dit item is gekoppeld. Deze id wordt ingesteld wanneer het item wordt geladen met MediaPlayerItemLoader.load. |