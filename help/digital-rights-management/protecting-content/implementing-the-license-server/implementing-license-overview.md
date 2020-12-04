---
seo-title: Overzicht van licentieserver
title: Overzicht van licentieserver
uuid: 8c62376b-b159-4297-9322-75d62947e84e
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15
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

Zie *Adobe Primetime DRM API Reference* voor meer informatie over de Java API.
