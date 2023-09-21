---
title: Gebruiksregels
description: Gebruiksregels
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 0%

---

# Gebruiksregels {#usage-rules}

De volgende onderwerpen beschrijven de gebruiksregels die u in een beleid van Adobe Primetime DRM kunt specificeren.

## Gebruikersverificatie {#user-authentication}

Met gebruikersverificatie wordt opgegeven of een referentie, zoals gebruikersnaam en wachtwoord, vereist is om een licentie te verkrijgen. Als geverifieerde (op identiteit gebaseerde) licenties zijn opgegeven, wordt de server ~~_authenticates_~~ de gebruiker voordat hij een licentie afgeeft.

Voorbeeld van gebruik: voor een abonnementenservice moet mogelijk een gebruikersnaam en wachtwoord worden ingevoerd voordat een inhoudslicentie wordt uitgegeven. Een dvd of Blu-ray-schijf met digitale kopie kan een code of een ander token leveren als betalingsbewijs, dat kan worden ingewisseld voor een elektronische download.
