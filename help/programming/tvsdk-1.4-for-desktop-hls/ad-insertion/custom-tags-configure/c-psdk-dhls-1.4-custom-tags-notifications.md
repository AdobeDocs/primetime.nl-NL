---
description: Met de eigenschap MediaPlayerItem.timedMetadata hebt u toegang tot alle objecten TimedMetadata die zijn gemaakt van afspeellijst-/manifesttags of van ID3-tags in de mediastream. De eigenschap MediaPlayerItem.hasTimedMetadata geeft aan of er een aangepaste tag met een abonnement aanwezig is in de huidige media.
title: Meldingen voor manifestlabels
exl-id: 1a91fa47-edd5-4496-9755-17c906a3cf54
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# Meldingen voor manifestlabels{#notifications-for-manifest-tags}

Met de eigenschap MediaPlayerItem.timedMetadata hebt u toegang tot alle objecten TimedMetadata die zijn gemaakt van afspeellijst-/manifesttags of van ID3-tags in de mediastream. De eigenschap MediaPlayerItem.hasTimedMetadata geeft aan of er een aangepaste tag met een abonnement aanwezig is in de huidige media.

U kunt getimede metagegevens controleren door te luisteren naar de volgende gebeurtenissen, die uw toepassing op de hoogte stellen van verwante activiteiten:

* `MediaPlayerItemEvent.ITEM_CREATED`: De eerste lijst van `TimedMetadata` objecten zijn beschikbaar na de `MediaPlayerItem` wordt gemaakt. Deze gebeurtenis brengt uw toepassing op de hoogte wanneer dit gebeurt.

* `MediaPlayerItemEvent.ITEM_UPDATED`: Voor live/lineaire streams waarbij het manifest/de afspeellijst periodiek wordt vernieuwd, kunnen extra aangepaste tags worden weergegeven in de bijgewerkte afspeellijst/het manifest, zodat aanvullende objecten TimedMetadata kunnen worden toegevoegd aan de `MediaPlayerItem.timedMetadata` eigenschap. Deze gebeurtenis brengt uw toepassing op de hoogte wanneer dit gebeurt.

* `TimedMetadataEvent.TIMED_METADATA_AVAILABLE`: Elke keer dat er een nieuwe `TimedMetadata` object is gemaakt, wordt deze gebeurtenis verzonden door de `MediaPlayer`. Deze gebeurtenis wordt niet verzonden voor de `TimedMetadata` object dat tijdens de initialisatiefase is gemaakt.
