---
description: Uw toepassing kan de activiteit in uw speler en de veranderende status van de speler controleren door naar de gebeurtenissen te luisteren die door TVSDK worden verzonden.
seo-description: Uw toepassing kan de activiteit in uw speler en de veranderende status van de speler controleren door naar de gebeurtenissen te luisteren die door TVSDK worden verzonden.
seo-title: Overzicht van gebeurtenissen in de primetime-speler
title: Overzicht van gebeurtenissen in de primetime-speler
uuid: ed3be4c2-8df3-4d96-a30b-74c196262798
translation-type: tm+mt
source-git-commit: a33e1f290fcf78e6f131910f6037f4803f7be98d

---


# Overzicht van gebeurtenissen in de primetime-speler {#primetime-player-events-summary-overview}

Uw toepassing kan de activiteit in uw speler en de veranderende status van de speler controleren door naar de gebeurtenissen te luisteren die door TVSDK worden verzonden.

## Gebeurtenissen {#events}

TVSDK brengt u op de hoogte wanneer gebeurtenissen plaatsvinden waarop uw toepassing moet reageren. Elke gebeurtenis komt overeen met een listenerklasse, met een callback-methode die u moet implementeren.

>[!TIP]
>
>De gebeurteniscodes zijn de constanten van de `MediaPlayerEvent` opsomming.

## AdBreakCompletedEventListener {#section_D7A74A4EACA44E54806D040491B7D879}

* ** Betekenis ** Het afspelen van het advertentieeinde is voltooid.

* ** Callback om te implementeren ** `onAdBreakCompleted(AdBreakPlaybackEvent event)`

* ** Gebeurteniscode ** `AD_BREAK_COMPLETE`

## AdBreakSkippedEventListener {#section_7AE5442442484F45B521D3309691C59C}

* ** Betekenis ** Er is een advertentie-einde overgeslagen tijdens het afspelen.

* ** Callback om te implementeren ** `onAdBreakSkipped(AdBreakPlaybackEvent event)`

* ** Gebeurteniscode ** `AD_BREAK_SKIPPED`

## AdBreakStartedEventListener {#section_0D50327621164E3A9C8F3337AA20BDE7}

* ** Betekenis ** Het afspelen van een advertentie-einde is begonnen.

* ** Callback om te implementeren ** `onAdBreakStarted(AdBreakPlaybackEvent event)`

* ** Gebeurteniscode ** `AD_BREAK_START`

## AdClickedEventListener {#section_9A6FD39EEDE0460B94FD074B5C2FB9BE}

* ** Betekenis ** Er is op een advertentie geklikt tijdens het afspelen.

* ** Callback om te implementeren ** `onAdClicked(AdClickEvent event)`

* ** Gebeurteniscode ** `AD_CLICK`

## AdCompletedEventListener {#section_D45EA0B1825145259EAC50A3E6B24BFC}

* ** Betekenis ** Het afspelen van de advertentie is voltooid.

* ** Callback om te implementeren ** `onAdCompleted(AdPlaybackEvent event)`

* ** Gebeurteniscode ** `AD_COMPLETE`

## AdProgressEventListener {#section_C26ACC4B941942B0A24DB06585EF52AB}

* ** Betekenis ** De voortgang tijdens het afspelen rapporteren.

* ** Callback om te implementeren ** `onAdProgress(AdPlaybackEvent event)`

* ** Gebeurteniscode ** `AD_PROGRESS`

## AdResolutionCompleteEventListener {#section_E9D545408CBA448EA2A8606DA629FB0B}

* ** Betekenis ** Primetime en besluitvorming en resolutie zijn voltooid. Deze gebeurtenis is alleen van toepassing op VOD-inhoud.

* ** Callback om te implementeren ** `onAdResolutionComplete()`

* ** Gebeurteniscode ** `AD_RESOLUTION_COMPLETE`

## AdStartedEventListener {#section_A4339C48F82640A8AF4AF09CB3B33188}

* ** Betekenis ** Het afspelen van de advertentie is gestart.

* ** Callback om te implementeren ** `onAdStarted(AdPlaybackEvent event)`

* ** Gebeurteniscode ** `AD_START`

## AudioUpdatedEventListener {#section_06E1A9F683E1411081CFC6BD30C3B669}

* ** Betekenis ** Er is een nieuwe audiotrack gedetecteerd.

* ** Callback om te implementeren ** `onAudioUpdated(MediaPlayerItemEvent event)`

* ** Gebeurteniscode ** `AUDIO_TRACK_UPDATED`

