---
seo-title: Voorvertoning van licentie
title: Voorvertoning van licentie
uuid: 3069aa16-5bf3-4af6-801c-ad823530d7eb
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---


# Voorvertoning licentie{#license-preview}

De client kan een aanvraag voor een voorvertoning van een licentie verzenden. Dit houdt in dat de toepassing een voorvertoning kan uitvoeren voordat de gebruiker wordt gevraagd de inhoud te kopen om te bepalen of de computer van de gebruiker daadwerkelijk voldoet aan alle criteria die vereist zijn voor het afspelen.

*`License preview`* verwijst naar de mogelijkheid van een klant om een voorvertoning van de licentie te bekijken (om te zien welke rechten de licentie toestaat) in plaats van een voorvertoning van de inhoud te bekijken (een klein gedeelte van de inhoud bekijken voordat wordt besloten om te kopen). Enkele parameters die uniek zijn voor elke computer zijn: beschikbare uitvoer en hun beveiligingsstatus, de beschikbare runtime/DRM-versie en het beveiligingsniveau van de DRM-client. In de modus voor voorvertoning van licentie kan de runtime/DRM-client de bedrijfslogica van de licentieserver testen en informatie teruggeven aan de gebruiker zodat deze een geïnformeerde beslissing kan nemen. De client kan dus zien hoe een geldige licentie eruitziet, maar ontvangt de sleutel voor het decoderen van de inhoud niet. Ondersteuning voor licentievoorvertoning is optioneel en alleen nodig als u een aangepaste client implementeert die deze functionaliteit gebruikt.

Om te bepalen of de cliënt een voorproefverzoek of een verzoek van de vergunningsaanschaf heeft verzonden, vraag `LicenseRequestMessage.getRequestPhase()`en vergelijk het met `LicenseRequestMessage.RequestPhase.Acquire`
