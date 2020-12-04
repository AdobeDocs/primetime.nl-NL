---
seo-title: Vereisten voor synchronisatie
title: Vereisten voor synchronisatie
uuid: 19a6ee7e-9580-48bb-a3a6-ff2cedcc796a
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# Vereisten voor synchronisatie {#requirements-for-synchronization}

Vereisten voor synchronisatie geven de frequentie aan waarmee de client de status synchroniseert met de server. Als aan de client een out-of-band licentie is verleend (zonder dat er een licentieserver wordt gecontacteerd), kunnen gebruiksregels opgeven dat de client synchronisatieberichten naar de server moet sturen om de veilige tijd van de client te synchroniseren en de status van de client aan de server moet rapporteren.

Het synchronisatiegedrag wordt bepaald gebruikend de volgende parameters:

* **Het Interval**  van het begin - specificeert hoe lang om na de laatste succesvolle synchronisatie te wachten om een andere synchronisatieverzoek te beginnen.
* **Hard stopinterval**  (optioneel). Afspelen niet toestaan als de synchronisatie niet binnen de opgegeven tijd is gelukt.
* **Synchrone synchronisatiewaarschijnlijkheid**  forceren (optioneel). Mogelijkheid waarmee de client een synchronisatiebericht moet verzenden vóór het volgende begininterval.

>[!NOTE]
>
>Deze gebruiksregel wordt ondersteund door Primetime DRM-clients versie 3.0 of hoger. Het gedrag bij oudere clients is afhankelijk van de minimale clientversie die door de licentieserver wordt ondersteund.
