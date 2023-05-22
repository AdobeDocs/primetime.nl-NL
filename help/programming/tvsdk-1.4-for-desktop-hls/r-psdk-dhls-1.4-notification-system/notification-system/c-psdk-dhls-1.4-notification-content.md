---
description: MediaPlayerNotification biedt informatie die gerelateerd is aan de status van de speler.
title: Inhoud voor meldingen
exl-id: dc46f717-f08b-4d52-82ea-88107076f4fb
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
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
   * `metadata`: Sleutel-waardeparen die relevante informatie over de kennisgeving bevatten. Een toets met de naam `URL` Hiermee wordt een waarde opgegeven die een URL is die gerelateerd is aan het bericht.

   * `innerNotification`: Een verwijzing naar een andere `MediaPlayerNotification` object dat rechtstreeks van invloed is op deze melding.

U kunt deze informatie lokaal opslaan voor latere analyse of naar een externe server verzenden voor registratie en grafische weergave.
