---
seo-title: Voorschriften voor synchronisatie
title: Voorschriften voor synchronisatie
uuid: 976a0ae1-bece-437e-b95b-6cd222525d13
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Voorschriften voor synchronisatie{#requirements-for-synchronization}

Hiermee geeft u de frequentie op waarmee de client de status synchroniseert met de server. Als aan de client een out-of-band licentie is verleend (zonder dat er een licentieserver wordt gecontacteerd), kunnen gebruiksregels opgeven dat de client synchronisatieberichten naar de server moet verzenden om de veilige tijd van de client te synchroniseren en de status van de client aan de server te melden.

Het synchronisatiegedrag wordt bepaald gebruikend de volgende parameters:

* Start Interval — Geeft aan hoe lang er moet worden gewacht na de laatste succesvolle synchronisatie om een andere synchronisatieaanvraag te starten.
* Hard stopinterval — (optioneel). Afspelen niet toestaan als de synchronisatie niet binnen de opgegeven tijd is gelukt.
* Synchrone synchronisatiewaarschijnlijkheid forceren (optioneel). Mogelijkheid waarmee de client een synchronisatiebericht moet verzenden vóór het volgende begininterval.

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>Deze gebruiksregel wordt ondersteund door Adobe Access-clients versie 3.0 en hoger. Het gedrag bij oudere clients is afhankelijk van de minimale clientversie die door de licentieserver wordt ondersteund. Zie [Minimale clientversie](../../../aaxs-protecting-content/content-implementing-the-license-server/content-handling-license-reqs/content-minimum-client-version.md).

