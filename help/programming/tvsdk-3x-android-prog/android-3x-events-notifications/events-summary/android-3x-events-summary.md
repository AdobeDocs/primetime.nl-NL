---
description: Uw toepassing kan de activiteit in uw speler en de veranderende status van de speler controleren door naar de gebeurtenissen te luisteren die door TVSDK worden verzonden.
title: Overzicht van gebeurtenissen in de primaire speler
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 0%

---


# Overzicht van gebeurtenissen in primetime-speler {#primetime-player-events-summary}

Uw toepassing kan de activiteit in uw speler en de veranderende status van de speler controleren door naar de gebeurtenissen te luisteren die door TVSDK worden verzonden.

## Gebeurtenissen {#events}

TVSDK brengt u op de hoogte wanneer gebeurtenissen plaatsvinden waarop uw toepassing moet reageren. Elke gebeurtenis komt overeen met een listenerklasse, met een callback-methode die u moet implementeren.

>[!TIP]
>
>De gebeurteniscodes zijn de constanten van de `MediaPlayerEvent`-opsomming.

`AdBreakCompletedEventListener`

* **** BetekenisHet afspelen van het advertentieeinde is voltooid.

* **Callback om uit te voeren** `onAdBreakCompleted(AdBreakPlaybackEvent event)`

* **Gebeurteniscode** `AD_BREAK_COMPLETE`

`AdBreakSkippedEventListener`

* **** Betekenis: een advertentie-einde is overgeslagen tijdens het afspelen.

* **Callback om uit te voeren** `onAdBreakSkipped(AdBreakPlaybackEvent event)`

* **Gebeurteniscode** `AD_BREAK_SKIPPED`

`AdBreakStartedEventListener`

* **** BetekenisHet afspelen van een advertentie-einde is begonnen.

* **Callback om uit te voeren** `onAdBreakStarted(AdBreakPlaybackEvent event)`

* **Gebeurteniscode** `AD_BREAK_START`

`AdClickedEventListener`

* **** BetekenisEr is op een advertentie geklikt tijdens het afspelen.

* **Callback om uit te voeren** `onAdClicked(AdClickEvent event)`
* **Gebeurteniscode** `AD_CLICK`

`AdCompletedEventListener`

* **** BetekenisHet afspelen van de advertentie is voltooid.

* **Callback om uit te voeren** `onAdCompleted(AdPlaybackEvent event)`

* **Gebeurteniscode** `AD_COMPLETE`

`AdProgressEventListener`

* **Voortgang** BetekenisRapportage tijdens playback.

* **Callback om uit te voeren** `onAdProgress(AdPlaybackEvent event)`

* **Gebeurteniscode** `AD_PROGRESS`

`AdResolutionCompleteEventListener`

* **** Betekenis: Primetime en besluitvorming en resolutie zijn voltooid. Deze gebeurtenis is alleen van toepassing op VOD-inhoud.

* **Callback om uit te voeren** `onAdResolutionComplete()`

* **Gebeurteniscode** `AD_RESOLUTION_COMPLETE`

