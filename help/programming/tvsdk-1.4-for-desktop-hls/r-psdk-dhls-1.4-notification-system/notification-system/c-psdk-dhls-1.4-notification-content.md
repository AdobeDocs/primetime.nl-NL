---
description: MediaPlayerNotification biedt informatie die gerelateerd is aan de status van de speler.
seo-description: MediaPlayerNotification biedt informatie die gerelateerd is aan de status van de speler.
seo-title: Inhoud voor meldingen
title: Inhoud voor meldingen
uuid: c2321a49-1b60-4e44-b8e2-a023b764d779
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---


# Kennisgevingsinhoud{#notification-content}

MediaPlayerNotification biedt informatie die gerelateerd is aan de status van de speler.

TVSDK bevat een chronologische lijst met `MediaPlayerNotification`-meldingen. Elke melding bevat de volgende informatie:

* Tijdstempel
* Diagnostische metagegevens die bestaan uit de volgende elementen:

   * type INFO, WARN of ERROR
   * `code`: Een numerieke weergave van de kennisgeving.
   * `name`: Een door mensen leesbare beschrijving van de melding, zoals SEEK_ERROR
   * `metadata`: Sleutel-waardeparen die relevante informatie over de kennisgeving bevatten. Een sleutel met de naam `URL` levert bijvoorbeeld een waarde die een URL is die gerelateerd is aan het bericht.

   * `innerNotification`: Een verwijzing naar een ander  `MediaPlayerNotification` object dat rechtstreeks van invloed is op deze melding.

U kunt deze informatie lokaal opslaan voor latere analyse of naar een externe server verzenden voor registratie en grafische weergave.
