---
description: De stapel van Apple HLS steunt omschakeling aan failover/reservestromen als het geen stromen van de primaire reeks kan terugwinnen. Voor Apple HLS-apparaten kunt u, om failover te vergemakkelijken, een signaal geven voor een manifestserver om primaire en failover-streams die in de master afspeellijst worden geïdentificeerd, te behandelen als gesplitste sets (met hun eigen UUID's).
title: HLS-speler helpen overschakelen naar failover-/back-upstreams
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---


# HLS-speler helpen overschakelen naar failover/back-upstreams {#facilitating-hls-player-switching-to-failover-backup-streams}

De stapel van Apple HLS steunt omschakeling aan failover/reservestromen als het geen stromen van de primaire reeks kan terugwinnen. Voor Apple HLS-apparaten kunt u, om failover te vergemakkelijken, een signaal geven voor een manifestserver om primaire en failover-streams die in de master afspeellijst worden geïdentificeerd, te behandelen als gesplitste sets (met hun eigen UUID&#39;s).

Als u de overstap naar failover- of back-upstreams op Apple HLS-apparaten wilt vergemakkelijken, kunt u de parameter `ptfailover` opgeven in de URL van Bootstrap. Als u deze parameter verstrekt, zal de manifestserver afzonderlijke playbackzittingen (die de geplaatste advertenties) voor elke failoverreeks bepalen.

## Details

Hoe SSAI HLS die aan failover/steun schakelen behandelt wanneer u `ptfailover=true` in het verzoek van Bootstrap omvat:

* Wanneer een master afspeellijst primaire en back-upsets bevat:

   * De manifestserver identificeert AV stroom URLs voor verschillende failoverreeksen gebruikend het `BANDWIDTH` attribuut en de parseringsorde van AV stroom URLs. Er worden afzonderlijke interne afspeelsessies gemaakt (geïdentificeerd door afzonderlijke UUID&#39;s) en er worden stroom-URL&#39;s gemaakt die verwijzen naar manifestservers met verschillende UUID&#39;s die verschillende afspeelsessies identificeren.
   * De manifestserver identificeert I-Frame stroom URLs voor verschillende failoverreeksen gebruikend het passende `RESOLUTION` attribuut en de parseerorde van I-Frame stroom URLs. SSAI gebruikt UUIDs die de bijbehorende stromen AV voor I-Frame stroom URLs identificeren die aan SSAI richten.
   * Voor deze functie ondersteunt de manifestserver alleen `EXT-X-MEDIA` groepen zonder URI-kenmerken in de master afspeellijst.
   * De manifestserver ontdekt een 404 foutenreactie van een CDN met een `X-Object-Too-Old: true` kopbal, en bewaart de statuscode en de kopbal wanneer het verzenden van die reactie naar de speler.

* Pre-roll advertenties worden slechts toegevoegd aan de primaire reeks; zij zijn volledig gehandicapt in de failoverreeksen om het even welke fout en/of gedupliceerde pre-roladvertenties te vermijden wanneer de speler aan failoverstromen schakelt.

