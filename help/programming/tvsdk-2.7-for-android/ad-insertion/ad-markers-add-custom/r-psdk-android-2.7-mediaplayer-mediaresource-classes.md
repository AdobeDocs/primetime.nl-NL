---
description: Een MediaResource vertegenwoordigt de inhoud die op het punt staat door de instantie MediaPlayer te worden geladen.
title: De klassen MediaPlayer en MediaResource
exl-id: c4219dff-de75-4b8a-ad33-e0a721c38de7
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---

# De klassen MediaPlayer en MediaResource {#mediaplayer-and-mediaresource-classes}

Een MediaResource vertegenwoordigt de inhoud die op het punt staat door de instantie MediaPlayer te worden geladen.

<!--<a id="section_431AB7221E0249BF949EC72EEB9B428A"></a>-->

TVSDK biedt de mogelijkheid om inhoud te laden en voor te bereiden voor afspelen met behulp van de `replaceCurrentResource` methode in `MediaPlayer`. Deze methode heeft twee argumenten, een instantie van `MediaPlayerResource` en, optioneel, een geval van `MediaPlayerItemConfig`, die u kunt gebruiken om door de toepassing gedefinieerde aangepaste parameters door te geven.

* Zie mediaplayer-reuse-or-remove voor meer informatie.
* Voor meer informatie over `MediaPlayerResource`, zie media-resource-create
