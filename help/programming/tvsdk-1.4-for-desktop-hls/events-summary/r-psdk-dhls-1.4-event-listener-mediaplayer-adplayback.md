---
description: TVSDK verzendt ad-playbackgebeurtenissen als reactie op ad-gerelateerde bewerkingen, zoals wanneer een advertentie wordt afgespeeld.
seo-description: TVSDK verzendt ad-playbackgebeurtenissen als reactie op ad-gerelateerde bewerkingen, zoals wanneer een advertentie wordt afgespeeld.
seo-title: Afspeelgebeurtenissen toevoegen
title: Afspeelgebeurtenissen toevoegen
uuid: 63138237-2315-45ff-914d-369da18fdff7
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---


# Afspeelgebeurtenissen toevoegen {#ad-playback-events}

TVSDK verzendt ad-playbackgebeurtenissen als reactie op ad-gerelateerde bewerkingen, zoals wanneer een advertentie wordt afgespeeld.

Registreer listeners bij het `MediaPlayer`-object voor de volgende gebeurtenissen om op de hoogte te worden gesteld van alle gebeurtenissen die betrekking hebben op het afspelen van het item.

>[!TIP]
>
>Wanneer advertenties worden ingevoegd in of verwijderd uit de media, verzendt TVSDK de gebeurtenis TimelineEvent.[TIMELINE_UPDATED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimelineEvent.html#TIMELINE_UPDATED).

| Gebeurtenis | Betekenis |
|---|---|
| AdBreakPlaybackEvent.[AD_BREAK_COMPLETED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdBreakPlaybackEvent.html#AD_BREAK_COMPLETED) | Een advertentie-einde is volledig afgespeeld. |
| AdBreakPlaybackEvent.[AD_BREAK_SKIPPED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdBreakPlaybackEvent.html#AD_BREAK_SKIPPED) | Een advertentie-einde is overgeslagen tijdens het afspelen. |
| AdBreakPlaybackEvent.[AD_BREAK_STARTED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdBreakPlaybackEvent.html#AD_BREAK_STARTED) | Er is een advertentie-einde gestart. |
| AdClickEvent.[AD _KLIKKEN](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdClickEvent.html#AD_CLICK) | De gebruiker heeft op de advertentie geklikt. Verstrekt informatie aan uw toepassing over de advertentie die de gebruiker klikte, in antwoord op uw toepassing die `notifyClick` op `MediaPlayerView` roept. |
| AdPlaybackEvent.[AD _COMPLEET](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_COMPLETED) | Een advertentie heeft helemaal gespeeld. |
| AdPlaybackEvent.[AD_PROGRESS](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_PROGRESS) | Het afspelen van de advertentie is voortgezet. Wordt meerdere keren verzonden terwijl een advertentie wordt afgespeeld. |
| AdPlaybackEvent.[AD_ZOEKEN](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_STARTED) | Een zoekopdracht heeft zich over advertentiegrenzen of binnen een advertentie voorgedaan. |
| AdPlaybackEvent.[AD _STARTEN](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_STARTED) | Er is een advertentie gestart. |