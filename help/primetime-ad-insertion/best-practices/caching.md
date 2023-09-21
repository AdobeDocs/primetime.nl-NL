---
title: Caching
description: Caching
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---

# HTTP-caching {#caching}

De Ad Insertion van Primetime door gebrek eerbiedigt de kopballen van de geheim voorgeheugencontrole van HTTP wanneer het halen en creatieve evenals inhoud.  Dit kan drastisch de hoeveelheid netwerkverzoeken verminderen die voor Primetime Ad Insertion wordt vereist om aan CDN over alle cliënten te maken.  Voor caching, adviseert de Adobe de volgende montages en impliceert het verzenden van de kopbal van HTTP `max-age` van uw CDN.  Neem contact op met de vertegenwoordiger van de CDN om deze headers in te schakelen voor uw videostreams en ad streams.

## Voor live/lineaire inhoud {#caching-live-linear-content}

* Hoofdmanifest: 24 uur, of cache-control: max-age=86400
* Mediummanifest: 1 seconde, of cache-besturing: max-age=1

## Voor VOD-inhoud {#caching-vod-content}

* Hoofdmanifest: 24 uur, of cache-control: max-age=86400
* Mediummanifest: 24 uur, of cache-besturing: max-age=86400
