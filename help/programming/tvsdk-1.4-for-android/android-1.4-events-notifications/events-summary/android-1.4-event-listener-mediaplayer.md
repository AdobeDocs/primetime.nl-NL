---
description: TVSDK verzendt ad-playbackgebeurtenissen als reactie op ad-gerelateerde bewerkingen, zoals wanneer een advertentie wordt afgespeeld.
seo-description: TVSDK verzendt ad-playbackgebeurtenissen als reactie op ad-gerelateerde bewerkingen, zoals wanneer een advertentie wordt afgespeeld.
seo-title: Afspeelgebeurtenissen toevoegen
title: Afspeelgebeurtenissen toevoegen
uuid: dd6991ae-3e33-4d92-92e9-26b1086a555a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---


# Afspeelgebeurtenissen toevoegen{#ad-playback-events}

TVSDK verzendt ad-playbackgebeurtenissen als reactie op ad-gerelateerde bewerkingen, zoals wanneer een advertentie wordt afgespeeld.

Registreer een implementatie van `MediaPlayer.AdPlaybackEventListener` met inbegrip van de volgende callbacks om op de hoogte te worden gesteld van alle gebeurtenissen die betrekking hebben op het afspelen van advertenties.

>[!TIP]
>
>Wanneer advertenties worden ingevoegd in of verwijderd uit de media, verzendt TVSDK de afspeelgebeurtenis [onTimelineUpdated](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onTimelineUpdated()).

| Gebeurtenis | Betekenis |
|---|---|
| [onAdBreakComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdBreakComplete(com.adobe.mediacore.timeline.advertising.AdBreak)) (AdBreak adBreak) | Een advertentie-einde is volledig afgespeeld. |
| onAdBreakSkipped | Een advertentie-einde is overgeslagen tijdens het afspelen. |
| [onAdBreakStart](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdBreakStart(com.adobe.mediacore.timeline.advertising.AdBreak)) (AdBreak adBreak) | Er is een advertentie-einde gestart. |
| [onAdClick](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdClick(com.adobe.mediacore.timeline.advertising.AdBreak,%20com.adobe.mediacore.timeline.advertising.Ad,%20com.adobe.mediacore.timeline.advertising.AdClick)) (AdBreak adBreak, Advertentie, AdClick enClick) | De gebruiker heeft op de advertentie geklikt. Verstrekt informatie aan uw toepassing over de advertentie die de gebruiker klikte, in antwoord op uw toepassing die `notifyClick` op `MediaPlayerView` roept. |
| [onAdComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdComplete(com.adobe.mediacore.timeline.advertising.AdBreak)) (AdBreak adBreak, advertentie) | Een advertentie heeft helemaal gespeeld. |
| [onAdProgress](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdProgress(com.adobe.mediacore.timeline.advertising.AdBreak,com.adobe.mediacore.timeline.advertising.Ad,%20int))  (AdBreak adBreak, Ad ad, int percentage) | Het afspelen van de advertentie is voortgezet. Wordt meerdere keren verzonden terwijl een advertentie wordt afgespeeld. |
| [onAdStart](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdStart(com.adobe.mediacore.timeline.advertising.AdBreak,%20com.adobe.mediacore.timeline.advertising.Ad)) (AdBreak adBreak, advertentie) | Er is een advertentie gestart. |