## BufferingBeginEventListener {#section_F8378841149A4801867ADDC7C0A98C57}

* ** Betekenis ** De speler is begonnen als buffer op te treden.

* ** Callback om te implementeren ** `onBufferingBegin(BufferEvent event)`

* ** Gebeurteniscode ** `BUFFERING_BEGIN`

## BufferingEndEventListener {#section_9107E0ED59474F11A04E243C6B117E21}

* ** Betekenis ** De speler is gestopt met bufferen.

* ** Callback om te implementeren ** `onBufferingEnd(BufferEvent event)`

* ** Gebeurteniscode ** `BUFFERING_END`

## BufferPreparedEventListener {#section_F6BFDF525D8B41B7B6E0EFCCE3065811}

* ** Betekenis ** De buffer wordt voorbereid.

* ** Callback om te implementeren ** `onBufferPrepared()`

* ** Gebeurteniscode ** `BUFFER_PREPARED`

## CaptionsUpdatedEventListener {#section_048BB128ADB747519F02DEDDD1C88B86}

* ** Betekenis ** Er is een nieuw bijschriftspoor gedetecteerd.

* ** Callback om te implementeren ** `onCaptionsUpdated(MediaPlayerItemEvent event)`

* ** Gebeurteniscode ** `CAPTIONS_UPDATED`

## DRMMetadataInfoEventListener {#section_CB55064D305A40D5BBAD09A53D63DB95}

* ** Betekenis ** Er zijn nieuwe DRM-metagegevens gedetecteerd in de mediastream.

* ** Callback om te implementeren ** `onDRMMetadataInfo(DRMMetadataInfoEvent event)`

* ** Gebeurteniscode ** `DRM_METADATA`

## ItemCreatedEventListener {#section_32A3178664C841008370E8447C978AB2}

* ** Betekenis ** Er is een nieuw mediaspelitem gemaakt.

* ** Callback om te implementeren ** `onItemCreated(MediaPlayerItemEvent event)`

* ** Gebeurteniscode ** `ITEM_CREATED`

## ItemLoadCompleteEventListener {#section_E29A3D7D2666461599909BD8E8BA46A7}

* ** Betekenis ** Nieuwe ladingsinformatie is gecreeerd voor het huidige punt.

* ** Callback om te implementeren ** `onLoadComplete(MediaPlayerItemEvent event)`

* ** Gebeurteniscode ** `ITEM_UPDATED`

## LoadInformationEventListener {#section_A986AD83F68446B99EAC888F98B39148}

* ** Betekenis ** Een nieuw segment is geladen.

* ** Callback om te implementeren ** `onLoadInformation(LoadInformationEvent event)`

* ** Gebeurteniscode ** `LOAD_INFORMATION_AVAILABLE`

## MainManifestUpdatedEventListener {#section_73709D121CED48C1B38550135DA55548}

* ** Betekenis ** Hoofdmanifest of playlist is bijgewerkt.

* ** Callback om te implementeren ** `onMainManifestUpdated(MediaPlayerItemEvent event)`

* ** Gebeurteniscode ** `MANIFEST_UPDATED`

## NotificationEventListener {#section_E8F27B979D374B5D8EA184E23BC17E43}

* ** Betekenis ** De bewerking is mislukt.

* ** Callback om te implementeren ** `onNotification(NotificationEvent event)`

* ** Gebeurteniscode ** `OPERATION_FAILED`

## PlaybackRangeUpdatedEventListener {#section_9072862D7EB842AEA3094DAF911CDF7F}

* ** Betekenis ** Het afspeelbereik is bijgewerkt.

* ** Callback om te implementeren ** `onPlaybackRangeUpdated(MediaPlayerItemEvent event)`

* ** Gebeurteniscode ** `PLAYBACK_RANGE_UPDATED`

## PlaybackRatePlayEventListener {#section_548A489ABED44F89BDF29DB9EDD348C5}

* ** Betekenis ** Een nieuwe playbacksnelheid is zichtbaar op het scherm.

* ** Callback om te implementeren ** `onRatePlaying(PlaybackRateEvent event)`

* ** Gebeurteniscode ** `RATE_PLAYING`

## PlaybackRateSelectedEventListener {#section_B303BAAFA6D14C1599AD3D7D79D722DD}

* ** Betekenis ** Het kenmerk rate van MediaPlayer is ingesteld.

* ** Callback om te implementeren ** `onRateSelected(PlaybackRateEvent event)`

* ** Gebeurteniscode ** `RATE_SELECTED`

