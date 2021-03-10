---
description: Nadat een MediaResource met succes wordt geladen, leidt Browser TVSDK tot een geval van de klasse MediaPlayerItem om toegang tot die middel te verlenen.
title: Informatie over de klasse MediaPlayerItem
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 0%

---


# Informatie over de MediaPlayerItem-klasse{#about-the-mediaplayeritem-class}

Nadat een MediaResource met succes wordt geladen, leidt Browser TVSDK tot een geval van de klasse MediaPlayerItem om toegang tot die middel te verlenen.

`MediaResource` vertegenwoordigt een verzoek dat door de toepassingslaag aan `MediaPlayer` instantie wordt uitgegeven om inhoud te laden.

`MediaPlayer` verhelpt de mediabron, laadt het bijbehorende manifestbestand en parseert het manifest. Dit is het asynchrone gedeelte van het proces voor het laden van bronnen. De instantie `MediaPlayerItem` wordt geproduceerd nadat het middel is opgelost, en deze instantie is een opgeloste versie van `MediaResource`. Browser TVSDK biedt via `MediaPlayer.CurrentItem` toegang tot de nieuwe instantie `MediaPlayerItem`.

>[!TIP]
>
>U moet wachten tot de bron is geladen voordat u het item van de mediaspeler opent.

