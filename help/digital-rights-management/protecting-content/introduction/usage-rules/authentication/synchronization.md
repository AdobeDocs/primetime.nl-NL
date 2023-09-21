---
title: Vereisten voor synchronisatie
description: Vereisten voor synchronisatie
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# Voorschriften voor synchronisatie {#requirements-for-synchronization}

Vereisten voor synchronisatie geven de frequentie aan waarmee de client de status synchroniseert met de server. Als aan de client een out-of-band licentie is verleend (zonder dat er een licentieserver wordt gecontacteerd), kunnen gebruiksregels opgeven dat de client synchronisatieberichten naar de server moet sturen om de veilige tijd van de client te synchroniseren en de status van de client aan de server moet rapporteren.

Het synchronisatiegedrag wordt bepaald gebruikend de volgende parameters:

* **Begininterval** - Geeft aan hoe lang moet worden gewacht na de laatste geslaagde synchronisatie om een andere synchronisatieaanvraag te starten.
* **Interval harde stop** - (Optioneel). Afspelen niet toestaan als de synchronisatie niet binnen de opgegeven tijd is gelukt.
* **Synchronisatiewaarschijnlijkheid forceren** - (Optioneel). Mogelijkheid waarmee de client een synchronisatiebericht moet verzenden vóór het volgende begininterval.

>[!NOTE]
>
>Deze gebruiksregel wordt ondersteund door Primetime DRM-clients versie 3.0 of hoger. Het gedrag bij oudere clients is afhankelijk van de minimale clientversie die door de licentieserver wordt ondersteund.
