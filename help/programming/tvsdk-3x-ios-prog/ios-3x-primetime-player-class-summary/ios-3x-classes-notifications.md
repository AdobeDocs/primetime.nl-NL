---
description: Deze klassen beschrijven berichten over fouten, waarschuwingen, en sommige activiteiten die TVSDK voor het registreren en het zuiveren doeleinden uitgeeft.
title: Meldingsklassen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# Meldingsklassen {#notification-classes}

Deze klassen beschrijven berichten over fouten, waarschuwingen, en sommige activiteiten die TVSDK voor het registreren en het zuiveren doeleinden uitgeeft.

| **Klassenaam** | **Beschrijving** |
|---|---|
| [PTMediaError](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaError.html) | Klasse die de melding voor een fout beschrijft die ervoor zorgt dat de speler het afspelen stopt. Dit is een [PTNotification](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotification.html) van berichttype ERROR. |
| [PTMediaPlayerNotifications](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaPlayerNotifications.html) | Hier worden alle meldingen weergegeven die door het Primetime Player-framework worden verzonden. |
| [PTNotification](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotification.html) | Klasse die informatieberichten, waarschuwingen en fouten bevat. Hiermee wordt de objectrepresentatie van één berichtgebeurtenis ingekapseld in [PTNotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistory.html). |
| [PTNotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistory.html) | Klasse die een logboek met meldingsobjecten opslaat [PTNotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistoryItem.html) objecten die toegang bieden tot een historielijst met berichtgebeurtenissen. Dit betekent dat er een lijst met elementen wordt bijgehouden, waarbij elk element een afzonderlijk exemplaar van het [PTNotification](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotification.html) |
| [PTNotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistoryItem.html) | Klasse die een item in de cirkellijst definieert in [PTNotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistory.html) en bevat de melding en het bijbehorende tijdstempel. |
