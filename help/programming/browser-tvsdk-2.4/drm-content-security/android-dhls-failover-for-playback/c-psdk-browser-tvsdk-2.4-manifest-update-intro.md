---
description: Browser-TVSDK kan gewijzigde afspeelinformatie in master m3u8-manifests voor live streaming detecteren en de afspeelinformatie bijwerken terwijl de stream wordt afgespeeld. Browser TVSDK steunt een dynamische reeks profielen van het beetjetarief aangezien de profielen verschijnen of verdwijnen uit hoofdmanifest, met inbegrip van niet-overlappende tarief van profielbeetjes tussen updates.
title: Live master-manifest bijwerken
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 0%

---

# Live master-manifest bijwerken{#live-master-manifest-update}

Browser-TVSDK kan gewijzigde afspeelinformatie in master m3u8-manifests voor live streaming detecteren en de afspeelinformatie bijwerken terwijl de stream wordt afgespeeld. Browser TVSDK steunt een dynamische reeks profielen van het beetjetarief aangezien de profielen verschijnen of verdwijnen uit hoofdmanifest, met inbegrip van niet-overlappende tarief van profielbeetjes tussen updates.

De volgende functies worden ondersteund:

* Aantal profielen (verhogen of verlagen)
* Profielbitsnelheden (overlappend of niet-overlappend)
* Profielen met URL&#39;s op dezelfde (of andere) server
* Elke failoverstructuur

Aan alle volgende voorwaarden moet worden voldaan:

* Stream is live.
* Zowel de tijd als de tag veranderen.
* Alle vertoningsgegevens blijven ongewijzigd (behalve dat URL&#39;s kunnen variëren).
* De DRM-toegangsgegevens blijven ongewijzigd.
* Segmenten worden verpakt rond dezelfde PTS- en framegrenzen in een klein foutbereik.
