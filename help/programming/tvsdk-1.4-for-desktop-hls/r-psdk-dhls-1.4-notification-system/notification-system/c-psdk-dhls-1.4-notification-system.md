---
description: MediaPlayerNotification-objecten bieden informatie over wijzigingen in spelerstatus, waarschuwingen en fouten. Fouten die het afspelen van de video stoppen, leiden ook tot een wijziging in de status van de speler.
title: Meldingen voor spelerstatus, activiteit, fouten en logboekregistratie
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 0%

---

# Overzicht {#notifications-for-player-status-activity-errors-and-logging-overview}

MediaPlayerNotification-objecten bieden informatie over wijzigingen in spelerstatus, waarschuwingen en fouten. Fouten die het afspelen van de video stoppen, leiden ook tot een wijziging in de status van de speler.

Uw toepassing kan de melding- en statusgegevens ophalen. U kunt ook een registratiesysteem voor diagnostiek en validatie maken met behulp van de meldingsgegevens.

U implementeert gebeurtenislisteners om gebeurtenissen vast te leggen en erop te reageren. Veel gebeurtenissen bieden `MediaPlayerNotification` statusmeldingen.
