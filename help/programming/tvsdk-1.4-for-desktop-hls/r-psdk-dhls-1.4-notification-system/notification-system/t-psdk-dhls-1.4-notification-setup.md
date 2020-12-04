---
description: U kunt luisteren naar meldingen en u kunt uw eigen meldingen toevoegen aan de berichtgeschiedenis.
seo-description: U kunt luisteren naar meldingen en u kunt uw eigen meldingen toevoegen aan de berichtgeschiedenis.
seo-title: Uw meldingssysteem instellen
title: Uw meldingssysteem instellen
uuid: 2d1876c7-4ce6-491c-880b-dd94697d4feb
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '139'
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

