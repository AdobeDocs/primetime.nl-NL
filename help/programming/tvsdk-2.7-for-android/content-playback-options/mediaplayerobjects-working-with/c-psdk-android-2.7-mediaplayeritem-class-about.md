---
description: Nadat u met succes het voorwerp MediaResource laadt, leidt TVSDK tot een geval van de klasse MediaPlayerItem om toegang tot die middel te verlenen.
seo-description: Nadat u met succes het voorwerp MediaResource laadt, leidt TVSDK tot een geval van de klasse MediaPlayerItem om toegang tot die middel te verlenen.
seo-title: Informatie over de klasse MediaPlayerItem
title: Informatie over de klasse MediaPlayerItem
uuid: 2d37f358-d158-481b-81d5-27546e9c2e0e
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Informatie over de klasse MediaPlayerItem {#about-the-mediaplayeritem-class}

Het MediaPlayer-object vertegenwoordigt uw mediaspeler. Een MediaPlayerItem vertegenwoordigt audio of video op uw speler.

Nadat u met succes het voorwerp MediaResource laadt, leidt TVSDK tot een geval van de klasse MediaPlayerItem om toegang tot die middel te verlenen.

Het `MediaResource` vertegenwoordigt een verzoek dat door de toepassingslaag aan de `MediaPlayer` instantie wordt uitgegeven om inhoud te laden.

De `MediaPlayer` mediabron verhelpt, laadt het bijbehorende manifestbestand en parseert het manifest. Dit is het asynchrone gedeelte van het proces voor het laden van bronnen. De `MediaPlayerItem` instantie wordt geproduceerd nadat het middel is opgelost, en dit geval is een opgeloste versie van een `MediaResource`. TVSDK biedt toegang tot de nieuwe `MediaPlayerItem` instantie via `MediaPlayer.CurrentItem`.

>[!TIP]
>
>U moet wachten tot de bron is geladen voordat u het item van de mediaspeler opent.