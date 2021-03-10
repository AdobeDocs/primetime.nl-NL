---
description: De eigenschap MediaPlayerItem.timedMetadata biedt toegang tot alle objecten TimedMetadata die zijn gemaakt van afspeellijst-/manifesttags of van ID3-tags in de mediastream.
title: Meldingen voor manifestlabels
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 0%

---


# Meldingen voor manifestlabels{#notifications-for-manifest-tags}

De eigenschap MediaPlayerItem.timedMetadata biedt toegang tot alle objecten TimedMetadata die zijn gemaakt van afspeellijst-/manifesttags of van ID3-tags in de mediastream.

<!--<a id="section_9A22F6F1EA1F4F0C9E0C7687D12AA4AA"></a>-->

De eigenschap `MediaPlayerItem.hasTimedMetadata` geeft aan of er een aangepaste tag met een abonnement aanwezig is in de huidige media. U kunt getimede meta-gegevens controleren door op `Events.TimedMetadataEvent` te luisteren, die de instantie MediaPlayer verzendt telkens als een nieuw `TimedMetadata` voorwerp wordt gecreeerd.
