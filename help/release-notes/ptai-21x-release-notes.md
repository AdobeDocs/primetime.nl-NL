---
title: Opmerkingen bij de release PTAI 21.11.1
description: In de PTAI-release wordt beschreven wat nieuw of gewijzigd is, wat de opgeloste en bekende problemen zijn in Primetime Ad Insertion in 2021.
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# Opmerkingen bij de release Primetime Ad Insertion 21.11.1

Opmerkingen bij de release van Primetime Ad Insertion 21.xx.x beschrijven wat nieuw of gewijzigd is, problemen die zijn opgelost en bekende problemen in Primetime Ad Insertion 2021.

## Nieuw in PTAI 21.11.1

Wanneer: Dinsdag 9 november 2021 van 1.30 tot 04.30 uur Oosterse tijd

* [!UICONTROL EXT-X-IMAGE-STREAM-INF] is nu configureerbaar per streek.

* Roku Trick Play wordt volledig ondersteund.

## Verbeteringen en correcties in vorige releaseversies

### Versie 21.10.1

Als: Dinsdag 12 oktober 2021, 19.45 - 13.45 uur Oost Tijd

* Geconsolideerde servers, verwijderde niet-productie en niet-bruikbare servers.

### Primetime Ad Insertion Maintenance release

Als: Dinsdag 28 september 2021, van 5.00 tot 6.00 uur Oost Tijd

* Updates voor Load Balancer-stapel van AWS Elastic Load Balancer naar AWS Application Load Balancer voor verbeterde functionaliteit en schaalbaarheid. Deze Balancers van de Lading worden gebruikt om verkeer aan Auditude achterste van de laag van de Ad Insertion (SSAI/CSAI) te leiden en te verzoeken.

### Versie 21.9.1

Wanneer: Dinsdag 7 september 2021 van 2.30 uur tot 05.30 uur Oosterse tijd

* Updates voor infrastructuurcomponenten achter de bemiddelings- en rapportagecomponenten van Primetime Ad Insertion (Primetime Ads GUI).

### Versie 21.8.1

Wanneer: Dinsdag 24 augustus 2021 van 2.00 tot 05.00 uur Oosterse tijd

* Toegevoegde ondersteuning voor live/lineaire DASH-streams (VOD wordt al ondersteund).

### Versie 21.5.1

Wanneer: woensdag 26 mei 2021 van 3.30 tot 06.30 uur &#39;s morgens

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

**Wijzigingen**

* Toegevoegde ondersteuning voor EXT-X-IMAGE-STREAM-INF-streaminvoeging/synchronisatie in HLS-streams. De eigenschap wordt toegelaten door een server-zijconfiguratie. Neem contact op met de vertegenwoordiger van uw technische account om deze functie in te schakelen.

### Versie 21.2.1

**Wanneer:** Woensdag 3 februari 2021, 13:00 - 04:00 uur Oosterse tijd

**Wijzigingen**

* Toegevoegde ondersteuning voor DASH-uitvoeroptimalisatie: tijdgebaseerde consolidatie van knooppunten.

### Versie 21.1.2

**Wanneer:** Dinsdag 19 januari 2021, 12.30 tot 8.30 uur &#39;s morgens

**Wijzigingen**

* Onderhoudsupdate: upgrade van Primetime Ad Insertion backend-geheugenclusters.

### Versie 21.1.1

**Wanneer:** Woensdag 13 januari 2021, 13.00 tot 4.00 uur Oosterse tijd

**Wijzigingen**

* Toegevoegde steun voor filiaal beschikbaar voor op SCTE35-Gebaseerde richtsnoerformaten.
