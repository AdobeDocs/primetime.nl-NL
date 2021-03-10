---
description: Nadat u met succes het voorwerp MediaResource laadt, leidt TVSDK tot een geval van de klasse MediaPlayerItem om toegang tot die middel te verlenen.
title: Informatie over de klasse MediaPlayerItem
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---


# Informatie over de MediaPlayerItem-klasse {#about-the-mediaplayeritem-class}

Het MediaPlayer-object vertegenwoordigt uw mediaspeler. Een MediaPlayerItem vertegenwoordigt audio of video op uw speler.

Nadat u met succes het voorwerp MediaResource laadt, leidt TVSDK tot een geval van de klasse MediaPlayerItem om toegang tot die middel te verlenen.

`MediaResource` vertegenwoordigt een verzoek dat door de toepassingslaag aan `MediaPlayer` instantie wordt uitgegeven om inhoud te laden.

`MediaPlayer` verhelpt de mediabron, laadt het bijbehorende manifestbestand en parseert het manifest. Dit is het asynchrone gedeelte van het proces voor het laden van bronnen. De instantie `MediaPlayerItem` wordt geproduceerd nadat het middel is opgelost, en deze instantie is een opgeloste versie van `MediaResource`. TVSDK biedt via `MediaPlayer.CurrentItem` toegang tot het nieuwe `MediaPlayerItem`-exemplaar.

>[!TIP]
>
>U moet wachten tot de bron is geladen voordat u het item van de mediaspeler opent.