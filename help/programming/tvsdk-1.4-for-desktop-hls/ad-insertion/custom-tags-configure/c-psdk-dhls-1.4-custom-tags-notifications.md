---
description: Met de eigenschap MediaPlayerItem.timedMetadata hebt u toegang tot alle objecten TimedMetadata die zijn gemaakt van afspeellijst-/manifesttags of van ID3-tags in de mediastream. De eigenschap MediaPlayerItem.hasTimedMetadata geeft aan of er een aangepaste tag met een abonnement aanwezig is in de huidige media.
seo-description: Met de eigenschap MediaPlayerItem.timedMetadata hebt u toegang tot alle objecten TimedMetadata die zijn gemaakt van afspeellijst-/manifesttags of van ID3-tags in de mediastream. De eigenschap MediaPlayerItem.hasTimedMetadata geeft aan of er een aangepaste tag met een abonnement aanwezig is in de huidige media.
seo-title: Meldingen voor manifestlabels
title: Meldingen voor manifestlabels
uuid: 87bee41b-b44e-4d12-afd2-7a63023f992c
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---


# Meldingen voor manifestlabels{#notifications-for-manifest-tags}

Met de eigenschap MediaPlayerItem.timedMetadata hebt u toegang tot alle objecten TimedMetadata die zijn gemaakt van afspeellijst-/manifesttags of van ID3-tags in de mediastream. De eigenschap MediaPlayerItem.hasTimedMetadata geeft aan of er een aangepaste tag met een abonnement aanwezig is in de huidige media.

U kunt getimede metagegevens controleren door te luisteren naar de volgende gebeurtenissen, die uw toepassing op de hoogte stellen van verwante activiteiten:

* `MediaPlayerItemEvent.ITEM_CREATED`: De eerste lijst met  `TimedMetadata` objecten is beschikbaar nadat de objecten  `MediaPlayerItem` zijn gemaakt. Deze gebeurtenis brengt uw toepassing op de hoogte wanneer dit gebeurt.

* `MediaPlayerItemEvent.ITEM_UPDATED`: Voor live/lineaire streams waarbij het manifest/de afspeellijst periodiek wordt vernieuwd, kunnen extra aangepaste tags worden weergegeven in de bijgewerkte afspeellijst/het manifest, zodat aanvullende objecten TimedMetadata aan de  `MediaPlayerItem.timedMetadata` eigenschap kunnen worden toegevoegd. Deze gebeurtenis brengt uw toepassing op de hoogte wanneer dit gebeurt.

* `TimedMetadataEvent.TIMED_METADATA_AVAILABLE`: Telkens wanneer een nieuw  `TimedMetadata` object wordt gemaakt, wordt deze gebeurtenis verzonden door de  `MediaPlayer`. Deze gebeurtenis wordt niet verzonden voor het `TimedMetadata`-object dat tijdens de initialisatiefase is gemaakt.

