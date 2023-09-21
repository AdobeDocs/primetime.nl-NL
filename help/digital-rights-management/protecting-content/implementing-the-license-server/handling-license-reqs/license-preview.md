---
title: Voorvertoning van licentie
description: Voorvertoning van licentie
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# Voorvertoning van licentie{#license-preview}

De client kan een aanvraag voor een voorvertoning van een licentie verzenden. Dit houdt in dat de toepassing een voorvertoning kan uitvoeren voordat de gebruiker wordt gevraagd de inhoud te kopen om te bepalen of de computer van de gebruiker daadwerkelijk voldoet aan alle criteria die vereist zijn voor het afspelen.

*`License preview`* verwijst naar de mogelijkheid van een klant om een voorvertoning van de licentie te bekijken (om te zien welke rechten de licentie toestaat) in plaats van een voorvertoning van de inhoud te bekijken (een klein gedeelte van de inhoud bekijken voordat wordt besloten om te kopen). Enkele parameters die uniek zijn voor elke computer zijn: beschikbare uitvoer en de beveiligingsstatus, de beschikbare runtime/DRM-versie en het beveiligingsniveau van de DRM-client. In de modus voor voorvertoning van licentie kan de runtime/DRM-client de bedrijfslogica van de licentieserver testen en informatie teruggeven aan de gebruiker zodat deze een geïnformeerde beslissing kan nemen. De client kan dus zien hoe een geldige licentie eruitziet, maar ontvangt de sleutel voor het decoderen van de inhoud niet. Ondersteuning voor licentievoorvertoning is optioneel en alleen nodig als u een aangepaste client implementeert die deze functionaliteit gebruikt.

Om te bepalen of de cliënt een voorproefverzoek of een verzoek van de vergunningsaanschaf heeft verzonden, vraag `LicenseRequestMessage.getRequestPhase()`en vergelijk het met `LicenseRequestMessage.RequestPhase.Acquire`
