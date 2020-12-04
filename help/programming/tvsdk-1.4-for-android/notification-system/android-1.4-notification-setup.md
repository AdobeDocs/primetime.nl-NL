---
description: U kunt luisteren naar meldingen en u kunt uw eigen meldingen toevoegen aan de berichtgeschiedenis.
seo-description: U kunt luisteren naar meldingen en u kunt uw eigen meldingen toevoegen aan de berichtgeschiedenis.
seo-title: Uw meldingssysteem instellen
title: Uw meldingssysteem instellen
uuid: caa6a306-dea9-45ee-b0b3-569b5f2527a1
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 0%

---


# Uw meldingssysteem instellen{#set-up-your-notification-system}

U kunt luisteren naar meldingen en u kunt uw eigen meldingen toevoegen aan de berichtgeschiedenis.

De kern van het Primetime Player meldingssysteem is de `Notification` klasse, die een standalone bericht vertegenwoordigt.

De klasse `NotificationHistory` biedt een mechanisme voor het verzamelen van meldingen. Het slaat een logboek van bericht (NotificationHistoryItem) voorwerpen op die een inzameling van Meldingen vertegenwoordigt.

Om meldingen te ontvangen:

* Luisteren naar meldingen
* Meldingen toevoegen aan de berichtgeschiedenis

1. Luisteren naar statuswijzigingen.
1. Voer `MediaPlayer.PlaybackEventListener.onStateChanged` callback uit.
1. TVSDK geeft twee parameters door aan de callback:

   * De nieuwe status ( `MediaPlayer.PlayerState`)
   * Een object `MediaPlayerNotification`

