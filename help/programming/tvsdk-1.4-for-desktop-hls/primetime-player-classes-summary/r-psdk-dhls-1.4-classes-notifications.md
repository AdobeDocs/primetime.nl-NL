---
description: Deze klassen beschrijven berichten over fouten, waarschuwingen, en sommige activiteiten die de kwesties voor registreren en het zuiveren doeleinden.
title: Meldingsklassen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# Meldingsklassen {#notification-classes}

Deze klassen beschrijven berichten over fouten, waarschuwingen, en sommige activiteiten die de kwesties voor registreren en het zuiveren doeleinden.

Pakket: [com.adobe.mediacore.notifications](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/package-detail.html)

| Klassenaam | Beschrijving |
|---|---|
| [Melding](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/Notification.html) | Klasse die informatieberichten, waarschuwingen en fouten bevat. Hiermee wordt de objectrepresentatie van één berichtgebeurtenis ingekapseld in [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistory.html). |
| [NotificationCode](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationCode.html) | Retourneert de beschrijving die is gekoppeld aan de opgegeven meldingscode en biedt numerieke constanten voor meldingsobjecten. |
| [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistory.html) | Klasse die een logboek met meldingsobjecten opslaat. Een cirkellijst van [NotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistoryItem.html) objecten die toegang bieden tot een historielijst met berichtgebeurtenissen. Dit betekent dat er een lijst met elementen wordt bijgehouden, waarbij elk element een afzonderlijk exemplaar van het [Melding](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/Notification.html) klasse. |
| [NotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistoryItem.html) | Klasse die een item in de cirkellijst definieert in [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistory.html) en bevat de melding en het bijbehorende tijdstempel. |
| [NotificationType](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationType.html) | Klasse die de ondersteunde berichttypen bevat. |
