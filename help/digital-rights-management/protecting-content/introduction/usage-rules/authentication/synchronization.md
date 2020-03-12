---
seo-title: Vereisten voor synchronisatie
title: Vereisten voor synchronisatie
uuid: 19a6ee7e-9580-48bb-a3a6-ff2cedcc796a
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# Voorschriften voor synchronisatie {#requirements-for-synchronization}

Vereisten voor synchronisatie geven de frequentie aan waarmee de client de status synchroniseert met de server. Als aan de client een out-of-band licentie is verleend (zonder dat er een licentieserver wordt gecontacteerd), kunnen gebruiksregels opgeven dat de client synchronisatieberichten naar de server moet sturen om de veilige tijd van de client te synchroniseren en de status van de client aan de server moet rapporteren.

Het synchronisatiegedrag wordt bepaald gebruikend de volgende parameters:

* **Interval** starten - Geeft aan hoe lang er moet worden gewacht na de laatste succesvolle synchronisatie om een andere synchronisatieaanvraag te starten.
* **Hard stopinterval** - (optioneel). Afspelen niet toestaan als de synchronisatie niet binnen de opgegeven tijd is gelukt.
* **Synchrone synchronisatiewaarschijnlijkheid** forceren (optioneel). Mogelijkheid waarmee de client een synchronisatiebericht moet verzenden vóór het volgende begininterval.

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>Deze gebruiksregel wordt ondersteund door Primetime DRM-clients versie 3.0 of hoger. Het gedrag bij oudere clients is afhankelijk van de minimale clientversie die door de licentieserver wordt ondersteund.
