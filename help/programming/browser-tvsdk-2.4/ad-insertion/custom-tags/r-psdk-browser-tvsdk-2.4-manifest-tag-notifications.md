---
description: De eigenschap MediaPlayerItem.timedMetadata biedt toegang tot alle objecten TimedMetadata die zijn gemaakt van afspeellijst-/manifesttags of van ID3-tags in de mediastream.
seo-description: De eigenschap MediaPlayerItem.timedMetadata biedt toegang tot alle objecten TimedMetadata die zijn gemaakt van afspeellijst-/manifesttags of van ID3-tags in de mediastream.
seo-title: Meldingen voor manifestlabels
title: Meldingen voor manifestlabels
uuid: 50727455-b37b-4e39-8efb-a97de3164074
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---


# Meldingen voor manifestlabels{#notifications-for-manifest-tags}

De eigenschap MediaPlayerItem.timedMetadata biedt toegang tot alle objecten TimedMetadata die zijn gemaakt van afspeellijst-/manifesttags of van ID3-tags in de mediastream.

<!--<a id="section_9A22F6F1EA1F4F0C9E0C7687D12AA4AA"></a>-->

De eigenschap `MediaPlayerItem.hasTimedMetadata` geeft aan of een aangepaste tag met een abonnement aanwezig is in de huidige media. U kunt getimede meta-gegevens controleren door op `Events.TimedMetadataEvent` te luisteren, die de instantie MediaPlayer verzendt telkens als een nieuw `TimedMetadata` voorwerp wordt gecreeerd.