`AdStartedEventListener`{#section_A4339C48F82640A8AF4AF09CB3B33188}

* **** Betekenis: het afspelen van de advertentie is begonnen.

* **Callback om uit te voeren** `onAdStarted(AdPlaybackEvent event)`

* **Gebeurteniscode** `AD_START`

`AudioUpdatedEventListener`

* **** BetekenisEr is een nieuwe audiotrack gedetecteerd.

* **Callback om uit te voeren** `onAudioUpdated(MediaPlayerItemEvent event)`

* **Gebeurteniscode** `AUDIO_TRACK_UPDATED`

`BufferingBeginEventListener`

* **** Betekenis: de speler is begonnen te bufferen.

* **Callback om uit te voeren** `onBufferingBegin(BufferEvent event)`

* **Gebeurteniscode** `BUFFERING_BEGIN`

`BufferingEndEventListener`

* **** BetekenisDe speler heeft het bufferen gestopt.

* **Callback om uit te voeren** `onBufferingEnd(BufferEvent event)`

* **Gebeurteniscode** `BUFFERING_END`

&quot;BufferPreparedEventListener&quot;

* **** BetekenisDe buffer wordt voorbereid.

* **Callback om uit te voeren** `onBufferPrepared()`

* **Gebeurteniscode** `BUFFER_PREPARED`

`CaptionsUpdatedEventListener`

* **** Betekenis Een nieuw bijschriftspoor is gedetecteerd.

* **Callback om uit te voeren** `onCaptionsUpdated(MediaPlayerItemEvent event)`

* **Gebeurteniscode** `CAPTIONS_UPDATED`

`DRMMetadataInfoEventListener`

* **** BetekenisEr zijn nieuwe DRM-metagegevens gedetecteerd in de mediastream.

* **Callback om uit te voeren** `onDRMMetadataInfo(DRMMetadataInfoEvent event)`

* **Gebeurteniscode** `DRM_METADATA`

`ItemCreatedEventListener`

* **** Betekenis: er is een nieuw mediaspeler-item gemaakt.

* **Callback om uit te voeren** `onItemCreated(MediaPlayerItemEvent event)`

* **Gebeurteniscode** `ITEM_CREATED`

`ItemLoadCompleteEventListener`

* **** BetekenisNieuwe ladingsinformatie is gecreeerd voor het huidige punt.

* **Callback om uit te voeren** `onLoadComplete(MediaPlayerItemEvent event)`

* **Gebeurteniscode** `ITEM_UPDATED`

`LoadInformationEventListener`

* **** BetekenisEen nieuw segment is geladen.

* **Callback om uit te voeren** `onLoadInformation(LoadInformationEvent event)`

* **Gebeurteniscode** `LOAD_INFORMATION_AVAILABLE`

`MainManifestUpdatedEventListener`

* **** BetekenisHet belangrijkste manifest of playlist is bijgewerkt.

* **Callback om uit te voeren** `onMainManifestUpdated(MediaPlayerItemEvent event)`

* **Gebeurteniscode** `MANIFEST_UPDATED`

`NotificationEventListener`

* **** BetekenisDe bewerking is mislukt.

* **Callback om uit te voeren** `onNotification(NotificationEvent event)`

* **Gebeurteniscode** `OPERATION_FAILED`

`PlaybackRangeUpdatedEventListener`

* **** BetekenisHet afspeelbereik is bijgewerkt.

* **Callback om uit te voeren** `onPlaybackRangeUpdated(MediaPlayerItemEvent event)`

* **Gebeurteniscode** `PLAYBACK_RANGE_UPDATED`

`PlaybackRatePlayingEventListener`

* **** Betekenis: er is een nieuwe afspeelsnelheid zichtbaar op het scherm.

* **Callback om uit te voeren** `onRatePlaying(PlaybackRateEvent event)`

* **Gebeurteniscode** `RATE_PLAYING`

`PlaybackRateSelectedEventListener`

* **** BetekenisHet de tariefattribuut van MediaPlayer is geplaatst.

* **Callback om uit te voeren** `onRateSelected(PlaybackRateEvent event)`

* **Gebeurteniscode** `RATE_SELECTED`

`PlayStartEventListener`

* **** Betekenis: het afspelen is gestart.

* **Callback om uit te voeren** `onPlayStart()`

* **Gebeurteniscode** `PLAY_START`

`ProfileChangeEventListener`

* **** Betekenis: het huidige profiel van MediaPlayer is gewijzigd.

* **Callback om uit te voeren** `onProfileChanged(ProfileEvent event)`

* **Gebeurteniscode** `PROFILE_CHANGED`

`ReservationReachedEventListener`

* **** Betekenis afspelen heeft een tijdlijnreservering bereikt.

* **Callback om uit te voeren** `onReservationReached(ReservationEvent event)`

* **Gebeurteniscode** `RESERVATION_REACHED`

`SeekBeginEventListener`

* **De** BetekenisSeek-bewerking is gestart.

* **Callback om uit te voeren** `onSeekBegin(SeekEvent event)`

* **Gebeurteniscode** `SEEK_BEGIN`

`SeekEndEventListener`

* **** BetekenisDe zoekbewerking is voltooid.

* **Callback om uit te voeren** `onSeekEnd(SeekEvent event)`

* **Gebeurteniscode** `SEEK_END`

`SeekPositionAdjustedEventListener`

* **** BetekenisDe zoekpositie is aangepast vanwege interne afspeelregels of externe bedrijfsregels.

* **Callback om uit te voeren** `onPositionAdjusted(SeekEvent event)`

* **Gebeurteniscode** `SEEK_POSITION_ADJUSTED`

`SizeAvailableEventListener`

* **** BetekenisDe grootte van de media is beschikbaar.

* **Callback om uit te voeren** `onSizeAvailable(SizeAvailableEvent event)`

* **Gebeurteniscode** `SIZE_AVAILABLE`

`StatusChangeEventListener`

* **** Betekenis: de status MediaPlayer is gewijzigd.

* **Callback om uit te voeren** `onStatusChanged(MediaPlayerStatusChangeEvent event)`

* **Gebeurteniscode** `STATUS_CHANGED`

`TimeChangeEventListener`

* **** BetekenisDe afspeelkop is gewijzigd.

* **Callback om uit te voeren** `onTimeChanged(TimeChangeEvent event)`

* **Gebeurteniscode** `TIME_CHANGED`

`TimedEventEventListener`

* **** BetekenisDe verrichting is volledig met de tijd die voor de verrichting wordt genomen.

* **Callback om uit te voeren** `onTimedEvent(TimedEventEvent event)`

* **Gebeurteniscode** `TIMED_EVENT`

`TimelineMetadataAddedInBackgroundEventListener`

* **** Betekenis: er zijn nieuwe metagegevens met tijdslimiet toegevoegd aan een item op de achtergrond.

* **Callback om uit te voeren** `onTimedMetadata(TimedMetadataEvent event)`

* **Gebeurteniscode** `TIMED_METADATA_ADDED_IN_BACKGROUND`

`TimedMetadataEventListener`

* **** Betekenis: er zijn nieuwe metagegevens met tijdslimiet gedetecteerd in de mediastream.

* **Callback om uit te voeren** `onTimedMetadata(TimedMetadataEvent event)`

* **Gebeurteniscode** `TIMED_METADATA_AVAILABLE`

`TimelineUpdatedEventListener`

* **** BetekenisDe tijdlijn is gewijzigd. Mogelijk zijn advertenties toegevoegd aan of verwijderd uit de tijdlijn.

* **Callback om uit te voeren** `onTimelineUpdated(TimelineEvent event)`

* **Gebeurteniscode** `TIMELINE_UPDATED`