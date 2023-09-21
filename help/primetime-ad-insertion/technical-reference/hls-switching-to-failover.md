---
title: HLS-speler helpen overschakelen naar failover/back-upstreams
description: Apple HLS-stapel ondersteunt de overschakeling op failover-/back-upstreams als deze geen streams van de primaire set kan ophalen. Voor Apple HLS-apparaten kunt u, om failover te vergemakkelijken, een signaal geven voor een manifestserver om primaire en failover-streams die in de hoofdafspeellijst zijn geïdentificeerd, te behandelen als gesplitste sets (met hun eigen UUID's).
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# HLS-speler helpen overschakelen naar failover/back-upstreams {#facilitating-hls-player-switching-to-failover-backup-streams}

Apple HLS-stapel ondersteunt de overschakeling op failover-/back-upstreams als deze geen streams van de primaire set kan ophalen. Voor Apple HLS-apparaten kunt u, om failover te vergemakkelijken, een signaal geven voor een manifestserver om primaire en failover-streams die in de hoofdafspeellijst zijn geïdentificeerd, te behandelen als gesplitste sets (met hun eigen UUID&#39;s).

Als u de overschakeling naar failover- of back-upstreams op Apple HLS-apparaten wilt vergemakkelijken, kunt u de `ptfailover` in de Bootstrap-URL. Als u deze parameter verstrekt, zal de manifestserver afzonderlijke playbackzittingen (die de geplaatste advertenties) voor elke failoverreeks bepalen.

## Details

Hoe SSAI HLS die aan failover/steun overschakelen behandelt wanneer u omvat `ptfailover=true` in het verzoek om Bootstrap:

* Wanneer een hoofdafspeellijst primaire en back-upsets bevat:

   * De manifestserver identificeert AV stroom URLs voor verschillende failover reeksen gebruikend `BANDWIDTH` en de parseervolgorde van URL&#39;s van AV-stream. Er worden afzonderlijke interne afspeelsessies gemaakt (geïdentificeerd door afzonderlijke UUID&#39;s) en er worden stroom-URL&#39;s gemaakt die verwijzen naar manifestservers met verschillende UUID&#39;s die verschillende afspeelsessies identificeren.
   * De manifestserver identificeert I-Frame stroom URLs voor verschillende failover reeksen gebruikend de aanpassing `RESOLUTION` en de parseervolgorde van URL&#39;s van I-Frame-streams. SSAI gebruikt UUIDs die de bijbehorende stromen AV voor I-Frame stroom URLs identificeren die aan SSAI richten.
   * Voor deze functie ondersteunt de manifestserver alleen `EXT-X-MEDIA` groepen zonder URI-kenmerken in de hoofdafspeellijst.
   * De manifestserver ontdekt een 404 foutenreactie van een CDN met een `X-Object-Too-Old: true` en behoudt de statuscode en de header wanneer die reactie naar de speler wordt verzonden.

* Pre-roll advertenties worden slechts toegevoegd aan de primaire reeks; zij worden volledig onbruikbaar gemaakt in de failoverreeksen om het even welke fout en/of gedupliceerde pre-roladvertenties te vermijden wanneer de speler aan failoverstromen schakelt.
