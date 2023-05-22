---
description: Het MediaPlayer-object vertegenwoordigt uw mediaspeler. Een MediaPlayerItem vertegenwoordigt audio of video op uw speler.
title: Informatie over de klasse MediaPlayerItem
exl-id: 07105fab-0338-4410-93f3-e337d46d9de5
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 0%

---

# Informatie over de klasse MediaPlayerItem{#about-the-mediaplayeritem-class}

Het MediaPlayer-object vertegenwoordigt uw mediaspeler. Een MediaPlayerItem vertegenwoordigt audio of video op uw speler.

Nadat een mediabron is geladen, maakt TVSDK een instantie van de `MediaPlayerItem` klasse om toegang tot die bron te verlenen.

De `MediaResource` vertegenwoordigt een verzoek dat door de toepassingslaag aan wordt uitgegeven `MediaPlayer` -instantie om inhoud te laden.

De `MediaPlayer` lost het media middel op, laadt het bijbehorende duidelijke dossier, en ontleedt manifest. Dit is het asynchrone gedeelte van het proces voor het laden van bronnen. De `MediaPlayerItem` -instantie wordt gemaakt nadat de bron is opgelost en dit is een opgeloste versie van een `MediaResource`. TVSDK biedt toegang tot het nieuwe `MediaPlayerItem` instantie door `MediaPlayer.CurrentItem`

>[!TIP]
>
>U moet wachten tot de bron is geladen voordat u het item van de mediaspeler opent.
