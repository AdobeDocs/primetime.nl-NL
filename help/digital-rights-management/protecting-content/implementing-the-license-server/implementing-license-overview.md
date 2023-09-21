---
title: Overzicht van licentieserver
description: Overzicht van licentieserver
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---

# Overzicht {#license-server-overview}

Voordat u licenties kunt verlenen aan clients, moet u een Adobe Primetime DRM-licentieserver implementeren. De licentieserver gebruikt de Primetime DRM SDK om een aantal taken uit te voeren.

Een licentieserver implementeren:

* Verwerk verificatieaanvragen als gebruikersbenaming-/wachtwoordverificatie wordt ondersteund.
* Procesvergunningsaanvragen
* Verzoeken naar serverversie ophalen van proces—Alle servers moeten ondersteuning voor dit type aanvraag implementeren.
* Registratieaanvragen voor domeinen verwerken—Alleen nodig bij het implementeren van een domeinserver.
* Registratieaanvragen voor domeinen verwerken; alleen nodig bij het implementeren van een domeinserver.
* Processynchronisatie: alleen nodig als voor licenties de synchronisatievereisten zijn opgegeven.

Bovendien moet de server bedrijfslogica voor het voor authentiek verklaren van gebruikers verstrekken, bepalend of de gebruikers worden gemachtigd om inhoud te bekijken, en naar keuze vergunningsgebruik te volgen.

Zie *Adobe Primetime DRM API Reference* voor meer informatie over de Java API.
