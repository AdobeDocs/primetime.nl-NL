---
title: Release 2.x van de Offline Packager van Primetime
description: Nieuw in de versies van Primetime Offline Packager 2.1 en 2.3.1
contentOwner: asgupta
products: SG_PRIMETIME
topic-tags: release-notes
translation-type: tm+mt
source-git-commit: b33240bf1b42b80389cd95a7ae4d3f85185a2d32
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---


# Release {#primetime-offline-packager-x-releases} van primetime Offline Packager

Nieuw in de versies van Primetime Offline Packager 2.1 en 2.3.1

## Nieuw in Primetime Offline Packager 2.3.1 (okt 2016) {#what-s-new-in-primetime-offline-packager-oct}

De release schakelt het profiel Op aanvraag in voor MPEG-DASH, voegt ondersteuning toe voor de optie `validate` voor het gereedschap PlaylistCreator en bevat enkele belangrijke correcties voor de hieronder vermelde scenario&#39;s voor multi-DRM.

| **Uitgiftenummer** | **Beschrijving** |
|---|---|
| PTPUB-985 | HLS AXS en Sample-AES werken niet voor pakketgestuurde sleutel |
| PTPUB-973 | Opgeloste fout in versleutelingsalgoritme voor bepaalde specifieke Widevine-inhoud |
| PTPUB-964 | CENC-codering verbroken voor bepaalde mediatypen op bepaalde speler - Android TVSDK. |
| PTPUB-954 | Sample-AES-versleuteling omzeilt standaard AXS DRM / Fout gegenereerd met levering via externe sleutel ingeschakeld. |
| PTPUB-951 | Offline packager genereert geen uitzondering wanneer key_file_path niet met Windows is opgegeven. In plaats daarvan wordt NPE gegenereerd. |

De meest recente documentatie van Primetime Packagers is beschikbaar op [https://help.adobe.com/en_US/primetime/api/packagers/index.html](https://help.adobe.com/en_US/primetime/api/packagers/index.html).

### Bekend probleem in versie 2.3.1 {#known-issue-in-version}

Deze release bevat de volgende problemen.

| **Uitgiftenummer** | **Beschrijving** |
|---|---|
| PTPUB-1005 | PlaylistCreator verstrekt correcte URL voor het .pssh dossier in het definitieve vastgestelde niveau .mpd dossier niet dat voor AXS DRM wordt geproduceerd. |
| PTPUB-1001 | PlaylistCreator moet een fout genereren wanneer een leeg pad wordt opgegeven via de parameter in_path |
| PTPUB-990 | Voor DASH schrijft Offline Packager geen pakketprogramma dat IV wordt gegenereerd naar schijf wanneer de parameters `log_vi` &amp; `iv_out_path` worden opgegeven. |
| PTPUB-980 | Wanneer het configuratiedossier voor verpakking wordt gebruikt, verwijdert het gebruiken van de parameter `key_url` niet de aanhalingstekens uit de verstrekte input. |

## Adobe Primetime Offline Packager 2.3.1 {#adobe-primetime-offline-packager}

### Minimale systeemvereisten {#minimum-system-requirements}

Ondersteunde besturingssystemen

* Linux CentOS 6.3 64-bits

Hardwarevereisten

* 3,2 GHz Intel® Pentium® 4-processor (dual Intel Xeon® of sneller aanbevolen)

* 64-bits besturingssystemen: 4 GB RAM (8 GB aanbevolen)

* Vaste schijf

(Schijf-SAS): Minimaal 10 GB met 7.500 rpm

(Schijf-SSD): 400 MBps lees-/schrijfsnelheid

(NAS): 1 GB toegewezen koppeling

Softwarevereisten

* Oracle Java SE 1.8 of hoger

### Adobe Primetime Offline Packager 2.3.1 {#adobe-primetime-offline-packager-1}

1. Download de Java SE-software van [Oracle site](https://www.oracle.com/technetwork/java/javase/downloads/index.html) en volg de installatie-instructies.
1. Extraheer het archiefbestand `PrimetimeOfflinePackager-2-3-1-b47-10142016.zip` van Adobe Primetime Offline Packager 2.3.1 naar de schijf.

### Het vormen van Offline Packager 2.3.1 {#configuring-the-offline-packager}

De configuratieinstructies zijn beschikbaar in de gids Aan de slag van het Begeleidende Offline Packager van Primetime bij [https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html)

## Nieuw in Primetime Offline Packager 2.1 (juli 2015) {#what-s-new-in-primetime-offline-packager-july}

Ondersteuning voor PlayReady BuyDRM (voor DASH). Voor details, verwijs naar de Documentatie van de Hulp [hier beschikbaar](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html).

De offlineverpakker is ook uitgebreid.

PTPUB-780 Toegevoegde ondersteuning voor EXT-X-START-tag

## Nieuw in Primetime Offline Packager 2.0 (juni 2015) {#what-s-new-in-primetime-offline-packager-june}

Er is ondersteuning voor DASH-uitvoer toegevoegd. Raadpleeg de productdocumentatie [hier](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html) voor meer informatie.

De volgende problemen zijn ook opgelost in deze release.

* PTPUB-783 Offline Packager kan nu lege WebVTT-bestanden verwerken.
* PTPUB- 781 Artefacten in HLS-uitvoer op Chrome wanneer bepaalde getranscodeerde MP4-elementen zijn verpakt met offlinepakketprogramma om MBR-uitvoer te produceren.

## Adobe Primetime Offline Packager 2.1 {#adobe-primetime-offline-packager-2}

### Minimale systeemvereisten {#minimum-system-requirements-1}

**Ondersteunde besturingssystemen**

* Linux CentOS 6.3 64-bits

**Hardwarevereisten**

* 3,2 GHz Intel® Pentium® 4-processor (dual Intel Xeon® of sneller aanbevolen)

* 64-bits besturingssystemen: 4 GB RAM (8 GB aanbevolen)

* 1 Gb Ethernet-kaart aanbevolen (meerdere netwerkkaarten en 10 Gb ook ondersteund)

* Vaste schijf

   * (Schijf-SAS): Minimaal 10 GB met 7.500 rpm
   * (Schijf-SSD): 400 MBps lees-/schrijfsnelheid
   * (NAS): 1 GB toegewezen koppeling

**Softwarevereisten**

* Oracle Java SE 1.8 of hoger

### Offline Packager 2.1 {#installing-offline-packager} installeren

1. Download de Java SE-software van [Oracle site](https://www.oracle.com/technetwork/java/javase/downloads/index.html) en volg de installatie-instructies.
1. Pak `Adobe Primetime - Offline Packager 2.1.0 archive file, PrimetimeOfflinePackager-2-1-0-b15-07082015.zip` uit op de schijf.

### Het vormen Offline Packager 2.1 {#configuring-the-offline-packager-1}

Verwijs naar het Voorkeur Offline Packager Getting Started document voor de configuratiedetails beschikbaar hier [https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html)

## Nuttige bronnen {#helpful-resources}

* Zie de volledige Help-documentatie op de pagina [Adobe Primetime Learn &amp; Support](https://helpx.adobe.com/support/primetime.html).