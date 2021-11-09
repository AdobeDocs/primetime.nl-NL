---
title: Opmerkingen bij de release PTAI 21.11.1
description: In de PTAI-release wordt beschreven wat nieuw of gewijzigd is, wat de opgeloste en bekende problemen zijn in Primetime Ad Insertion in 2021.
exl-id: 39a05f6d-431a-4416-81b1-21d82c0dbd69
source-git-commit: b58fea35be528c4c030eab39fde9dd642d90cb58
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# Opmerkingen bij de release Primetime Ad Insertion 21.11.1

Opmerkingen bij de release van Primetime Ad Insertion 21.xx.x beschrijven wat nieuw of gewijzigd is, problemen die zijn opgelost en bekende problemen in Primetime Ad Insertion 2021.

## Nieuw in PTAI 21.11.1

Wanneer: Dinsdag 9 november 2021, 13.30 tot 4.30 uur Oosterse tijd

* [!UICONTROL EXT-X-IMAGE-STREAM-INF] is nu configureerbaar per streek.

## Verbeteringen en correcties in vorige releaseversies

### Versie 21.10.1

Wanneer: Dinsdag 12 oktober 2021, 19.45 - 13.45 uur Oosterse tijd

* Consolidated servers, removed non-production and non-useful servers.

### Primetime Ad Insertion Maintenance release

Wanneer: Dinsdag 28 september 2021, van 5.00 tot 6.00 uur Oosterse tijd

* Updates to Load Balancer stack from AWS&#39;s Elastic Load Balancer to AWS&#39;s Application Load Balancer for enhanced functionality and scalability. These Load Balancers are used to route ad request traffic to Auditude backend from the Ad Insertion layer (SSAI/CSAI).

### Versie 21.9.1

Wanneer: Dinsdag 7 september 2021, 2.30 uur &#39;s middags tot 5.30 uur &#39;s morgens

* Updates voor infrastructuurcomponenten achter de bemiddelings- en rapportagecomponenten van Primetime Ad Insertion (Primetime Ads GUI).

### Version 21.8.1

When: Tuesday, August 24, 2021 from 2:00 AM to 05:00 AM Eastern Time

* Added support for DASH Live/ Linear streams (VOD is already supported).

### Version 21.5.1

Wanneer: Woensdag 26 mei 2021, 15.30 - 06.30 uur Oosterse tijd

**Wijzigingen**

* Toegevoegde ondersteuning voor afgekeurd segmentatietype 0x01 (UPID) voor op SCTE gebaseerde actiefindelingen.

* Nieuwe telemetrie toegevoegd voor aanstaande dashboardwijzigingen.

### Versie 21.4.1

**Wanneer:** Donderdag 22 april 2021, van 2.00 tot 17.00 uur Oosterse tijd

**Wijzigingen**

* Beperking van sessieverzoeken wordt ingeschakeld om te beschermen tegen mogelijke DDOS-aanvallen. De zittingen zullen tot 10 verzoeken per seconde, met een maximum van 100 een rij gevormde verzoeken worden beperkt. We verwachten geen gevolgen voor spelers die zich gedragen volgens de HLS/DASH-specificaties.

* Andere verbeteringen op het gebied van onderhoud en beveiliging

### Versie 21.2.2

**Wanneer:** Dinsdag 23 februari 2021, 13:00 - 04:00 uur Oosterse tijd

**Changes**

* Toegevoegde ondersteuning voor EXT-X-IMAGE-STREAM-INF-streaminvoeging/synchronisatie in HLS-streams. De eigenschap wordt toegelaten door een server-zijconfiguratie. Neem contact op met de vertegenwoordiger van uw technische account om deze functie in te schakelen.

### Versie 21.2.1

**Wanneer:** Woensdag 3 februari 2021, 13:00 - 04:00 uur Oosterse tijd

**Wijzigingen**

* Toegevoegde ondersteuning voor DASH-uitvoeroptimalisatie: op tijd gebaseerde consolidatie van knooppunten.

### Versie 21.1.2

**Wanneer:** Dinsdag 19 januari 2021, 12.30 tot 8.30 uur &#39;s morgens

**Changes**

* Onderhoudsupdate: Upgrade van Primetime Ad Insertion backend-geheugenclusters.

### Versie 21.1.1

**Wanneer:** Woensdag 13 januari 2021, 13.00 tot 4.00 uur Oosterse tijd

**Wijzigingen**

* Toegevoegde steun voor filiaal beschikbaar voor op SCTE35-Gebaseerde richtsnoerformaten.
