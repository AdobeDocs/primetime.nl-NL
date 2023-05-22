---
description: U kunt luisteren naar meldingen en u kunt uw eigen meldingen toevoegen aan de berichtgeschiedenis.
title: Uw meldingssysteem instellen
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---


# Uw meldingssysteem instellen{#set-up-your-notification-system}

U kunt luisteren naar meldingen en u kunt uw eigen meldingen toevoegen aan de berichtgeschiedenis.

De kern van het meldingssysteem van Primetime Player is de `Notification` klasse, die een standalone bericht vertegenwoordigt.

De `NotificationHistory` class biedt een mechanisme voor het verzamelen van meldingen. Het slaat een logboek van bericht (NotificationHistoryItem) voorwerpen op die een inzameling van Meldingen vertegenwoordigt.

Om meldingen te ontvangen:

* Luisteren naar meldingen
* Meldingen toevoegen aan de berichtgeschiedenis

1. Luisteren naar statuswijzigingen.
1. Implementeer de `MediaPlayer.PlaybackEventListener.onStateChanged` callback.
1. TVSDK geeft twee parameters door aan de callback:

   * De nieuwe staat ( `MediaPlayer.PlayerState`)
   * A `MediaPlayerNotification` object

