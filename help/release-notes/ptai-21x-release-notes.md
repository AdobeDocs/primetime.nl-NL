---
title: Opmerkingen bij de release PTAI 21.5.1
description: In de PTAI-release wordt beschreven wat nieuw of gewijzigd is, wat de opgeloste en bekende problemen zijn in Primetime Ad Insertion in 2021.
exl-id: 39a05f6d-431a-4416-81b1-21d82c0dbd69
source-git-commit: 02e43df4d9b58b4b1ed8fdbc086771bbf3380c0f
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---

# Opmerkingen bij de release Primetime Ad Insertion 21.5.1

Opmerkingen bij de release van Primetime Ad Insertion 21.x.x beschrijven wat nieuw of gewijzigd is, problemen die zijn opgelost en bekende problemen in Primetime Ad Insertion 2021.

## Nieuw in PTAI 21.5.1

Wanneer:  Woensdag 26 mei 2021, 15.30 - 06.30 uur OOSTEN

* Toegevoegde ondersteuning voor afgekeurd segmentatietype 0x01 (UPID) voor op SCTE gebaseerde actiefindelingen.
* Nieuwe telemetrie toegevoegd voor aanstaande dashboardwijzigingen.

## Verbeteringen en correcties in vorige releaseversies

### Versie 21.4.1

**Als:** donderdag, 22 april 2021, van 2.00 uur tot 17.00 uur OOSTEN

**Wijzigingen**

* Beperking van sessieverzoeken wordt ingeschakeld om te beschermen tegen mogelijke DDOS-aanvallen. De zittingen zullen tot 10 verzoeken per seconde, met een maximum van 100 een rij gevormde verzoeken worden beperkt. We verwachten geen gevolgen voor spelers die zich gedragen volgens de HLS/DASH-specificaties.
* Andere verbeteringen op het gebied van onderhoud en beveiliging

### Versie 21.2.2

**Wanneer:** Dinsdag, 23 februari, 2021 van 1:00 AM aan 04:00 Oost Tijd

**Wijzigingen**

* Toegevoegde ondersteuning voor EXT-X-IMAGE-STREAM-INF-streaminvoeging/synchronisatie in HLS-streams. De eigenschap wordt toegelaten door een server-zijconfiguratie. Neem contact op met de vertegenwoordiger van uw technische account om deze functie in te schakelen.

### Versie 21.2.1

**Als:** woensdag, 3 februari 2021 van 13.00 tot 04.00 uur Oosterse tijd

**Wijzigingen**

* Toegevoegde ondersteuning voor DASH-uitvoeroptimalisatie: op tijd gebaseerde consolidatie van knooppunten.

### Versie 21.1.2

**Wanneer:** Dinsdag, 19 januari 2021 van 12.30 uur tot 8.30 uur &#39;s morgens

**Wijzigingen**

* Onderhoudsupdate: Upgrade van Primetime Ad Insertion backend-geheugenclusters.

### Versie 21.1.1

**Wanneer:** Woensdag, 13 januari 2021 van 01:00 uur tot 04:00 uur Oosterse tijd

**Wijzigingen**

* Toegevoegde steun voor filiaal beschikbaar voor op SCTE35-Gebaseerde richtsnoerformaten.
