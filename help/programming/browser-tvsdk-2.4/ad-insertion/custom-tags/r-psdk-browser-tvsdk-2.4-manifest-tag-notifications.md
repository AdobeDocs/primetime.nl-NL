---
description: De eigenschap MediaPlayerItem.timedMetadata biedt toegang tot alle objecten TimedMetadata die zijn gemaakt van afspeellijst-/manifesttags of van ID3-tags in de mediastream.
title: Meldingen voor manifestlabels
exl-id: a8a3cada-d796-460a-bd8f-fc4a2703e7f0
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 0%

---

# Meldingen voor manifestlabels{#notifications-for-manifest-tags}

De eigenschap MediaPlayerItem.timedMetadata biedt toegang tot alle objecten TimedMetadata die zijn gemaakt van afspeellijst-/manifesttags of van ID3-tags in de mediastream.

<!--<a id="section_9A22F6F1EA1F4F0C9E0C7687D12AA4AA"></a>-->

De `MediaPlayerItem.hasTimedMetadata` Deze eigenschap geeft aan of er een aangepaste tag met een abonnement voorkomt in de huidige media. U kunt vastgestelde meta-gegevens controleren door op `Events.TimedMetadataEvent`, die de instantie MediaPlayer elke keer verzendt als een nieuwe instantie `TimedMetadata` wordt gemaakt.
