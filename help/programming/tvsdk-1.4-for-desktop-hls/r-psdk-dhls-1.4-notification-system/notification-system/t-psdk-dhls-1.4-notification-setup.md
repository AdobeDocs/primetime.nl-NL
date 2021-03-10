---
description: U kunt luisteren naar meldingen en u kunt uw eigen meldingen toevoegen aan de berichtgeschiedenis.
title: Uw meldingssysteem instellen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---


# Uw meldingssysteem instellen{#set-up-your-notification-system}

U kunt luisteren naar meldingen en u kunt uw eigen meldingen toevoegen aan de berichtgeschiedenis.

De kern van het Primetime Player-meldingssysteem is de klasse Notification, die een standalone melding vertegenwoordigt.

De klasse NotificationHistory biedt een mechanisme voor het verzamelen van meldingen. Er wordt een logboek met meldingsobjecten ( `NotificationHistoryItem`) opgeslagen dat een verzameling meldingen vertegenwoordigt.

Om meldingen te ontvangen:

* Luisteren naar meldingen
* Meldingen toevoegen aan de berichtgeschiedenis

1. Luisteren naar statuswijzigingen.
1. Implementeer de gebeurtenislistener `MediaPlayer.StatusChangeEvent.STATUS_CHANGED`.
1. TVSDK geeft een `MediaPlayer.StatusChangeEvent`-instantie door aan de gebeurtenislistener, die twee parameters bevat:

   * De nieuwe status ( `MediaPlayer.Status`)
   * Een object `MediaPlayerNotification`

