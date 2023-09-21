---
description: Uw toepassing kan de activiteit in uw speler en de veranderende status van de speler controleren door naar de gebeurtenissen te luisteren die door TVSDK worden verzonden.
title: Overzicht van gebeurtenissen in de primetime-speler
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 0%

---

# Overzicht van gebeurtenissen in de primetime-speler {#primetime-player-events-summary}

Uw toepassing kan de activiteit in uw speler en de veranderende status van de speler controleren door naar de gebeurtenissen te luisteren die door TVSDK worden verzonden.

## Gebeurtenissen {#events}

TVSDK brengt u op de hoogte wanneer gebeurtenissen plaatsvinden waarop uw toepassing moet reageren. Elke gebeurtenis komt overeen met een listenerklasse, met een callback-methode die u moet implementeren.

>[!TIP]
>
>De gebeurteniscodes zijn de constanten van de `MediaPlayerEvent` enum.

`AdBreakCompletedEventListener`

* **Betekenis** Het afspelen van het advertentieeinde is voltooid.

* **Callback om uit te voeren** `onAdBreakCompleted(AdBreakPlaybackEvent event)`

* **Gebeurteniscode** `AD_BREAK_COMPLETE`

`AdBreakSkippedEventListener`

* **Betekenis** Een advertentie-einde is overgeslagen tijdens het afspelen.

* **Callback om uit te voeren** `onAdBreakSkipped(AdBreakPlaybackEvent event)`

* **Gebeurteniscode** `AD_BREAK_SKIPPED`

`AdBreakStartedEventListener`

* **Betekenis** Het afspelen van een advertentieeinde is gestart.

* **Callback om uit te voeren** `onAdBreakStarted(AdBreakPlaybackEvent event)`

* **Gebeurteniscode** `AD_BREAK_START`

`AdClickedEventListener`

* **Betekenis** Er is tijdens het afspelen op een advertentie geklikt.

* **Callback om uit te voeren** `onAdClicked(AdClickEvent event)`
* **Gebeurteniscode** `AD_CLICK`

`AdCompletedEventListener`

* **Betekenis** Het afspelen van de advertentie is voltooid.

* **Callback om uit te voeren** `onAdCompleted(AdPlaybackEvent event)`

* **Gebeurteniscode** `AD_COMPLETE`

`AdProgressEventListener`

* **Betekenis** Voortgang rapporteren tijdens afspelen.

* **Callback om uit te voeren** `onAdProgress(AdPlaybackEvent event)`

* **Gebeurteniscode** `AD_PROGRESS`

`AdResolutionCompleteEventListener`

* **Betekenis** Primetime en besluitvorming en resolutie zijn voltooid. Deze gebeurtenis is alleen van toepassing op VOD-inhoud.

* **Callback om uit te voeren** `onAdResolutionComplete()`

* **Gebeurteniscode** `AD_RESOLUTION_COMPLETE`

