---
description: U kunt luisteren naar meldingen en u kunt uw eigen meldingen toevoegen aan de berichtgeschiedenis.
title: Uw meldingssysteem instellen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---

# Uw meldingssysteem instellen{#set-up-your-notification-system}

U kunt luisteren naar meldingen en u kunt uw eigen meldingen toevoegen aan de berichtgeschiedenis.

De kern van het Primetime Player-meldingssysteem is de klasse Notification, die een standalone melding vertegenwoordigt.

De klasse NotificationHistory biedt een mechanisme voor het verzamelen van meldingen. Het slaat een logboek van bericht op ( `NotificationHistoryItem`) objecten die een verzameling meldingen vertegenwoordigen.

Om meldingen te ontvangen:

* Luisteren naar meldingen
* Meldingen toevoegen aan de berichtgeschiedenis

1. Luisteren naar statuswijzigingen.
1. Implementeer de `MediaPlayer.StatusChangeEvent.STATUS_CHANGED` gebeurtenislistener.
1. TVSDK geeft een `MediaPlayer.StatusChangeEvent` -instantie aan de gebeurtenislistener, die twee parameters bevat:

   * De nieuwe staat ( `MediaPlayer.Status`)
   * A `MediaPlayerNotification` object
