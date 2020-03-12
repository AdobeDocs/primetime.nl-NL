---
description: Deze klassen beschrijven berichten over fouten, waarschuwingen, en sommige activiteiten die TVSDK voor het registreren en het zuiveren doeleinden uitgeeft.
seo-description: Deze klassen beschrijven berichten over fouten, waarschuwingen, en sommige activiteiten die TVSDK voor het registreren en het zuiveren doeleinden uitgeeft.
seo-title: Kennisgevingsklassen
title: Kennisgevingsklassen
uuid: e231a2d0-6190-4251-87db-ca46d2aee60d
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Kennisgevingsklassen{#notification-classes}

Deze klassen beschrijven berichten over fouten, waarschuwingen, en sommige activiteiten die TVSDK voor het registreren en het zuiveren doeleinden uitgeeft.

Pakket: [com.adobe.mediacore](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/package-summary.html) -pakket: [com.adobe.mediacore.session](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/package-summary.html)

| Klassenaam | Beschrijving |
|---|---|
| MediaPlayerNotification. [Fout](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.Error.html) | Klasse die de melding voor een fout beschrijft die ervoor zorgt dat de speler het afspelen stopt. Dit is een [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) van berichttype FOUT. |
| MediaPlayerNotification. [Info](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.Info.html) | Klasse die een informatieve melding beschrijft. Dit is een [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) van berichttype INFO. |
| MediaPlayerNotification. [Waarschuwing](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.Warning.html) | Klasse die een waarschuwingsbericht beschrijft. Dit is een [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) van berichttype WAARSCHUWING. |
| [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) | Klasse die informatieberichten, waarschuwingen en fouten bevat. kapselt de objecten vertegenwoordiging van één enkele berichtgebeurtenis binnen [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.html)in. |
| MediaPlayerNotification. [NotificationCode](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.NotificationCode.html) | Retourneert de beschrijving die is gekoppeld aan de opgegeven meldingscode. |
| [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.html) | Klasse die een logboek met meldingsobjecten opslaat. Een cirkellijst van voorwerpen [NotificationHistory.Item](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.Item.html) die toegang tot een de geschiedenislijst van berichtgebeurtenissen verleent. Dat wil zeggen dat er een lijst met elementen wordt bijgehouden, elk element dat een afzonderlijke instantie van de [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) -klasse bevat. (In- [sessiepakket](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/package-summary.html) .) |
| NotificationHistory. [Item](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.Item.html) | Klasse die een item in de cirkellijst in [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.html) definieert en het bericht en de bijbehorende tijdstempel bevat. |
| MediaPlayerNotification. [EntryType](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.EntryType.html) | Klasse die de ondersteunde berichttypen bevat. |