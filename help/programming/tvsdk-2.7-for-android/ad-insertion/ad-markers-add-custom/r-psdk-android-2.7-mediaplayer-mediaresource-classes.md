---
description: Een MediaResource vertegenwoordigt de inhoud die door de instantie MediaPlayer wordt geladen.
title: De klassen MediaPlayer en MediaResource
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---

# De klassen MediaPlayer en MediaResource {#mediaplayer-and-mediaresource-classes}

Een MediaResource vertegenwoordigt de inhoud die door de instantie MediaPlayer wordt geladen.

<!--<a id="section_431AB7221E0249BF949EC72EEB9B428A"></a>-->

TVSDK biedt de mogelijkheid om inhoud te laden en voor te bereiden voor afspelen met de `replaceCurrentResource` methode in `MediaPlayer`. Deze methode heeft twee argumenten, een instantie van `MediaPlayerResource` en, optioneel, een geval van `MediaPlayerItemConfig`, die u kunt gebruiken om door de toepassing gedefinieerde aangepaste parameters door te geven.

* Zie mediaplayer-reuse-or-remove voor meer informatie.
* Voor meer informatie over `MediaPlayerResource`, zie media-resource-create
