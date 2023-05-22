---
description: TVSDK verzendt ad-playbackgebeurtenissen als reactie op ad-gerelateerde bewerkingen, zoals wanneer een advertentie wordt afgespeeld.
title: Afspeelgebeurtenissen toevoegen
exl-id: 61e7c9ec-20ed-4221-8ae7-b5d43adb4ce4
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# Afspeelgebeurtenissen toevoegen {#ad-playback-events}

TVSDK verzendt ad-playbackgebeurtenissen als reactie op ad-gerelateerde bewerkingen, zoals wanneer een advertentie wordt afgespeeld.

Registreer listeners bij de `MediaPlayer` -object voor de volgende gebeurtenissen.

>[!TIP]
>
>Wanneer advertenties worden ingevoegd in of verwijderd uit de media, verzendt TVSDK de gebeurtenis TimelineEvent.[TIMELINE_UPDATED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimelineEvent.html#TIMELINE_UPDATED).

| Gebeurtenis | Betekenis |
|---|---|
| AdBreakPlaybackEvent.[AD_BREAK_COMPLETED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdBreakPlaybackEvent.html#AD_BREAK_COMPLETED) | Een advertentie-einde is volledig afgespeeld. |
| AdBreakPlaybackEvent.[AD_BREAK_SKIPPED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdBreakPlaybackEvent.html#AD_BREAK_SKIPPED) | Een advertentie-einde is overgeslagen tijdens het afspelen. |
| AdBreakPlaybackEvent.[AD_BREAK_STARTED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdBreakPlaybackEvent.html#AD_BREAK_STARTED) | Er is een advertentie-einde gestart. |
| AdClickEvent.[AD _KLIKKEN](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdClickEvent.html#AD_CLICK) | De gebruiker heeft op de advertentie geklikt. Verstrekt informatie aan uw toepassing over de advertentie die de gebruiker klikte, in antwoord op uw toepassing die `notifyClick` op de `MediaPlayerView`. |
| AdPlaybackEvent.[AD _COMPLEET](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_COMPLETED) | Een advertentie heeft helemaal gespeeld. |
| AdPlaybackEvent.[AD_PROGRESS](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_PROGRESS) | Het afspelen van de advertentie is voortgezet. Wordt meerdere keren verzonden terwijl een advertentie wordt afgespeeld. |
| AdPlaybackEvent.[AD_ZOEKEN](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_STARTED) | Een zoekopdracht heeft zich over advertentiegrenzen of binnen een advertentie voorgedaan. |
| AdPlaybackEvent.[AD _STARTEN](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_STARTED) | Er is een advertentie gestart. |
