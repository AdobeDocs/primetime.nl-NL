---
description: Browser-TVSDK kan gewijzigde afspeelinformatie in master m3u8-manifests voor live streaming detecteren en de afspeelinformatie bijwerken terwijl de stream wordt afgespeeld. Browser TVSDK steunt een dynamische reeks profielen van het beetjetarief aangezien de profielen verschijnen of verdwijnen uit hoofdmanifest, met inbegrip van niet-overlappende tarief van profielbeetjes tussen updates.
seo-description: Browser-TVSDK kan gewijzigde afspeelinformatie in master m3u8-manifests voor live streaming detecteren en de afspeelinformatie bijwerken terwijl de stream wordt afgespeeld. Browser TVSDK steunt een dynamische reeks profielen van het beetjetarief aangezien de profielen verschijnen of verdwijnen uit hoofdmanifest, met inbegrip van niet-overlappende tarief van profielbeetjes tussen updates.
seo-title: Live master-manifest bijwerken
title: Live master-manifest bijwerken
uuid: 4b918a73-dacf-465a-82d6-404c6bdb01f2
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

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
* Alle vertoningsgegevens blijven hetzelfde (behalve dat URL&#39;s kunnen variëren).
* De DRM-toegangsgegevens blijven ongewijzigd.
* Segmenten worden verpakt rond dezelfde PTS- en framegrenzen in een klein foutbereik.

