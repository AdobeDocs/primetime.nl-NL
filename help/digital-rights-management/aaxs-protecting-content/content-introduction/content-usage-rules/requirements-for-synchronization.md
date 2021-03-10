---
title: Voorschriften voor synchronisatie
description: Voorschriften voor synchronisatie
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---


# Vereisten voor synchronisatie{#requirements-for-synchronization}

Hiermee geeft u de frequentie op waarmee de client de status synchroniseert met de server. Als aan de client een out-of-band licentie is verleend (zonder dat er een licentieserver wordt gecontacteerd), kunnen gebruiksregels opgeven dat de client synchronisatieberichten naar de server moet verzenden om de veilige tijd van de client te synchroniseren en de status van de client aan de server te melden.

Het synchronisatiegedrag wordt bepaald gebruikend de volgende parameters:

* Start Interval — Geeft aan hoe lang er moet worden gewacht na de laatste succesvolle synchronisatie om een andere synchronisatieaanvraag te starten.
* Hard stopinterval — (optioneel). Afspelen niet toestaan als de synchronisatie niet binnen de opgegeven tijd is gelukt.
* Synchrone synchronisatiewaarschijnlijkheid forceren (optioneel). Mogelijkheid waarmee de client een synchronisatiebericht moet verzenden vóór het volgende begininterval.

>[!NOTE]
>
>Deze gebruiksregel wordt gesteund door de cliëntversie 3.0 van de Toegang van de Adobe. Het gedrag bij oudere clients is afhankelijk van de minimale clientversie die door de licentieserver wordt ondersteund. Zie [Minimale clientversie](../../../aaxs-protecting-content/content-implementing-the-license-server/content-handling-license-reqs/content-minimum-client-version.md).

