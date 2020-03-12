---
description: De eigenschap MediaPlayerItem.timedMetadata biedt toegang tot alle objecten TimedMetadata die zijn gemaakt van afspeellijst-/manifesttags of van ID3-tags in de mediastream.
seo-description: De eigenschap MediaPlayerItem.timedMetadata biedt toegang tot alle objecten TimedMetadata die zijn gemaakt van afspeellijst-/manifesttags of van ID3-tags in de mediastream.
seo-title: Meldingen voor manifestlabels
title: Meldingen voor manifestlabels
uuid: 50727455-b37b-4e39-8efb-a97de3164074
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Meldingen voor manifestlabels{#notifications-for-manifest-tags}

De eigenschap MediaPlayerItem.timedMetadata biedt toegang tot alle objecten TimedMetadata die zijn gemaakt van afspeellijst-/manifesttags of van ID3-tags in de mediastream.

<!--<a id="section_9A22F6F1EA1F4F0C9E0C7687D12AA4AA"></a>-->

De `MediaPlayerItem.hasTimedMetadata` eigenschap geeft aan of er een aangepaste tag met abonnement aanwezig is in de huidige media. U kunt metagegevens met tijdinstellingen controleren door te luisteren naar de metagegevens `Events.TimedMetadataEvent`die de instantie MediaPlayer verzendt telkens wanneer een nieuw `TimedMetadata` object wordt gemaakt.
