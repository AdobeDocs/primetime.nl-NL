---
description: Het MediaPlayer-object vertegenwoordigt uw mediaspeler. Een MediaPlayerItem vertegenwoordigt audio of video op uw speler.
seo-description: Het MediaPlayer-object vertegenwoordigt uw mediaspeler. Een MediaPlayerItem vertegenwoordigt audio of video op uw speler.
seo-title: Informatie over de klasse MediaPlayerItem
title: Informatie over de klasse MediaPlayerItem
uuid: 531dd1a6-d72c-4ae3-9c3f-2f1d854245c5
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Informatie over de klasse MediaPlayerItem{#about-the-mediaplayeritem-class}

Het MediaPlayer-object vertegenwoordigt uw mediaspeler. Een MediaPlayerItem vertegenwoordigt audio of video op uw speler.

<!--<a id="section_01BC89E5C5A94D0A95EF9D29FBCE758A"></a>-->

Nadat een media middel met succes wordt geladen, leidt TVSDK tot een geval van de `MediaPlayerItem` klasse om toegang tot dat middel te verlenen.

Het `MediaResource` vertegenwoordigt een verzoek dat door de toepassingslaag aan de `MediaPlayer` instantie wordt uitgegeven om inhoud te laden.

De `MediaPlayer` mediabron verhelpt, laadt het bijbehorende manifestbestand en parseert het manifest. Dit is het asynchrone gedeelte van het proces voor het laden van bronnen. De `MediaPlayerItem` instantie wordt geproduceerd nadat het middel is opgelost, en dit geval is een opgeloste versie van een `MediaResource`. TVSDK biedt toegang tot de nieuwe `MediaPlayerItem` instantie via `MediaPlayer.currentItem`.

>[!TIP]
>
>U moet wachten tot de bron is geladen voordat u het item van de mediaspeler opent.

