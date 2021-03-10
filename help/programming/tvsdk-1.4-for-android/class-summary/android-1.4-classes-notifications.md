---
description: Deze klassen beschrijven berichten over fouten, waarschuwingen, en sommige activiteiten die TVSDK voor het registreren en het zuiveren doeleinden uitgeeft.
title: Kennisgevingsklassen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---


# Kennisgevingsklassen{#notification-classes}

Deze klassen beschrijven berichten over fouten, waarschuwingen, en sommige activiteiten die TVSDK voor het registreren en het zuiveren doeleinden uitgeeft.

Pakket: [com.adobe.mediacore](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/package-summary.html) Pakket: [com.adobe.mediacore.session](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/package-summary.html)

| Klassenaam | Beschrijving |
|---|---|
| MediaPlayerNotification. [Fout](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.Error.html) | Klasse die de melding voor een fout beschrijft die ervoor zorgt dat de speler het afspelen stopt. Dit is een [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) van berichttype FOUT. |
| MediaPlayerNotification. [Info](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.Info.html) | Klasse die een informatieve melding beschrijft. Dit is een [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) van berichttype INFO. |
| MediaPlayerNotification. [Waarschuwing](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.Warning.html) | Klasse die een waarschuwingsbericht beschrijft. Dit is een [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) van berichttype WAARSCHUWING. |
| [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) | Klasse die informatieberichten, waarschuwingen en fouten bevat. Hiermee wordt de objectrepresentatie van één berichtgebeurtenis ingekapseld binnen [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.html). |
| MediaPlayerNotification. [NotificationCode](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.NotificationCode.html) | Retourneert de beschrijving die is gekoppeld aan de opgegeven meldingscode. |
| [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.html) | Klasse die een logboek met meldingsobjecten opslaat. Een cirkellijst van [NotificationHistory.Item](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.Item.html) voorwerpen die toegang tot een de geschiedenislijst van berichtgebeurtenissen verleent. Dat wil zeggen dat er een lijst met elementen wordt bijgehouden, elk element dat een afzonderlijke instantie bevat van de klasse [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html). (In [session](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/package-summary.html)-pakket.) |
| NotificationHistory. [Item](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.Item.html) | Klasse die een ingang in de kringlijst in [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.html) bepaalt en het bericht en zijn timestamp houdt. |
| MediaPlayerNotification. [EntryType](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.EntryType.html) | Klasse die de ondersteunde berichttypen bevat. |