`AdStartedEventListener`{#section_A4339C48F82640A8AF4AF09CB3B33188}

* **Betekenis** Het afspelen van de advertentie is gestart.

* **Callback om uit te voeren** `onAdStarted(AdPlaybackEvent event)`

* **Gebeurteniscode** `AD_START`

`AudioUpdatedEventListener`

* **Betekenis** Er is een nieuwe audiotrack gevonden.

* **Callback om uit te voeren** `onAudioUpdated(MediaPlayerItemEvent event)`

* **Gebeurteniscode** `AUDIO_TRACK_UPDATED`

`BufferingBeginEventListener`

* **Betekenis** De speler is begonnen met bufferen.

* **Callback om uit te voeren** `onBufferingBegin(BufferEvent event)`

* **Gebeurteniscode** `BUFFERING_BEGIN`

`BufferingEndEventListener`

* **Betekenis** De speler heeft het bufferen gestopt.

* **Callback om uit te voeren** `onBufferingEnd(BufferEvent event)`

* **Gebeurteniscode** `BUFFERING_END`

`BufferPreparedEventListener`

* **Betekenis** De buffer wordt voorbereid.

* **Callback om uit te voeren** `onBufferPrepared()`

* **Gebeurteniscode** `BUFFER_PREPARED`

`CaptionsUpdatedEventListener`

* **Betekenis** Er is een nieuwe bijschrifttrack gedetecteerd.

* **Callback om uit te voeren** `onCaptionsUpdated(MediaPlayerItemEvent event)`

* **Gebeurteniscode** `CAPTIONS_UPDATED`

`DRMMetadataInfoEventListener`

* **Betekenis** Er zijn nieuwe DRM-metagegevens gedetecteerd in de mediastream.

* **Callback om uit te voeren** `onDRMMetadataInfo(DRMMetadataInfoEvent event)`

* **Gebeurteniscode** `DRM_METADATA`

`ItemCreatedEventListener`

* **Betekenis** Er is een nieuw mediaspelitem gemaakt.

* **Callback om uit te voeren** `onItemCreated(MediaPlayerItemEvent event)`

* **Gebeurteniscode** `ITEM_CREATED`

`ItemLoadCompleteEventListener`

* **Betekenis** Er zijn nieuwe laadgegevens gemaakt voor het huidige item.

* **Callback om uit te voeren** `onLoadComplete(MediaPlayerItemEvent event)`

* **Gebeurteniscode** `ITEM_UPDATED`

`LoadInformationEventListener`

* **Betekenis** Er is een nieuw segment geladen.

* **Callback om uit te voeren** `onLoadInformation(LoadInformationEvent event)`

* **Gebeurteniscode** `LOAD_INFORMATION_AVAILABLE`

`MainManifestUpdatedEventListener`

* **Betekenis** Het hoofdmanifest of de afspeellijst is bijgewerkt.

* **Callback om uit te voeren** `onMainManifestUpdated(MediaPlayerItemEvent event)`

* **Gebeurteniscode** `MANIFEST_UPDATED`

`NotificationEventListener`

* **Betekenis** De bewerking is mislukt.

* **Callback om uit te voeren** `onNotification(NotificationEvent event)`

* **Gebeurteniscode** `OPERATION_FAILED`

`PlaybackRangeUpdatedEventListener`

* **Betekenis** Het afspeelbereik is bijgewerkt.

* **Callback om uit te voeren** `onPlaybackRangeUpdated(MediaPlayerItemEvent event)`

* **Gebeurteniscode** `PLAYBACK_RANGE_UPDATED`

`PlaybackRatePlayingEventListener`

* **Betekenis** Er wordt een nieuwe afspeelsnelheid weergegeven op het scherm.

* **Callback om uit te voeren** `onRatePlaying(PlaybackRateEvent event)`

* **Gebeurteniscode** `RATE_PLAYING`

`PlaybackRateSelectedEventListener`

* **Betekenis** Het kenmerk rate van MediaPlayer is ingesteld.

* **Callback om uit te voeren** `onRateSelected(PlaybackRateEvent event)`

* **Gebeurteniscode** `RATE_SELECTED`

`PlayStartEventListener`

* **Betekenis** Het afspelen is gestart.

* **Callback om uit te voeren** `onPlayStart()`

* **Gebeurteniscode** `PLAY_START`

`ProfileChangeEventListener`

* **Betekenis** Het huidige profiel van MediaPlayer is gewijzigd.

* **Callback om uit te voeren** `onProfileChanged(ProfileEvent event)`

* **Gebeurteniscode** `PROFILE_CHANGED`

`ReservationReachedEventListener`

* **Betekenis** Bij het afspelen is een tijdlijnreservering bereikt.

* **Callback om uit te voeren** `onReservationReached(ReservationEvent event)`

* **Gebeurteniscode** `RESERVATION_REACHED`

`SeekBeginEventListener`

* **Betekenis** De zoekbewerking is gestart.

* **Callback om uit te voeren** `onSeekBegin(SeekEvent event)`

* **Gebeurteniscode** `SEEK_BEGIN`

`SeekEndEventListener`

* **Betekenis** De zoekbewerking is voltooid.

* **Callback om uit te voeren** `onSeekEnd(SeekEvent event)`

* **Gebeurteniscode** `SEEK_END`

`SeekPositionAdjustedEventListener`

* **Betekenis** De zoekpositie is aangepast vanwege interne afspeelregels of externe bedrijfsregels.

* **Callback om uit te voeren** `onPositionAdjusted(SeekEvent event)`

* **Gebeurteniscode** `SEEK_POSITION_ADJUSTED`

`SizeAvailableEventListener`

* **Betekenis** De grootte van de media is beschikbaar.

* **Callback om uit te voeren** `onSizeAvailable(SizeAvailableEvent event)`

* **Gebeurteniscode** `SIZE_AVAILABLE`

`StatusChangeEventListener`

* **Betekenis** De status MediaPlayer is gewijzigd.

* **Callback om uit te voeren** `onStatusChanged(MediaPlayerStatusChangeEvent event)`

* **Gebeurteniscode** `STATUS_CHANGED`

`TimeChangeEventListener`

* **Betekenis** De afspeelkop is gewijzigd.

* **Callback om uit te voeren** `onTimeChanged(TimeChangeEvent event)`

* **Gebeurteniscode** `TIME_CHANGED`

`TimedEventEventListener`

* **Betekenis** De bewerking is voltooid met de tijd die nodig is voor de bewerking.

* **Callback om uit te voeren** `onTimedEvent(TimedEventEvent event)`

* **Gebeurteniscode** `TIMED_EVENT`

`TimelineMetadataAddedInBackgroundEventListener`

* **Betekenis** Er zijn nieuwe metagegevens met tijdslimiet toegevoegd aan een item op de achtergrond.

* **Callback om uit te voeren** `onTimedMetadata(TimedMetadataEvent event)`

* **Gebeurteniscode** `TIMED_METADATA_ADDED_IN_BACKGROUND`

`TimedMetadataEventListener`

* **Betekenis** Er zijn nieuwe metagegevens met tijdslimiet gedetecteerd in de mediastream.

* **Callback om uit te voeren** `onTimedMetadata(TimedMetadataEvent event)`

* **Gebeurteniscode** `TIMED_METADATA_AVAILABLE`

`TimelineUpdatedEventListener`

* **Betekenis** De tijdlijn is gewijzigd. Mogelijk zijn advertenties toegevoegd aan of verwijderd uit de tijdlijn.

* **Callback om uit te voeren** `onTimelineUpdated(TimelineEvent event)`

* **Gebeurteniscode** `TIMELINE_UPDATED`
