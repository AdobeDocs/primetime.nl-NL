---
description: U kunt meldingen gebruiken om realtime aanmelding in uw videotoepassing te implementeren.
seo-description: U kunt meldingen gebruiken om realtime aanmelding in uw videotoepassing te implementeren.
seo-title: Logboekregistratie en foutopsporing in realtime toevoegen
title: Logboekregistratie en foutopsporing in realtime toevoegen
uuid: 568ea2e7-963b-427e-9cb2-e261e4423902
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Logboekregistratie en foutopsporing in realtime toevoegen{#add-real-time-logging-and-debugging}

U kunt meldingen gebruiken om realtime aanmelding in uw videotoepassing te implementeren.

Het berichtsysteem staat u toe om het registreren en het zuiveren informatie voor diagnostiek en bevestiging te verzamelen zonder het systeem te benadrukken.

>[!IMPORTANT]
>
>Het registreren achtereind maakt geen deel uit van een productieconfiguratie en wordt niet verwacht om hoog-ladingsverkeer te behandelen. Als uw implementatie niet volledig hoeft te zijn, kunt u beter de efficiëntie van gegevensoverdracht in overweging nemen om te voorkomen dat uw systeem wordt overbelast.

Hier is een voorbeeld van hoe u meldingen kunt ophalen.

1. Creeer een op tijdopnemer-gebaseerde uitvoeringsdraad voor uw videotoepassing die periodiek de gegevens vraagt die door het TVSDK berichtsysteem worden verzameld.

1. Als het interval van de timer te groot is en de gebeurtenislijst te klein is, loopt de lijst met berichtgebeurtenissen over. Voer een van de volgende handelingen uit om deze overloop te voorkomen:

   * Verlaag het tijdinterval dat de draad drijft die voor nieuwe gebeurtenissen opiniepeilt.
   * Vergroot de lijst met meldingen.

1. Serialiseren van de meest recente berichtgebeurtenisberichten in JSON-indeling en verzenden de berichten naar een externe server voor nabewerking.

   De externe server kan de verschafte gegevens dan grafisch in real-time weergeven.
1. Om het verlies van berichtgebeurtenissen te ontdekken, zoek hiaten in de opeenvolging van waarden van de gebeurtenisindex.

   Elke meldingsgebeurtenis heeft een indexwaarde die automatisch wordt verhoogd door de `NotificationHistory` klasse.
