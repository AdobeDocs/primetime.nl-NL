---
description: Het MediaPlayer-object vertegenwoordigt uw mediaspeler. Een MediaPlayerItem vertegenwoordigt audio of video op uw speler.
seo-description: Het MediaPlayer-object vertegenwoordigt uw mediaspeler. Een MediaPlayerItem vertegenwoordigt audio of video op uw speler.
seo-title: Informatie over de klasse MediaPlayerItem
title: Informatie over de klasse MediaPlayerItem
uuid: d7f65edf-4693-4b1e-bae0-46fadce98751
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---


# Informatie over de MediaPlayerItem-klasse{#about-the-mediaplayeritem-class}

Het MediaPlayer-object vertegenwoordigt uw mediaspeler. Een MediaPlayerItem vertegenwoordigt audio of video op uw speler.

Nadat een media middel met succes wordt geladen, leidt TVSDK tot een geval van de `MediaPlayerItem` klasse om toegang tot die middel te verlenen.

`MediaResource` vertegenwoordigt een verzoek dat door de toepassingslaag aan `MediaPlayer` instantie wordt uitgegeven om inhoud te laden.

`MediaPlayer` verhelpt de mediabron, laadt het bijbehorende manifestbestand en parseert het manifest. Dit is het asynchrone gedeelte van het proces voor het laden van bronnen. De instantie `MediaPlayerItem` wordt geproduceerd nadat het middel is opgelost, en deze instantie is een opgeloste versie van `MediaResource`. TVSDK biedt toegang tot de nieuwe `MediaPlayerItem`-instantie via `MediaPlayer.CurrentItem`

>[!TIP]
>
>U moet wachten tot de bron is geladen voordat u het item van de mediaspeler opent.

