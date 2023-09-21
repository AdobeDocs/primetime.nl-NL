---
title: Externe en lokale iOS-sleutellevering
description: Externe en lokale iOS-sleutellevering
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# Externe en lokale iOS-sleutellevering {#remote-and-local-ios-key-delivery}

Adobe Primetime biedt ondersteuning voor de volgende opties voor belangrijke levering aan iOS-clients:

* **Extern** - Voert uit zoals gespecificeerd in de Levende Streaming van HTTP (HLS) specificatie; M3U8 manifest specificeert een weg HTTPS die een sleutel AES omvat die zou moeten worden gebruikt om de volgende gecodeerde segmenten in de stroom te decrypteren. Wanneer u `Remote` in het Primetime DRM-beleid moet het clientapparaat verbinding maken met een externe HTTPS-server om een AES-sleutel te verkrijgen.

* **Lokaal** - Wanneer u `Local` in Primetime DRM in plaats van verbinding te maken met internet/netwerk voor de AES-sleutel, wordt een lokale HTTPS-server ingesloten in de iOS-toepassing, die vervolgens alle AES-sleutelverzoeken beheert. De ingesloten HTTPS-server wordt automatisch ingesteld en geconfigureerd in de P-toepassing. De ontwikkelaar van de toepassing heeft geen tussenkomst nodig.

De levering van de externe sleutel wordt ingeschakeld via het Primetime DRM-beleid dat wordt gebruikt om inhoud te verpakken. Als u deze instelling wilt wijzigen, moet u de inhoud opnieuw verpakken. Als u levering via een externe sleutel inschakelt, moet u een Primetime DRM-sleutelserver implementeren die belangrijke aanvragen van iOS-clients kan beheren. De workflow voor clients op andere platforms wordt echter niet gewijzigd.

>[!NOTE]
>
>De selectie voor belangrijke levering is alleen van invloed op iOS-clients. Alle andere apparaten die HLS-inhoud gebruiken, zoals Android en Primetime op Desktop (Flash Player), gebruiken altijd `Local` belangrijke levering, zelfs als `Remote` is opgegeven.
