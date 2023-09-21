---
description: TVSDK verzendt ad-playbackgebeurtenissen als reactie op ad-gerelateerde bewerkingen, zoals wanneer een advertentie wordt afgespeeld.
title: Afspeelgebeurtenissen toevoegen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Afspeelgebeurtenissen toevoegen{#ad-playback-events}

TVSDK verzendt ad-playbackgebeurtenissen als reactie op ad-gerelateerde bewerkingen, zoals wanneer een advertentie wordt afgespeeld.

Registreer een implementatie van `MediaPlayer.AdPlaybackEventListener` inclusief de volgende callbacks.

>[!TIP]
>
>Wanneer advertenties in het medium worden geplaatst of uit het medium worden verwijderd, verzendt TVSDK de afspeelgebeurtenis [onTimelineUpdated](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onTimelineUpdated()).

| Gebeurtenis | Betekenis |
|---|---|
| [onAdBreakComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdBreakComplete(com.adobe.mediacore.timeline.advertising.AdBreak)) (AdBreak adBreak) | Een advertentie-einde is volledig afgespeeld. |
| onAdBreakSkipped | Een advertentie-einde is overgeslagen tijdens het afspelen. |
| [onAdBreakStart](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdBreakStart(com.adobe.mediacore.timeline.advertising.AdBreak)) (AdBreak adBreak) | Er is een advertentie-einde gestart. |
| [onAdClick](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdClick(com.adobe.mediacore.timeline.advertising.AdBreak,%20com.adobe.mediacore.timeline.advertising.Ad,%20com.adobe.mediacore.timeline.advertising.AdClick)) (AdBreak, advertentie, AdClick en klik) | De gebruiker heeft op de advertentie geklikt. Verstrekt informatie aan uw toepassing over de advertentie die de gebruiker klikte, in antwoord op uw toepassing die `notifyClick` op de `MediaPlayerView`. |
| [onAdComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdComplete(com.adobe.mediacore.timeline.advertising.AdBreak)) (AdBreak, advertentie) | Een advertentie heeft helemaal gespeeld. |
| [onAdProgress](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdProgress(com.adobe.mediacore.timeline.advertising.AdBreak,com.adobe.mediacore.timeline.advertising.Ad,%20int)) (AdBreak adBreak, Ad ad, int percentage) | Het afspelen van de advertentie is voortgezet. Wordt meerdere keren verzonden terwijl een advertentie wordt afgespeeld. |
| [onAdStart](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdStart(com.adobe.mediacore.timeline.advertising.AdBreak,%20com.adobe.mediacore.timeline.advertising.Ad)) (AdBreak, advertentie) | Er is een advertentie gestart. |
