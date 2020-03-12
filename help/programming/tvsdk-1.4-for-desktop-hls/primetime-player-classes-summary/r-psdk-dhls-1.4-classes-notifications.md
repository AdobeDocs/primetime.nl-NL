---
description: Deze klassen beschrijven berichten over fouten, waarschuwingen, en sommige activiteiten die de kwesties voor registreren en het zuiveren doeleinden.
seo-description: Deze klassen beschrijven berichten over fouten, waarschuwingen, en sommige activiteiten die de kwesties voor registreren en het zuiveren doeleinden.
seo-title: Kennisgevingsklassen
title: Kennisgevingsklassen
uuid: 3befc64b-4abd-47df-9c45-215b49029757
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# Kennisgevingsklassen {#notification-classes}

Deze klassen beschrijven berichten over fouten, waarschuwingen, en sommige activiteiten die de kwesties voor registreren en het zuiveren doeleinden.

Pakket: [com.adobe.mediacore.notifications](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/package-detail.html)

| Klassenaam | Beschrijving |
|---|---|
| [Melding](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/Notification.html) | Klasse die informatieberichten, waarschuwingen en fouten bevat. kapselt de objecten vertegenwoordiging van één enkele berichtgebeurtenis binnen [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistory.html)in. |
| [NotificationCode](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationCode.html) | Retourneert de beschrijving die is gekoppeld aan de opgegeven meldingscode en biedt numerieke constanten voor meldingsobjecten. |
| [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistory.html) | Klasse die een logboek met meldingsobjecten opslaat. Een cirkellijst van voorwerpen [NotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistoryItem.html) die toegang tot een de geschiedenislijst van berichtgebeurtenissen verleent. Dat wil zeggen dat er een lijst met elementen wordt bijgehouden, elk element dat een afzonderlijke instantie van de klasse [Notification](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/Notification.html) bevat. |
| [NotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistoryItem.html) | Klasse die een item in de cirkellijst in [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistory.html) definieert en het bericht en de bijbehorende tijdstempel bevat. |
| [NotificationType](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationType.html) | Klasse die de ondersteunde berichttypen bevat. |

