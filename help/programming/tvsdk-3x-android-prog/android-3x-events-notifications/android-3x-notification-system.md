---
description: Met gebeurtenissen en meldingen kunt u de asynchrone aspecten van de videotoepassing beheren.
seo-description: Met gebeurtenissen en meldingen kunt u de asynchrone aspecten van de videotoepassing beheren.
seo-title: Meldingen en gebeurtenissen voor spelerstatus, activiteit, fouten en logboekregistratie
title: Meldingen en gebeurtenissen voor spelerstatus, activiteit, fouten en logboekregistratie
uuid: c4a108e7-72aa-4c96-9538-b1385343d6af
translation-type: tm+mt
source-git-commit: 5df9a8b98baaf1cd1803581d2b60c7ed4261a0e8
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---


# Meldingen en gebeurtenissen voor spelerstatus, activiteit, fouten en logboekregistratie {#notifications-and-events-for-player-status-activity-errors-and-logging}

Met gebeurtenissen en meldingen kunt u de asynchrone aspecten van de videotoepassing beheren.

`MediaPlayerStatus` objecten bevatten informatie over wijzigingen in de spelerstatus. `Notification` objecten bevatten informatie over waarschuwingen en fouten. Fouten die het afspelen van de video stoppen, leiden ook tot een wijziging in de status van de speler. U implementeert gebeurtenislisteners om gebeurtenissen ( `MediaPlayerEvent` objecten) vast te leggen en erop te reageren.

Uw toepassing kan meldingen en statusgegevens ophalen. Met deze informatie kunt u ook een registratiesysteem voor diagnostiek en validatie maken.

## Inhoud voor meldingen {#section_DF951FF601794CF592841BB7406DC1A1}

`MediaPlayerNotification` geeft informatie over de status van de speler.

TVSDK verstrekt een chronologische lijst van `MediaPlayerNotification` meldingen, en elke kennisgeving bevat de volgende informatie:

* Een tijdstempel
* Diagnostische metagegevens die bestaan uit de volgende elementen:

   * `type`: INFORMATIE, WAARSCHUWING of FOUT.
   * `code`: Een numerieke weergave van de kennisgeving.
   * `name`: Een door mensen leesbare beschrijving van de melding, zoals SEEK_ERROR
   * `metadata`: Sleutel-waardeparen die relevante informatie over de kennisgeving bevatten. Een benoemde sleutel `URL` biedt bijvoorbeeld een waarde die een URL is die gerelateerd is aan het bericht.

   * `innerNotification`: Een verwijzing naar een ander `MediaPlayerNotification` object dat rechtstreeks van invloed is op deze melding.

U kunt deze informatie lokaal opslaan voor latere analyse of naar een externe server verzenden voor registratie en grafische weergave.

## Uw meldingssysteem instellen {#section_9E37C09ECFA54B3DA8D3AA9ED1BAFC17}

U kunt luisteren naar meldingen.

De kern van het meldingssysteem van de Speler Primetime is de `Notification` klasse, die een standalone bericht vertegenwoordigt.

Als u meldingen wilt ontvangen, luistert u als volgt naar meldingen:

1. Implementeer de `NotificationEventListener.onNotification()` callback.
1. TVSDK geeft een `NotificationEvent` object door aan de callback.

   >[!NOTE]
   >
   >Typen meldingen worden opgesomd in de `Notification.Type` opsomming:

   * `ERROR`
   * `INFO`
   * `WARNING`

## Logboekregistratie en foutopsporing in realtime toevoegen {#section_9D4004308CB243AD9B50818895D10005}

U kunt meldingen gebruiken om realtime aanmelding in uw videotoepassing te implementeren.

Het berichtsysteem staat u toe om het registreren en het zuiveren informatie voor diagnostiek en bevestiging te verzamelen zonder het systeem te benadrukken.

>[!IMPORTANT]
>
>Het registreren achtereind maakt geen deel uit van een productieconfiguratie en wordt niet verwacht om hoog-ladingsverkeer te behandelen. Als uw implementatie niet volledig hoeft te zijn, kunt u beter de efficiëntie van gegevensoverdracht in overweging nemen om te voorkomen dat uw systeem wordt overbelast.

Hier is een voorbeeld van hoe u meldingen kunt ophalen:

1. Creeer een op tijdopnemer-gebaseerde uitvoeringsdraad voor uw videotoepassing die periodiek de gegevens vraagt die door het TVSDK berichtsysteem worden verzameld.
1. Als het interval van de timer te groot is en de gebeurtenislijst te klein is, loopt de lijst met berichtgebeurtenissen over.

   >[!NOTE]
   >
   >Voer een van de volgende handelingen uit om deze overloop te voorkomen:
   >
   >1. Verlaag het tijdinterval dat de draad drijft die voor nieuwe gebeurtenissen opiniepeilt.
      >
      >
   1. Vergroot de lijst met meldingen.


1. Serialiseren van de meest recente berichtgebeurtenisberichten in JSON-indeling en verzenden de berichten naar een externe server voor nabewerking.

   >[!NOTE]
   >
   >De externe server kan de verschafte gegevens grafisch in real-time weergeven.

1. Om het verlies van berichtgebeurtenissen te ontdekken, zoek hiaten in de opeenvolging van waarden van de gebeurtenisindex.