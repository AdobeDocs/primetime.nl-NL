---
title: Externe en lokale iOS-sleutellevering
description: Externe en lokale iOS-sleutellevering
copied-description: true
exl-id: becc2d3f-39f3-40ee-b980-7dfbbe6f569d
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# Externe en lokale iOS-sleutellevering {#remote-and-local-ios-key-delivery}

Adobe Primetime biedt ondersteuning voor de volgende opties voor belangrijke levering aan iOS-clients:

* **Extern** - voert de handelingen uit zoals gespecificeerd in de specificatie HTTP Live Streaming (HLS); Het M3U8-manifest geeft een HTTPS-pad aan dat een AES-sleutel bevat die moet worden gebruikt om de volgende gecodeerde segmenten in de stream te decoderen. Wanneer u `Remote` in het Primetime DRM-beleid moet het clientapparaat verbinding maken met een externe HTTPS-server om een AES-sleutel te verkrijgen.

* **Lokaal** - Wanneer u `Local` in Primetime DRM in plaats van verbinding te maken met internet/netwerk voor de AES-sleutel, wordt een lokale HTTPS-server ingesloten in de iOS-toepassing, die vervolgens alle AES-sleutelverzoeken beheert. De ingesloten HTTPS-server wordt automatisch ingesteld en geconfigureerd in de P-toepassing. De ontwikkelaar van de toepassing heeft geen interventie nodig.

De levering van de externe sleutel wordt ingeschakeld via het Primetime DRM-beleid dat wordt gebruikt om inhoud te verpakken. Als u deze instelling wilt wijzigen, moet u de inhoud opnieuw verpakken. Als u levering via een externe sleutel inschakelt, moet u een Primetime DRM-sleutelserver implementeren die belangrijke aanvragen van iOS-clients kan beheren. De workflow voor clients op andere platforms wordt echter niet gewijzigd.

>[!NOTE]
>
>De selectie voor belangrijke levering is alleen van invloed op iOS-clients. Alle andere apparaten die HLS-inhoud gebruiken, zoals Android en Primetime op Desktop (Flash Player), gebruiken altijd `Local` belangrijke levering, zelfs als `Remote` is opgegeven.
