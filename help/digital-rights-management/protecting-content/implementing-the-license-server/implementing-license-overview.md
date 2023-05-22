---
title: Overzicht van licentieserver
description: Overzicht van licentieserver
copied-description: true
exl-id: 101d9f63-b9b9-4281-a069-8c66427b34cb
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---

# Overzicht {#license-server-overview}

Voordat u licenties kunt verlenen aan clients, moet u een Adobe Primetime DRM-licentieserver implementeren. De licentieserver gebruikt de Primetime DRM SDK om een aantal taken uit te voeren.

Een licentieserver implementeren:

* Verwerk verificatieaanvragen als gebruikersbenaming-/wachtwoordverificatie wordt ondersteund.
* Procesvergunningsaanvragen
* Verzoeken van de Versie van de Server van het proces krijgen-Alle servers moeten steun voor dit type van verzoek uitvoeren.
* Registratieaanvragen voor domeinen verwerken—Alleen nodig bij het implementeren van een domeinserver.
* Registratieaanvragen voor domeinen verwerken; alleen nodig bij het implementeren van een domeinserver.
* Processynchronisatie: alleen nodig als voor licenties de synchronisatievereisten zijn opgegeven.

Bovendien moet de server bedrijfslogica voor het voor authentiek verklaren van gebruikers verstrekken, bepalend of de gebruikers worden gemachtigd om inhoud te bekijken, en naar keuze vergunningsgebruik te volgen.

Zie *Adobe Primetime DRM API-naslaggids* voor meer informatie over de Java API.
