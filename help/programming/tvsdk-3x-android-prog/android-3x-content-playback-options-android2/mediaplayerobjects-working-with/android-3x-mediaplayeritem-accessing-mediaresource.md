---
description: Met de methoden in de MediaPlayerItem-klasse kunt u informatie ophalen over de inhoudsstroom die wordt vertegenwoordigd door een geladen MediaResource.
title: Methoden van MediaPlayerItem voor toegang tot MediaResource-informatie
exl-id: d6a547f3-0267-4a49-93a4-628b4879aef4
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# Methoden van MediaPlayerItem voor toegang tot MediaResource-informatie {#mediaplayeritem-methods-for-accessing-mediaresource-information}

Met de methoden in de MediaPlayerItem-klasse kunt u informatie ophalen over de inhoudsstroom die wordt vertegenwoordigd door een geladen MediaResource.

| Methode | Beschrijving |
|--- |--- |
| **Labels toevoegen** |  |
| Lijst`<String>` getAdTags() | Bevat de lijst met advertentietags die worden gebruikt voor het plaatsingsproces. |
| **Live stream** |  |
| boolean isLive(); | True if the stream is live; false als het om VOD gaat. |
| **DRM beveiligd** |  |
| boolean isProtected(); | True if the stream is protected DRM. |
| Lijst`<DRMMetadataInfo>` getDRMMetadataInfos(); | Hiermee worden alle DRM-metagegevensobjecten weergegeven die in het manifest zijn aangetroffen. |
| **Ondertiteling** |  |
| boolean hasClosedCaptions(); | True if closed-caption tracks are available. |
| Lijst`<ClosedCaptionsTrack>` getClosedCationsTracks(); | Bevat een lijst met beschikbare Closed Caption-tracks. |
| ClosedCaptionsTrack get SelectedClosedCaptionsTrack(); | Hiermee wordt de huidige gesloten bijschrifttrack opgehaald die is geselecteerd met SelectClosedCaptionsTrack. |
| selectClosedCaptionsTrack ( ClosedCaptionsTrack closedCaptionsTrack) | Hiermee stelt u een Closed Caption-track in als de huidige Closed Caption-track. |
| **Alternatieve audiotracks** |  |
| boolean hasAlternateAudio(); | True als de stream alternatieve audiotracks heeft. Opmerking: De hoofdaudiotrack (standaard) maakt ook deel uit van de lijst met alternatieve audiotracks.  TVSDK voor Android beschouwt de hoofdaudiotrack als een van de items in de alternatieve audiotracklijst. Daarom is het enige geval waarin MediaPlayerItem.hasAlternateAudio false retourneert, wanneer de stream helemaal geen audio heeft. Als de inhoud slechts één audiotrack heeft, retourneert deze methode true, en  `MediaPlayerItem.getAudioTracks`  Hiermee wordt een lijst met één element geretourneerd (de standaardaudiotrack). |
| Lijst`<AudioTrack>` getAudioTracks(); | Geeft een lijst met beschikbare alternatieve audiotracks. |
| AudioTrack getSelectedAudioTrack(); | Hiermee wordt de audiotrack opgehaald die is geselecteerd met selectAudioTrack. |
| selectAudioTrack ( AudioTrack AudioTrack ) | Hiermee selecteert u een audiotrack als huidige audiotrack. |
| **Timed metadata** |  |
| boolean hasTimedMetadata(); | True if the stream has associated timed metadata. |
| Lijst`<TimedMetadata>` getTimedMetadata(); | Bevat een lijst met de metagegevensobjecten met tijdslimiet die aan de stream zijn gekoppeld. |
| **Meerdere profielen (bitsnelheden)** |
| boolean isDynamic(); | True if the stream is a multiple bit rate (MBR) stream. |
| Lijst`<Profile>` getProfiles(); | Verstrekt een lijst van de bijbehorende profielen van het beetjetarief. Voor elk profiel kunt u de bitsnelheid en de hoogte en breedte van het profiel ophalen. |
| Profiel getSelectedProfile() | Hiermee wordt het geselecteerde profiel opgehaald. |
| **Steen spelen** |  |
| boolean isTrickPlaySupported(); | True if the player supports fast forward, rewind, and resume. |
| Lijst`< Float>` getAvailablePlaybackRates() | Verstrekt de lijst van beschikbare playbacktarieven in de context van de truc-speleigenschap. |
| Float getSelectedPlaybackRate() | Hiermee wordt de momenteel geselecteerde afspeelsnelheid opgehaald. |
| MediaPlayerItemConfig getConfig() | Retourneert de instantie MediaPlayerItemConfig die aan dit item is gekoppeld. |
| **Mediabron** |  |
| MediaResource getResource(); | Retourneert de mediabron die aan dit item is gekoppeld. |
| int getResourceId() | Retourneert de media-id die aan dit item is gekoppeld. Deze id wordt ingesteld wanneer het item wordt geladen met MediaPlayerItemLoader.load. |
