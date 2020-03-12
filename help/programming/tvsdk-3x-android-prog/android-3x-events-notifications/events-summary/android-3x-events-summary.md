---
description: Uw toepassing kan de activiteit in uw speler en de veranderende status van de speler controleren door naar de gebeurtenissen te luisteren die door TVSDK worden verzonden.
seo-description: Uw toepassing kan de activiteit in uw speler en de veranderende status van de speler controleren door naar de gebeurtenissen te luisteren die door TVSDK worden verzonden.
seo-title: Overzicht van gebeurtenissen in de primetime-speler
title: Overzicht van gebeurtenissen in de primetime-speler
uuid: b2ff74f2-c373-42da-a717-2f0550cbcb7f
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Overzicht van gebeurtenissen in de primetime-speler {#primetime-player-events-summary}

Uw toepassing kan de activiteit in uw speler en de veranderende status van de speler controleren door naar de gebeurtenissen te luisteren die door TVSDK worden verzonden.

## Gebeurtenissen {#events}

TVSDK brengt u op de hoogte wanneer gebeurtenissen plaatsvinden waarop uw toepassing moet reageren. Elke gebeurtenis komt overeen met een listenerklasse, met een callback-methode die u moet implementeren.

>[!TIP]
>
>De gebeurteniscodes zijn de constanten van de `MediaPlayerEvent` opsomming.

`AdBreakCompletedEventListener`

* **Dit betekent** dat het afspelen van het advertentieeinde is voltooid.

* **Callback om te implementeren**`onAdBreakCompleted(AdBreakPlaybackEvent event)`

* **Gebeurteniscode**`AD_BREAK_COMPLETE`

`AdBreakSkippedEventListener`

* **Dit betekent** dat een advertentie-einde is overgeslagen tijdens het afspelen.

* **Callback om te implementeren**`onAdBreakSkipped(AdBreakPlaybackEvent event)`

* **Gebeurteniscode**`AD_BREAK_SKIPPED`

`AdBreakStartedEventListener`

* **Dit betekent** dat het afspelen van een advertentie-einde is gestart.

* **Callback om te implementeren**`onAdBreakStarted(AdBreakPlaybackEvent event)`

* **Gebeurteniscode**`AD_BREAK_START`

`AdClickedEventListener`

* **Dit betekent dat** tijdens het afspelen op een advertentie is geklikt.

* **Callback om te implementeren**`onAdClicked(AdClickEvent event)`
* **Gebeurteniscode**`AD_CLICK`

`AdCompletedEventListener`

* **Dit betekent** dat het afspelen van de advertentie is voltooid.

* **Callback om te implementeren**`onAdCompleted(AdPlaybackEvent event)`

* **Gebeurteniscode**`AD_COMPLETE`

`AdProgressEventListener`

* **Betekenis** het Melden van vooruitgang tijdens playback.

* **Callback om te implementeren**`onAdProgress(AdPlaybackEvent event)`

* **Gebeurteniscode**`AD_PROGRESS`

`AdResolutionCompleteEventListener`

* **Dat betekent dat** Primetime en besluitvorming en resolutie compleet zijn. Deze gebeurtenis is alleen van toepassing op VOD-inhoud.

* **Callback om te implementeren**`onAdResolutionComplete()`

* **Gebeurteniscode**`AD_RESOLUTION_COMPLETE`

`AdStartedEventListener`{#section_A4339C48F82640A8AF4AF09CB3B33188}

* **Dit betekent** dat het afspelen van de advertentie is gestart.

* **Callback om te implementeren**`onAdStarted(AdPlaybackEvent event)`

* **Gebeurteniscode**`AD_START`

`AudioUpdatedEventListener`

* **Betekenis** Er is een nieuwe audiotrack gedetecteerd.

* **Callback om te implementeren**`onAudioUpdated(MediaPlayerItemEvent event)`

* **Gebeurteniscode**`AUDIO_TRACK_UPDATED`

`BufferingBeginEventListener`

* **Dit betekent** dat de speler begint te bufferen.

* **Callback om te implementeren**`onBufferingBegin(BufferEvent event)`

* **Gebeurteniscode**`BUFFERING_BEGIN`

`BufferingEndEventListener`

* **Dit betekent** dat de speler niet meer buffert.

* **Callback om te implementeren**`onBufferingEnd(BufferEvent event)`

* **Gebeurteniscode**`BUFFERING_END`

&quot;BufferPreparedEventListener&quot;

* **Betekenis** De buffer wordt voorbereid.

* **Callback om te implementeren**`onBufferPrepared()`

* **Gebeurteniscode**`BUFFER_PREPARED`

`CaptionsUpdatedEventListener`

* **Betekenis** Er is een nieuw bijschriftspoor gedetecteerd.

* **Callback om te implementeren**`onCaptionsUpdated(MediaPlayerItemEvent event)`

* **Gebeurteniscode**`CAPTIONS_UPDATED`

`DRMMetadataInfoEventListener`

* **Betekenis** Er zijn nieuwe DRM-metagegevens gedetecteerd in de mediastream.

* **Callback om te implementeren**`onDRMMetadataInfo(DRMMetadataInfoEvent event)`

* **Gebeurteniscode**`DRM_METADATA`

`ItemCreatedEventListener`

* **Betekenis** Er is een nieuw mediaspelitem gemaakt.

* **Callback om te implementeren**`onItemCreated(MediaPlayerItemEvent event)`

* **Gebeurteniscode**`ITEM_CREATED`

`ItemLoadCompleteEventListener`

* **Betekenis** de Nieuwe ladingsinformatie is gecreeerd voor het huidige punt.

* **Callback om te implementeren**`onLoadComplete(MediaPlayerItemEvent event)`

* **Gebeurteniscode**`ITEM_UPDATED`

`LoadInformationEventListener`

* **Betekenis** Een nieuw segment is geladen.

* **Callback om te implementeren**`onLoadInformation(LoadInformationEvent event)`

* **Gebeurteniscode**`LOAD_INFORMATION_AVAILABLE`

`MainManifestUpdatedEventListener`

* **Betekenis** belangrijkste manifest of playlist is bijgewerkt.

* **Callback om te implementeren**`onMainManifestUpdated(MediaPlayerItemEvent event)`

* **Gebeurteniscode**`MANIFEST_UPDATED`

`NotificationEventListener`

* **Betekenis** De bewerking is mislukt.

* **Callback om te implementeren**`onNotification(NotificationEvent event)`

* **Gebeurteniscode**`OPERATION_FAILED`

`PlaybackRangeUpdatedEventListener`

* **Dit betekent** dat het afspeelbereik is bijgewerkt.

* **Callback om te implementeren**`onPlaybackRangeUpdated(MediaPlayerItemEvent event)`

* **Gebeurteniscode**`PLAYBACK_RANGE_UPDATED`

`PlaybackRatePlayingEventListener`

* **Dit betekent** dat een nieuwe afspeelsnelheid zichtbaar is op het scherm.

* **Callback om te implementeren**`onRatePlaying(PlaybackRateEvent event)`

* **Gebeurteniscode**`RATE_PLAYING`

`PlaybackRateSelectedEventListener`

* **Betekenis** het de tariefattribuut van MediaPlayer is geplaatst.

* **Callback om te implementeren**`onRateSelected(PlaybackRateEvent event)`

* **Gebeurteniscode**`RATE_SELECTED`

`PlayStartEventListener`

* **Dit betekent** dat het afspelen is gestart.

* **Callback om te implementeren**`onPlayStart()`

* **Gebeurteniscode**`PLAY_START`

`ProfileChangeEventListener`

* **Dit betekent** dat het huidige profiel van MediaPlayer is gewijzigd.

* **Callback om te implementeren**`onProfileChanged(ProfileEvent event)`

* **Gebeurteniscode**`PROFILE_CHANGED`

`ReservationReachedEventListener`

* **Betekenis dat** het afspelen een tijdlijnreservering heeft bereikt.

* **Callback om te implementeren**`onReservationReached(ReservationEvent event)`

* **Gebeurteniscode**`RESERVATION_REACHED`

`SeekBeginEventListener`

* **Betekenis** dat de zoekopdracht is gestart.

* **Callback om te implementeren**`onSeekBegin(SeekEvent event)`

* **Gebeurteniscode**`SEEK_BEGIN`

`SeekEndEventListener`

* **Betekenis** De zoekbewerking is voltooid.

* **Callback om te implementeren**`onSeekEnd(SeekEvent event)`

* **Gebeurteniscode**`SEEK_END`

`SeekPositionAdjustedEventListener`

* **Betekenis** De zoekpositie is aangepast vanwege interne afspeelregels of externe bedrijfsregels.

* **Callback om te implementeren**`onPositionAdjusted(SeekEvent event)`

* **Gebeurteniscode**`SEEK_POSITION_ADJUSTED`

`SizeAvailableEventListener`

* **Betekenis** de grootte van de media is beschikbaar.

* **Callback om te implementeren**`onSizeAvailable(SizeAvailableEvent event)`

* **Gebeurteniscode**`SIZE_AVAILABLE`

`StatusChangeEventListener`

* **Betekenis** de staat MediaPlayer is veranderd.

* **Callback om te implementeren**`onStatusChanged(MediaPlayerStatusChangeEvent event)`

* **Gebeurteniscode**`STATUS_CHANGED`

`TimeChangeEventListener`

* **Betekenis** De afspeelkop is veranderd.

* **Callback om te implementeren**`onTimeChanged(TimeChangeEvent event)`

* **Gebeurteniscode**`TIME_CHANGED`

`TimedEventEventListener`

* **Betekenis** De bewerking is voltooid met de tijd die voor de bewerking is genomen.

* **Callback om te implementeren**`onTimedEvent(TimedEventEvent event)`

* **Gebeurteniscode**`TIMED_EVENT`

`TimelineMetadataAddedInBackgroundEventListener`

* **Betekenis** Er zijn nieuwe metagegevens met tijdslimiet toegevoegd aan een item op de achtergrond.

* **Callback om te implementeren**`onTimedMetadata(TimedMetadataEvent event)`

* **Gebeurteniscode**`TIMED_METADATA_ADDED_IN_BACKGROUND`

`TimedMetadataEventListener`

* **Betekenis** Er zijn nieuwe metagegevens met tijdslimiet gedetecteerd in de mediastream.

* **Callback om te implementeren**`onTimedMetadata(TimedMetadataEvent event)`

* **Gebeurteniscode**`TIMED_METADATA_AVAILABLE`

`TimelineUpdatedEventListener`

* **Betekenis** De tijdlijn is gewijzigd. Mogelijk zijn advertenties toegevoegd aan of verwijderd uit de tijdlijn.

* **Callback om te implementeren**`onTimelineUpdated(TimelineEvent event)`

* **Gebeurteniscode**`TIMELINE_UPDATED`