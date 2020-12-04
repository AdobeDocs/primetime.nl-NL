---
description: Nadat een MediaResource met succes wordt geladen, leidt Browser TVSDK tot een geval van de klasse MediaPlayerItem om toegang tot die middel te verlenen.
seo-description: Nadat een MediaResource met succes wordt geladen, leidt Browser TVSDK tot een geval van de klasse MediaPlayerItem om toegang tot die middel te verlenen.
seo-title: Informatie over de klasse MediaPlayerItem
title: Informatie over de klasse MediaPlayerItem
uuid: 5226d3ad-2438-44fe-a8ef-bcc0da8331b8
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# Informatie over de MediaPlayerItem-klasse{#about-the-mediaplayeritem-class}

Nadat een MediaResource met succes wordt geladen, leidt Browser TVSDK tot een geval van de klasse MediaPlayerItem om toegang tot die middel te verlenen.

`MediaResource` vertegenwoordigt een verzoek dat door de toepassingslaag aan `MediaPlayer` instantie wordt uitgegeven om inhoud te laden.

`MediaPlayer` verhelpt de mediabron, laadt het bijbehorende manifestbestand en parseert het manifest. Dit is het asynchrone gedeelte van het proces voor het laden van bronnen. De instantie `MediaPlayerItem` wordt geproduceerd nadat het middel is opgelost, en deze instantie is een opgeloste versie van `MediaResource`. Browser TVSDK biedt via `MediaPlayer.CurrentItem` toegang tot de nieuwe instantie `MediaPlayerItem`.

>[!TIP]
>
>U moet wachten tot de bron is geladen voordat u het item van de mediaspeler opent.

