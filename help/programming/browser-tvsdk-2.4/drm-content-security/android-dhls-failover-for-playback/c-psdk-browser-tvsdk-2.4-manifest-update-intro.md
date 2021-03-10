---
description: Browser-TVSDK kan gewijzigde afspeelinformatie in master m3u8-manifests voor live streaming detecteren en de afspeelinformatie bijwerken terwijl de stream wordt afgespeeld. Browser TVSDK steunt een dynamische reeks profielen van het beetjetarief aangezien de profielen verschijnen of verdwijnen uit master manifest, met inbegrip van niet-overlappende profielbeetjetarieven tussen updates.
title: Live master-manifest-update
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 0%

---


# Live master-manifest update{#live-master-manifest-update}

Browser-TVSDK kan gewijzigde afspeelinformatie in master m3u8-manifests voor live streaming detecteren en de afspeelinformatie bijwerken terwijl de stream wordt afgespeeld. Browser TVSDK steunt een dynamische reeks profielen van het beetjetarief aangezien de profielen verschijnen of verdwijnen uit master manifest, met inbegrip van niet-overlappende profielbeetjetarieven tussen updates.

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

