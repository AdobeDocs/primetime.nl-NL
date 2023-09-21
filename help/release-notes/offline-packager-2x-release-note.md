---
title: Release 2.x van de Offline Packager van Primetime
description: Nieuw in de versies van Primetime Offline Packager 2.1 en 2.3.1
contentOwner: asgupta
products: SG_PRIMETIME
topic-tags: release-notes
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---

# De versies van de Offline Packager van Primetime {#primetime-offline-packager-x-releases}

Nieuw in de versies van Primetime Offline Packager 2.1 en 2.3.1

## Nieuw in Primetime Offline Packager 2.3.1 (okt 2016)  {#what-s-new-in-primetime-offline-packager-oct}

Met deze release wordt Profiel op aanvraag ingeschakeld voor MPEG-DASH. Daarnaast wordt ondersteuning geboden voor de `validate` voor het gereedschap PlaylistCreator en bevat enkele belangrijke correcties voor multi-DRM-scenario&#39;s die hieronder worden vermeld.

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
| PTPUB-980 | Wanneer het configuratiedossier voor verpakking wordt gebruikt, gebruikend de parameter `key_url` worden de aanhalingstekens niet van de opgegeven invoer verwijderd. |

## Adobe Primetime Offline Packager 2.3.1 {#adobe-primetime-offline-packager}

### Minimale systeemvereisten {#minimum-system-requirements}

Ondersteunde besturingssystemen

* Linux CentOS 6.3 64-bits

Hardwarevereisten

* 3,2 GHz Intel® Pentium® 4-processor (dual Intel Xeon® of sneller aanbevolen)

* 64-bits besturingssystemen: 4 GB RAM (8 GB aanbevolen)

* Vaste schijf

(Schijf-SAS): minimaal 10 GB met 7.500 rpm

(Schijf-SSD): 400 MBps lees-/schrijfsnelheid

(NAS): 1 GB toegewezen koppeling

Softwarevereisten

* Oracle Java SE 1.8 of hoger

### Adobe Primetime Offline Packager 2.3.1 {#adobe-primetime-offline-packager-1}

1. Download de Java SE-software van de [Oracle](https://www.oracle.com/technetwork/java/javase/downloads/index.html) en volgt u de installatie-instructies.
1. Het Adobe Primetime Offline Packager 2.3.1-archiefbestand met de naam `PrimetimeOfflinePackager-2-3-1-b47-10142016.zip` naar de schijf.

### Het vormen van Offline Packager 2.3.1 {#configuring-the-offline-packager}

De configuratieinstructies zijn beschikbaar in de gids Aan de slag van het Pakket van de Offline Primetime bij [https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html)

## Nieuw in Primetime Offline Packager 2.1 (juli 2015) {#what-s-new-in-primetime-offline-packager-july}

Ondersteuning voor PlayReady BuyDRM (voor DASH). Raadpleeg de Help-documentatie voor meer informatie [hier beschikbaar](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html).

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

   * (Schijf-SAS): minimaal 10 GB met 7.500 rpm
   * (Schijf-SSD): 400 MBps lees-/schrijfsnelheid
   * (NAS): 1 GB toegewezen koppeling

**Softwarevereisten**

* Oracle Java SE 1.8 of hoger

### Offline Packager 2.1 installeren {#installing-offline-packager}

1. Download de Java SE-software van de [Oracle](https://www.oracle.com/technetwork/java/javase/downloads/index.html) en volgt u de installatie-instructies.
1. Het gereedschap `Adobe Primetime - Offline Packager 2.1.0 archive file, PrimetimeOfflinePackager-2-1-0-b15-07082015.zip`, naar uw schijf.

### Het vormen van Offline Packager 2.1 {#configuring-the-offline-packager-1}

Verwijs het Voorkeur Offline Packager die - hier beschikbaar configuratiedetails krijgt [https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html)

## Nuttige bronnen {#helpful-resources}

* Zie de volledige Help-documentatie op [Adobe Primetime - Meer informatie en ondersteuning](https://helpx.adobe.com/support/primetime.html) pagina.