## PlayStartEventListener {#section_1D54CAE387B243679348A26E65B6A3FD}

* ** Betekenis ** Het afspelen is gestart.

* ** Callback om te implementeren ** `onPlayStart()`

* ** Gebeurteniscode ** `PLAY_START`

## ProfileChangeEventListener {#section_EEDF08916D1D40509E64EC180F143C9A}

* ** Betekenis ** Het huidige profiel van MediaPlayer is gewijzigd.

* ** Callback om te implementeren ** `onProfileChanged(ProfileEvent event)`

* ** Gebeurteniscode ** `PROFILE_CHANGED`

## ReservationReachedEventListener {#section_31677E931F154E7E86D725B2B046065C}

* ** Betekenis ** Het afspelen heeft een tijdlijnreservering bereikt.

* ** Callback om te implementeren ** `onReservationReached(ReservationEvent event)`

* ** Gebeurteniscode ** `RESERVATION_REACHED`

## SeekBeginEventListener {#section_749E02ED2B1647438F50224C85260A1D}

* ** Betekenis ** De zoekbewerking is gestart.

* ** Callback om te implementeren ** `onSeekBegin(SeekEvent event)`

* ** Gebeurteniscode ** `SEEK_BEGIN`

## SeekEndEventListener {#section_4F70BAD695AF4717B2254D9DBA1071E4}

* ** Betekenis ** De zoekbewerking is voltooid.

* ** Callback om te implementeren ** `onSeekEnd(SeekEvent event)`

* ** Gebeurteniscode ** `SEEK_END`

## SeekPositionAdjustedEventListener {#section_01F89B73DBB84BEBBA60D820BF5FAC9A}

* ** Betekenis ** De zoekpositie is aangepast vanwege interne afspeelregels of externe bedrijfsregels.

* ** Callback om te implementeren ** `onPositionAdjusted(SeekEvent event)`

* ** Gebeurteniscode ** `SEEK_POSITION_ADJUSTED`

## SizeAvailableEventListener {#section_90DF6565E59B44B19338A7B89D53BBBF}

* ** Betekenis ** De grootte van de media is beschikbaar.

* ** Callback om te implementeren ** `onSizeAvailable(SizeAvailableEvent event)`

* ** Gebeurteniscode ** `SIZE_AVAILABLE`

## StatusChangeEventListener {#section_310D2327089D46358F9CE03EA76F3287}

* ** Betekenis ** De staat MediaPlayer is veranderd.

* ** Callback om te implementeren ** `onStatusChanged(MediaPlayerStatusChangeEvent event)`

* ** Gebeurteniscode ** `STATUS_CHANGED`

## TimeChangeEventListener {#section_ED3855BD90124D97836B2D0957AD9E0C}

* ** Betekenis ** De afspeelkop is gewijzigd.

* ** Callback om te implementeren ** `onTimeChanged(TimeChangeEvent event)`

* ** Gebeurteniscode ** `TIME_CHANGED`

## TimedEventListener {#section_5E62C2C81C3B4F93B46E7518578456EA}

* ** Betekenis ** De bewerking is voltooid met de tijd die nodig is voor de bewerking.

* ** Callback om te implementeren ** `onTimedEvent(TimedEventEvent event)`

* ** Gebeurteniscode ** `TIMED_EVENT`

## TimelineMetadataAddedInBackgroundEventListener {#section_7B923C7116154CCFBAE1FCA92C928EB2}

* ** Betekenis ** Er zijn nieuwe metagegevens met tijdslimiet toegevoegd aan een item op de achtergrond.

* ** Callback om te implementeren ** `onTimedMetadata(TimedMetadataEvent event)`

* ** Gebeurteniscode ** `TIMED_METADATA_ADDED_IN_BACKGROUND`

## TimedMetadataEventListener {#section_9741EA321ACF403FB8E9AB311BAACDD7}

* ** Betekenis ** Er is een nieuwe metagegevens met tijdslimiet gedetecteerd in de mediastream.

* ** Callback om te implementeren ** `onTimedMetadata(TimedMetadataEvent event)`

* ** Gebeurteniscode ** `TIMED_METADATA_AVAILABLE`

## TimelineUpdatedEventListener {#section_D0755BD2AF3347C7861395706E31B861}

* ** Betekenis ** De tijdlijn is gewijzigd. Mogelijk zijn advertenties toegevoegd aan of verwijderd uit de tijdlijn.

* ** Callback om te implementeren ** `onTimelineUpdated(TimelineEvent event)`

* ** Gebeurteniscode ** `TIMELINE_UPDATED`