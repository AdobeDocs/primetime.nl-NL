---
description: Het MediaPlayer-object vertegenwoordigt uw mediaspeler. Een MediaPlayerItem vertegenwoordigt audio of video op uw speler.
title: Informatie over de klasse MediaPlayerItem
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 0%

---

# Informatie over de klasse MediaPlayerItem{#about-the-mediaplayeritem-class}

Het MediaPlayer-object vertegenwoordigt uw mediaspeler. Een MediaPlayerItem vertegenwoordigt audio of video op uw speler.

<!--<a id="section_01BC89E5C5A94D0A95EF9D29FBCE758A"></a>-->

Nadat een mediabron is geladen, maakt TVSDK een instantie van de `MediaPlayerItem` klasse om toegang tot die bron te verlenen.

De `MediaResource` vertegenwoordigt een verzoek dat door de toepassingslaag aan wordt uitgegeven `MediaPlayer` -instantie om inhoud te laden.

De `MediaPlayer` lost het media middel op, laadt het bijbehorende duidelijke dossier, en ontleedt manifest. Dit is het asynchrone gedeelte van het proces voor het laden van bronnen. De `MediaPlayerItem` -instantie wordt gemaakt nadat de bron is opgelost en dit is een opgeloste versie van een `MediaResource`. TVSDK biedt toegang tot het zojuist gemaakte `MediaPlayerItem` instantie door `MediaPlayer.currentItem`.

>[!TIP]
>
>U moet wachten tot de bron is geladen voordat u het item van de mediaspeler opent.
