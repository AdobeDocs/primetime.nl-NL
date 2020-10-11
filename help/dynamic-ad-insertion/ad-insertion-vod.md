---
title: Ad Insertion gebruiken voor VOD
description: Ad Insertion gebruiken voor VOD
translation-type: tm+mt
source-git-commit: 7d74e526dbc4c9f623d1ec30e4bc70d9318a89f9
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---


# Ad Insertion gebruiken voor VOD {#ad-insertion-vod}

Primetime Ad Insertion ondersteunt het toevoegen van VOD-bestanden aan meerdere VOD-bestanden met de standaard VAST 3.0+- of VMAP 1.0+-indelingen.

* [IAB VMAP](https://www.iab.com/wp-content/uploads/2015/06/VMAPv1_0.pdf)

* [IAB VAST](https://www.iab.com/wp-content/uploads/2015/06/VASTv3_0.pdf)

## VOD (via server toegewezen advertenties) {#server-mapped-ads}

Primetime Ad Insertion ondersteunt VOD-invoeging met advertenties die vóór het begin van het afspelen zijn ingevoegd met behulp van tijdlijngegevens die in een VMAP-indeling zijn gedefinieerd.  VMAP-specifieke bijschriften, zoals breakStart/breakEnd-beacons, worden geleverd met [Advertentie bijhouden](set-up-ad-tracking.md).

## Volledige weergave van gebeurtenissen (VOD met Ad Decisioning Cues) {#full-event-replay}

Primetime Ad Insertion ondersteunt ook gespecialiseerde VOD-elementen die cues bevatten in de inhoudsstroom zelf, zoals die worden gevonden bij het afspelen van eerder opgenomen live gebeurtenissen. Voor meer informatie over de types van ad beslissingsaanwijzingen (of richtsnoerformaten) steunen wij, zie [het Gebruiken van Ad Insertion in Levend/Lineair](ad-insertion-live-linear-stream.md).

Wij steunen zowel één enkel ad-request als parallelle veelvoudige ad-request scenario&#39;s voor activa VOD die meer dan één ad-break bevatten. Zie parameter in de beschrijving van de `ptmulticall` parameter voor meer informatie [](/help/dynamic-ad-insertion/msapi-topics/ms-getting-started/ms-api-query-params.md). Zowel VAST als VMAP-indelingen worden ondersteund voor in-stream cues.
