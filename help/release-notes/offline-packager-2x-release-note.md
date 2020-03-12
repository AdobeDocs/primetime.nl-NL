---
title: Release 2.x van de Offline Packager van Primetime
seo-title: Release 2.x van de Offline Packager van Primetime
description: Nieuw in de versies van Primetime Offline Packager 2.1 en 2.3.1
seo-description: Nieuw in de versies van Primetime Offline Packager 2.1 en 2.3.1
uuid: 01926a10-890d-477d-b832-e22847d957e0
contentOwner: asgupta
products: SG_PRIMETIME
topic-tags: release-notes
discoiquuid: 933a0711-846a-4bb7-bf51-b300822a93d4
translation-type: tm+mt
source-git-commit: e644e8497e118e2d03e72bef727c4ce1455d68d6

---


# De versies van de Offline Packager van Primetime {#primetime-offline-packager-x-releases}

Nieuw in de versies van Primetime Offline Packager 2.1 en 2.3.1

## Nieuw in Primetime Offline Packager 2.3.1 (okt 2016) {#what-s-new-in-primetime-offline-packager-oct}

De release schakelt het profiel Op aanvraag in voor MPEG-DASH, voegt ondersteuning toe voor de `validate` optie voor het gereedschap PlaylistCreator en bevat enkele belangrijke correcties voor de hieronder vermelde scenario&#39;s voor multi-DRM.

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
| PTPUB-990 | Voor DASH schrijft Offline Packager geen verpakkingshulpprogramma dat IV wordt gegenereerd naar schijf wanneer de parameters `log_vi` &amp; `iv_out_path` worden opgegeven. |
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

1. Download de Java SE-software van de [Oracle-site](https://www.oracle.com/technetwork/java/javase/downloads/index.html) en volg de installatie-instructies.
1. Extraheer het archiefbestand Adobe Primetime Offline Packager 2.3.1 genaamd `PrimetimeOfflinePackager-2-3-1-b47-10142016.zip` naar de schijf.

### Het vormen van Offline Packager 2.3.1 {#configuring-the-offline-packager}

De configuratie-instructies zijn beschikbaar in de gids Aan de slag met Primetime Offline Packager op [https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html)

## Nieuw in Primetime Offline Packager 2.1 (juli 2015) {#what-s-new-in-primetime-offline-packager-july}

Ondersteuning voor PlayReady BuyDRM (voor DASH). Raadpleeg de Help-documentatie [die hier](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html)beschikbaar is voor meer informatie.

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

### Offline Packager 2.1 installeren {#installing-offline-packager}

1. Download de Java SE-software van de [Oracle-site](https://www.oracle.com/technetwork/java/javase/downloads/index.html) en volg de installatie-instructies.
1. Pak de `Adobe Primetime - Offline Packager 2.1.0 archive file, PrimetimeOfflinePackager-2-1-0-b15-07082015.zip`schijf uit.

### Het vormen van Offline Packager 2.1 {#configuring-the-offline-packager-1}

Verwijs naar het Aan de slag zijnde document van de Offline Packager van Primetime voor de configuratiedetails beschikbaar hier [https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html)

## Nuttige bronnen {#helpful-resources}

* Zie de volledige Help-documentatie op de pagina [Adobe Primetime Learn &amp; Support](https://helpx.adobe.com/support/primetime.html) .