---
description: Nadat een MediaResource met succes wordt geladen, leidt Browser TVSDK tot een geval van de klasse MediaPlayerItem om toegang tot die middel te verlenen.
title: Informatie over de klasse MediaPlayerItem
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 0%

---

# Informatie over de klasse MediaPlayerItem{#about-the-mediaplayeritem-class}

Nadat een MediaResource met succes wordt geladen, leidt Browser TVSDK tot een geval van de klasse MediaPlayerItem om toegang tot die middel te verlenen.

De `MediaResource` vertegenwoordigt een verzoek dat door de toepassingslaag aan wordt uitgegeven `MediaPlayer` -instantie om inhoud te laden.

De `MediaPlayer` lost het media middel op, laadt het bijbehorende duidelijke dossier, en ontleedt manifest. Dit is het asynchrone gedeelte van het proces voor het laden van bronnen. De `MediaPlayerItem` -instantie wordt gemaakt nadat de bron is opgelost en dit is een opgeloste versie van een `MediaResource`. Browser TVSDK biedt toegang tot het zojuist gemaakte `MediaPlayerItem` instantie door `MediaPlayer.CurrentItem`.

>[!TIP]
>
>U moet wachten tot de bron is geladen voordat u het item van de mediaspeler opent.
