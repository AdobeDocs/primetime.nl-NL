---
description: MediaPlayerNotification biedt informatie die gerelateerd is aan de status van de speler.
title: Inhoud voor meldingen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# Inhoud voor meldingen{#notification-content}

MediaPlayerNotification biedt informatie die gerelateerd is aan de status van de speler.

TVSDK verstrekt een chronologische lijst van `MediaPlayerNotification` meldingen. Elke melding bevat de volgende informatie:

* Tijdstempel
* Diagnostische metagegevens die bestaan uit de volgende elementen:

   * type INFO, WARN of ERROR
   * `code`: Een numerieke weergave van de kennisgeving.
   * `name`: Een door mensen leesbare beschrijving van de melding, zoals SEEK_ERROR
   * `metadata`: sleutel/waardeparen die relevante informatie over de kennisgeving bevatten. Bijvoorbeeld een toets met de naam `URL` Hiermee wordt een waarde opgegeven die een URL is die gerelateerd is aan het bericht.

   * `innerNotification`: Een verwijzing naar een andere `MediaPlayerNotification` object dat rechtstreeks van invloed is op deze melding.

U kunt deze informatie lokaal opslaan voor latere analyse of naar een externe server verzenden voor registratie en grafische weergave.
