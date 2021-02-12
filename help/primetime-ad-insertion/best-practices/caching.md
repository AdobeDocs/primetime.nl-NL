---
title: Caching
description: null
translation-type: tm+mt
source-git-commit: 76dc54fabdae400ad708ba83fcf6f7fd5caa2b22
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 0%

---


# HTTP-caching {#caching}

De Ad Insertion van Primetime door gebrek eerbiedigt de kopballen van de geheim voorgeheugencontrole van HTTP wanneer het halen en creatieve evenals inhoud.  Dit kan drastisch de hoeveelheid netwerkverzoeken verminderen die voor Primetime Ad Insertion wordt vereist om aan CDN over alle cliënten te maken.  Voor caching, adviseert Adobe de volgende montages en impliceert het verzenden van de kopbal `max-age` van HTTP van uw CDN.  Neem contact op met de vertegenwoordiger van de CDN om deze headers in te schakelen voor uw videostreams en ad streams.

## Voor live/lineaire inhoud {#caching-live-linear-content}

* Master manifest: 24 uur, of cache-besturing: max-age=86400
* Mediamanifest: 1 seconde, of cache-control: max-age=1

## Voor VOD-inhoud {#caching-vod-content}

* Master manifest: 24 uur, of cache-besturing: max-age=86400
* Mediamanifest: 24 uur, of cache-besturing: max-age=86400
