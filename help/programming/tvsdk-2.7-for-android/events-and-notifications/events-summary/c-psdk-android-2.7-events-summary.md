---
description: Uw toepassing kan de activiteit in uw speler en de veranderende status van de speler controleren door naar de gebeurtenissen te luisteren die door TVSDK worden verzonden.
title: Overzicht van gebeurtenissen in de primaire speler
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 0%

---


# Overzicht van gebeurtenissen in primetime-speler {#primetime-player-events-summary-overview}

Uw toepassing kan de activiteit in uw speler en de veranderende status van de speler controleren door naar de gebeurtenissen te luisteren die door TVSDK worden verzonden.

## Gebeurtenissen {#events}

TVSDK brengt u op de hoogte wanneer gebeurtenissen plaatsvinden waarop uw toepassing moet reageren. Elke gebeurtenis komt overeen met een listenerklasse, met een callback-methode die u moet implementeren.

>[!TIP]
>
>De gebeurteniscodes zijn de constanten van de `MediaPlayerEvent`-opsomming.

## AdBreakCompletedEventListener {#section_D7A74A4EACA44E54806D040491B7D879}

* ** Betekenis ** Het afspelen van het advertentieeinde is voltooid.

* ** Callback om ** `onAdBreakCompleted(AdBreakPlaybackEvent event)` uit te voeren

* ** Gebeurteniscode ** `AD_BREAK_COMPLETE`

## AdBreakSkippedEventListener {#section_7AE5442442484F45B521D3309691C59C}

* ** Betekenis ** Er is een advertentie-einde overgeslagen tijdens het afspelen.

* ** Callback om ** `onAdBreakSkipped(AdBreakPlaybackEvent event)` uit te voeren

* ** Gebeurteniscode ** `AD_BREAK_SKIPPED`

## AdBreakStartedEventListener {#section_0D50327621164E3A9C8F3337AA20BDE7}

* ** Betekenis ** Het afspelen van een advertentie-einde is begonnen.

* ** Callback om ** `onAdBreakStarted(AdBreakPlaybackEvent event)` uit te voeren

* ** Gebeurteniscode ** `AD_BREAK_START`

## AdClickedEventListener {#section_9A6FD39EEDE0460B94FD074B5C2FB9BE}

* ** Betekenis ** Er is op een advertentie geklikt tijdens het afspelen.

* ** Callback om ** `onAdClicked(AdClickEvent event)` uit te voeren

* ** Gebeurteniscode ** `AD_CLICK`

## AdCompletedEventListener {#section_D45EA0B1825145259EAC50A3E6B24BFC}

* ** Betekenis ** Het afspelen van de advertentie is voltooid.

* ** Callback om ** `onAdCompleted(AdPlaybackEvent event)` uit te voeren

* ** Gebeurteniscode ** `AD_COMPLETE`

## AdProgressEventListener {#section_C26ACC4B941942B0A24DB06585EF52AB}

* ** Betekenis ** De voortgang tijdens het afspelen rapporteren.

* ** Callback om ** `onAdProgress(AdPlaybackEvent event)` uit te voeren

* ** Gebeurteniscode ** `AD_PROGRESS`

## AdResolutionCompleteEventListener {#section_E9D545408CBA448EA2A8606DA629FB0B}

* ** Betekenis ** Primetime en besluitvorming en resolutie zijn voltooid. Deze gebeurtenis is alleen van toepassing op VOD-inhoud.

* ** Callback om ** `onAdResolutionComplete()` uit te voeren

* ** Gebeurteniscode ** `AD_RESOLUTION_COMPLETE`

## AdStartedEventListener {#section_A4339C48F82640A8AF4AF09CB3B33188}

* ** Betekenis ** Het afspelen van de advertentie is gestart.

* ** Callback om ** `onAdStarted(AdPlaybackEvent event)` uit te voeren

* ** Gebeurteniscode ** `AD_START`

## AudioUpdatedEventListener {#section_06E1A9F683E1411081CFC6BD30C3B669}

* ** Betekenis ** Er is een nieuwe audiotrack gedetecteerd.

* ** Callback om ** `onAudioUpdated(MediaPlayerItemEvent event)` uit te voeren

* ** Gebeurteniscode ** `AUDIO_TRACK_UPDATED`

## BufferingBeginEventListener {#section_F8378841149A4801867ADDC7C0A98C57}

* ** Betekenis ** De speler is begonnen als buffer op te treden.

