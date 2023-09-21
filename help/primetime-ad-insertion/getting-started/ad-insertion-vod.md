---
title: Ad Insertion gebruiken voor VOD
description: Ad Insertion gebruiken voor VOD
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# Ad Insertion gebruiken voor VOD {#ad-insertion-vod}

Primetime Ad Insertion ondersteunt het toevoegen van VOD-bestanden aan meerdere VOD-bestanden met de standaard VAST 3.0+- of VMAP 1.0+-indelingen.

* [IAB VMAP](https://www.iab.com/wp-content/uploads/2015/06/VMAPv1_0.pdf)

* [IAB VAST](https://www.iab.com/wp-content/uploads/2015/06/VASTv3_0.pdf)

## VOD (advertentiekaarten) {#server-mapped-ads}

Primetime Ad Insertion ondersteunt VOD-invoeging met advertenties die vóór het begin van het afspelen zijn ingevoegd met behulp van tijdlijngegevens die in een VMAP-indeling zijn gedefinieerd.  VMAP-specifieke bijschriften, zoals breakStart/breakEnd-beacons, worden geleverd bij [Advertentie bijhouden](set-up-ad-tracking.md).

## Volledige weergave van gebeurtenissen (VOD met Ad Decisioning Cues) {#full-event-replay}

Primetime Ad Insertion ondersteunt ook gespecialiseerde VOD-elementen die cues bevatten in de inhoudsstroom zelf, zoals die worden gevonden bij het afspelen van eerder opgenomen live gebeurtenissen. Voor meer informatie over de soorten ad-beslissingsaanwijzingen (of actiefindelingen) die wij ondersteunen, raadpleegt u [Ad Insertion gebruiken in Live/Lineair](ad-insertion-live-linear-stream.md).

Wij steunen zowel één enkel ad-request als parallelle veelvoudige ad-request scenario&#39;s voor activa VOD die meer dan één ad-break bevatten. Zie voor meer informatie `ptmulticall` parameter in [Parameterbeschrijving](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md). Zowel VAST als VMAP-indelingen worden ondersteund voor in-stream cues.
