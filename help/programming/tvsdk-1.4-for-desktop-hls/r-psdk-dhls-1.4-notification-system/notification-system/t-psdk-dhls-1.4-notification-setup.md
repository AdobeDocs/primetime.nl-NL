---
description: U kunt luisteren naar meldingen en u kunt uw eigen meldingen toevoegen aan de berichtgeschiedenis.
seo-description: U kunt luisteren naar meldingen en u kunt uw eigen meldingen toevoegen aan de berichtgeschiedenis.
seo-title: Uw meldingssysteem instellen
title: Uw meldingssysteem instellen
uuid: 2d1876c7-4ce6-491c-880b-dd94697d4feb
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Uw meldingssysteem instellen{#set-up-your-notification-system}

U kunt luisteren naar meldingen en u kunt uw eigen meldingen toevoegen aan de berichtgeschiedenis.

De kern van het Primetime Player-meldingssysteem is de klasse Notification, die een standalone melding vertegenwoordigt.

De klasse NotificationHistory biedt een mechanisme voor het verzamelen van meldingen. Het slaat een logboek van bericht ( `NotificationHistoryItem`) voorwerpen op die een inzameling van Meldingen vertegenwoordigt.

Om meldingen te ontvangen:

* Luisteren naar meldingen
* Meldingen toevoegen aan de berichtgeschiedenis

1. Luisteren naar statuswijzigingen.
1. Implementeer de `MediaPlayer.StatusChangeEvent.STATUS_CHANGED` gebeurtenislistener.
1. TVSDK geeft een `MediaPlayer.StatusChangeEvent` instantie door aan de gebeurtenislistener, die twee parameters bevat:

   * Het nieuwe frame ( `MediaPlayer.Status`)
   * Een `MediaPlayerNotification` object