* ** Callback om ** `onBufferingBegin(BufferEvent event)` uit te voeren

* ** Gebeurteniscode ** `BUFFERING_BEGIN`

## BufferingEndEventListener {#section_9107E0ED59474F11A04E243C6B117E21}

* ** Betekenis ** De speler is gestopt met bufferen.

* ** Callback om ** `onBufferingEnd(BufferEvent event)` uit te voeren

* ** Gebeurteniscode ** `BUFFERING_END`

## BufferPreparedEventListener {#section_F6BFDF525D8B41B7B6E0EFCCE3065811}

* ** Betekenis ** De buffer wordt voorbereid.

* ** Callback om ** `onBufferPrepared()` uit te voeren

* ** Gebeurteniscode ** `BUFFER_PREPARED`

## CaptionsUpdatedEventListener {#section_048BB128ADB747519F02DEDDD1C88B86}

* ** Betekenis ** Er is een nieuw bijschriftspoor gedetecteerd.

* ** Callback om ** `onCaptionsUpdated(MediaPlayerItemEvent event)` uit te voeren

* ** Gebeurteniscode ** `CAPTIONS_UPDATED`

## DRMMetadataInfoEventListener {#section_CB55064D305A40D5BBAD09A53D63DB95}

* ** Betekenis ** Er zijn nieuwe DRM-metagegevens gedetecteerd in de mediastream.

* ** Callback om ** `onDRMMetadataInfo(DRMMetadataInfoEvent event)` uit te voeren

* ** Gebeurteniscode ** `DRM_METADATA`

## ItemCreatedEventListener {#section_32A3178664C841008370E8447C978AB2}

* ** Betekenis ** Er is een nieuw mediaspelitem gemaakt.

* ** Callback om ** `onItemCreated(MediaPlayerItemEvent event)` uit te voeren

* ** Gebeurteniscode ** `ITEM_CREATED`

## ItemLoadCompleteEventListener {#section_E29A3D7D2666461599909BD8E8BA46A7}

* ** Betekenis ** Nieuwe ladingsinformatie is gecreeerd voor het huidige punt.

* ** Callback om ** `onLoadComplete(MediaPlayerItemEvent event)` uit te voeren

* ** Gebeurteniscode ** `ITEM_UPDATED`

## LoadInformationEventListener {#section_A986AD83F68446B99EAC888F98B39148}

* ** Betekenis ** Een nieuw segment is geladen.

* ** Callback om ** `onLoadInformation(LoadInformationEvent event)` uit te voeren

* ** Gebeurteniscode ** `LOAD_INFORMATION_AVAILABLE`

## MainManifestUpdatedEventListener {#section_73709D121CED48C1B38550135DA55548}

* ** Betekenis ** Hoofdmanifest of playlist is bijgewerkt.

* ** Callback om ** `onMainManifestUpdated(MediaPlayerItemEvent event)` uit te voeren

* ** Gebeurteniscode ** `MANIFEST_UPDATED`

## NotificationEventListener {#section_E8F27B979D374B5D8EA184E23BC17E43}

* ** Betekenis ** De bewerking is mislukt.

* ** Callback om ** `onNotification(NotificationEvent event)` uit te voeren

* ** Gebeurteniscode ** `OPERATION_FAILED`

## PlaybackRangeUpdatedEventListener {#section_9072862D7EB842AEA3094DAF911CDF7F}

* ** Betekenis ** Het afspeelbereik is bijgewerkt.

* ** Callback om ** `onPlaybackRangeUpdated(MediaPlayerItemEvent event)` uit te voeren

* ** Gebeurteniscode ** `PLAYBACK_RANGE_UPDATED`

## PlaybackRatePlayEventListener {#section_548A489ABED44F89BDF29DB9EDD348C5}

* ** Betekenis ** Een nieuwe playbacksnelheid is zichtbaar op het scherm.

* ** Callback om ** `onRatePlaying(PlaybackRateEvent event)` uit te voeren

* ** Gebeurteniscode ** `RATE_PLAYING`

## PlaybackRateSelectedEventListener {#section_B303BAAFA6D14C1599AD3D7D79D722DD}

* ** Betekenis ** Het kenmerk rate van MediaPlayer is ingesteld.

* ** Callback om ** `onRateSelected(PlaybackRateEvent event)` uit te voeren

* ** Gebeurteniscode ** `RATE_SELECTED`

## PlayStartEventListener {#section_1D54CAE387B243679348A26E65B6A3FD}

* ** Betekenis ** Het afspelen is gestart.

