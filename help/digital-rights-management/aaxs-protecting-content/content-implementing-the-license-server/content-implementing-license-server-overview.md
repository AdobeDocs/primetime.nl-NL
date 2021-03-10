---
title: Overzicht
description: Overzicht
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---


# Overzicht{#overview}

Als u licenties aan klanten wilt verlenen, moet u een Adobe Access-licentieserver implementeren. De licentieserver gebruikt de Adobe® Access™ SDK om de volgende taken uit te voeren:

* Verwerk verificatieaanvragen als gebruikersbenaming-/wachtwoordverificatie wordt ondersteund.
* Procesvergunningsaanvragen
* Verzoeken om serverversie ophalen van proces — Alle servers moeten ondersteuning voor dit type aanvraag implementeren.
* Registratieaanvragen voor procesdomeinen — Alleen nodig bij implementatie van een domeinserver.
* Registratieverzoeken voor procesdomeinen — Alleen nodig bij implementatie van een domeinserver.
* Processynchronisatie: alleen nodig als voor licenties de synchronisatievereisten zijn opgegeven.

Bovendien moet de server bedrijfslogica voor het voor authentiek verklaren van gebruikers verstrekken, bepalend of de gebruikers worden gemachtigd om inhoud te bekijken, en naar keuze vergunningsgebruik te volgen.

Zie *Referentie voor API voor Adobe Access* voor meer informatie over de Java API die in dit hoofdstuk wordt besproken.
