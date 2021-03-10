---
description: Deze klassen beschrijven berichten over fouten, waarschuwingen, en sommige activiteiten die TVSDK voor het registreren en het zuiveren doeleinden uitgeeft.
title: Kennisgevingsklassen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---


# Kennisgevingsklassen {#notification-classes}

Deze klassen beschrijven berichten over fouten, waarschuwingen, en sommige activiteiten die TVSDK voor het registreren en het zuiveren doeleinden uitgeeft.

| **Klassenaam** | **Beschrijving** |
|---|---|
| [PTMediaError](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaError.html) | Klasse die de melding voor een fout beschrijft die ervoor zorgt dat de speler het afspelen stopt. Dit is een [PTNotification](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotification.html) van berichttype FOUT. |
| [PTMediaPlayerNotifications](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaPlayerNotifications.html) | Hier worden alle meldingen weergegeven die door het Primetime Player-framework worden verzonden. |
| [PTNotification](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotification.html) | Klasse die informatieberichten, waarschuwingen en fouten bevat. Hiermee wordt de objectrepresentatie van één berichtgebeurtenis ingekapseld binnen [PTNotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistory.html). |
| [PTNotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistory.html) | Klasse die een logboek van berichtvoorwerpen [PTNotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistoryItem.html) voorwerpen opslaat die toegang tot een de geschiedenislijst van berichtgebeurtenissen verleent. Dat wil zeggen dat er een lijst met elementen wordt bijgehouden, waarbij elk element een afzonderlijke instantie bevat van de [PTNotification](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotification.html) |
| [PTNotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistoryItem.html) | Klasse die een ingang in de kringlijst in [PTNotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistory.html) bepaalt en het bericht en zijn timestamp houdt. |