* ** Callback om ** `onPlayStart()` uit te voeren

* ** Gebeurteniscode ** `PLAY_START`

## ProfileChangeEventListener {#section_EEDF08916D1D40509E64EC180F143C9A}

* ** Betekenis ** Het huidige profiel van MediaPlayer is gewijzigd.

* ** Callback om ** `onProfileChanged(ProfileEvent event)` uit te voeren

* ** Gebeurteniscode ** `PROFILE_CHANGED`

## ReservationReachedEventListener {#section_31677E931F154E7E86D725B2B046065C}

* ** Betekenis ** Het afspelen heeft een tijdlijnreservering bereikt.

* ** Callback om ** `onReservationReached(ReservationEvent event)` uit te voeren

* ** Gebeurteniscode ** `RESERVATION_REACHED`

## SeekBeginEventListener {#section_749E02ED2B1647438F50224C85260A1D}

* ** Betekenis ** De zoekbewerking is gestart.

* ** Callback om ** `onSeekBegin(SeekEvent event)` uit te voeren

* ** Gebeurteniscode ** `SEEK_BEGIN`

## SeekEndEventListener {#section_4F70BAD695AF4717B2254D9DBA1071E4}

* ** Betekenis ** De zoekbewerking is voltooid.

* ** Callback om ** `onSeekEnd(SeekEvent event)` uit te voeren

* ** Gebeurteniscode ** `SEEK_END`

## SeekPositionAdjustedEventListener {#section_01F89B73DBB84BEBBA60D820BF5FAC9A}

* ** Betekenis ** De zoekpositie is aangepast vanwege interne afspeelregels of externe bedrijfsregels.

* ** Callback om ** `onPositionAdjusted(SeekEvent event)` uit te voeren

* ** Gebeurteniscode ** `SEEK_POSITION_ADJUSTED`

## SizeAvailableEventListener {#section_90DF6565E59B44B19338A7B89D53BBBF}

* ** Betekenis ** De grootte van de media is beschikbaar.

* ** Callback om ** `onSizeAvailable(SizeAvailableEvent event)` uit te voeren

* ** Gebeurteniscode ** `SIZE_AVAILABLE`

## StatusChangeEventListener {#section_310D2327089D46358F9CE03EA76F3287}

* ** Betekenis ** De status MediaPlayer is gewijzigd.

* ** Callback om ** `onStatusChanged(MediaPlayerStatusChangeEvent event)` uit te voeren

* ** Gebeurteniscode ** `STATUS_CHANGED`

## TimeChangeEventListener {#section_ED3855BD90124D97836B2D0957AD9E0C}

* ** Betekenis ** De afspeelkop is gewijzigd.

* ** Callback om ** `onTimeChanged(TimeChangeEvent event)` uit te voeren

* ** Gebeurteniscode ** `TIME_CHANGED`

## TimedEventListener {#section_5E62C2C81C3B4F93B46E7518578456EA}

* ** Betekenis ** De bewerking is voltooid met de tijd die nodig is voor de bewerking.

* ** Callback om ** `onTimedEvent(TimedEventEvent event)` uit te voeren

* ** Gebeurteniscode ** `TIMED_EVENT`

## TimelineMetadataAddedInBackgroundEventListener {#section_7B923C7116154CCFBAE1FCA92C928EB2}

* ** Betekenis ** Er zijn nieuwe metagegevens met tijdslimiet toegevoegd aan een item op de achtergrond.

* ** Callback om ** `onTimedMetadata(TimedMetadataEvent event)` uit te voeren

* ** Gebeurteniscode ** `TIMED_METADATA_ADDED_IN_BACKGROUND`

## TimedMetadataEventListener {#section_9741EA321ACF403FB8E9AB311BAACDD7}

* ** Betekenis ** Er is een nieuwe metagegevens met tijdslimiet gedetecteerd in de mediastream.

* ** Callback om ** `onTimedMetadata(TimedMetadataEvent event)` uit te voeren

* ** Gebeurteniscode ** `TIMED_METADATA_AVAILABLE`

## TimelineUpdatedEventListener {#section_D0755BD2AF3347C7861395706E31B861}

* ** Betekenis ** De tijdlijn is gewijzigd. Mogelijk zijn advertenties toegevoegd aan of verwijderd uit de tijdlijn.

* ** Callback om ** `onTimelineUpdated(TimelineEvent event)` uit te voeren

* ** Gebeurteniscode ** `TIMELINE_UPDATED`