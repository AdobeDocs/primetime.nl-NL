---
description: Met de eigenschap MediaPlayerItem.timedMetadata hebt u toegang tot alle objecten TimedMetadata die zijn gemaakt van afspeellijst-/manifesttags of van ID3-tags in de mediastream. De eigenschap MediaPlayerItem.hasTimedMetadata geeft aan of er een aangepaste tag met een abonnement aanwezig is in de huidige media.
title: Meldingen voor manifestlabels
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---


# Meldingen voor manifestlabels{#notifications-for-manifest-tags}

Met de eigenschap MediaPlayerItem.timedMetadata hebt u toegang tot alle objecten TimedMetadata die zijn gemaakt van afspeellijst-/manifesttags of van ID3-tags in de mediastream. De eigenschap MediaPlayerItem.hasTimedMetadata geeft aan of er een aangepaste tag met een abonnement aanwezig is in de huidige media.

U kunt getimede metagegevens controleren door te luisteren naar de volgende gebeurtenissen, die uw toepassing op de hoogte stellen van verwante activiteiten:

* `MediaPlayerItemEvent.ITEM_CREATED`: De eerste lijst met  `TimedMetadata` objecten is beschikbaar nadat de objecten  `MediaPlayerItem` zijn gemaakt. Deze gebeurtenis brengt uw toepassing op de hoogte wanneer dit gebeurt.

* `MediaPlayerItemEvent.ITEM_UPDATED`: Voor live/lineaire streams waarbij het manifest/de afspeellijst periodiek wordt vernieuwd, kunnen extra aangepaste tags worden weergegeven in de bijgewerkte afspeellijst/het manifest, zodat aanvullende objecten TimedMetadata aan de  `MediaPlayerItem.timedMetadata` eigenschap kunnen worden toegevoegd. Deze gebeurtenis brengt uw toepassing op de hoogte wanneer dit gebeurt.

* `TimedMetadataEvent.TIMED_METADATA_AVAILABLE`: Telkens wanneer een nieuw  `TimedMetadata` object wordt gemaakt, wordt deze gebeurtenis verzonden door de  `MediaPlayer`. Deze gebeurtenis wordt niet verzonden voor het `TimedMetadata`-object dat tijdens de initialisatiefase is gemaakt.

