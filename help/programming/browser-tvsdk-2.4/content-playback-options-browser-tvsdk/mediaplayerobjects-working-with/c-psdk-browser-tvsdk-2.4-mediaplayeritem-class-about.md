---
description: Nadat een MediaResource met succes wordt geladen, leidt Browser TVSDK tot een geval van de klasse MediaPlayerItem om toegang tot die middel te verlenen.
seo-description: Nadat een MediaResource met succes wordt geladen, leidt Browser TVSDK tot een geval van de klasse MediaPlayerItem om toegang tot die middel te verlenen.
seo-title: Informatie over de klasse MediaPlayerItem
title: Informatie over de klasse MediaPlayerItem
uuid: 5226d3ad-2438-44fe-a8ef-bcc0da8331b8
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Informatie over de klasse MediaPlayerItem{#about-the-mediaplayeritem-class}

Nadat een MediaResource met succes wordt geladen, leidt Browser TVSDK tot een geval van de klasse MediaPlayerItem om toegang tot die middel te verlenen.

Het `MediaResource` vertegenwoordigt een verzoek dat door de toepassingslaag aan de `MediaPlayer` instantie wordt uitgegeven om inhoud te laden.

De `MediaPlayer` mediabron verhelpt, laadt het bijbehorende manifestbestand en parseert het manifest. Dit is het asynchrone gedeelte van het proces voor het laden van bronnen. De `MediaPlayerItem` instantie wordt geproduceerd nadat het middel is opgelost, en dit geval is een opgeloste versie van een `MediaResource`. Browser TVSDK biedt via `MediaPlayerItem` het nieuwe `MediaPlayer.CurrentItem`exemplaar toegang tot het nieuwe exemplaar.

>[!TIP]
>
>U moet wachten tot de bron is geladen voordat u het item van de mediaspeler opent.

