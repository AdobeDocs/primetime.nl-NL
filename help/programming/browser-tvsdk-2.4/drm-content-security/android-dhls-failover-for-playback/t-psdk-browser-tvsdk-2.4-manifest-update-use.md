---
description: U kunt deze functie inschakelen en controleren op verwante gebeurtenissen.
seo-description: U kunt deze functie inschakelen en controleren op verwante gebeurtenissen.
seo-title: Live master-manifest bijwerken gebruiken
title: Live master-manifest bijwerken gebruiken
uuid: 4ec665ab-b7ce-4a45-a251-13a07eb4d789
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Live master-manifest bijwerken gebruiken{#use-live-master-manifest-update}

U kunt deze functie inschakelen en controleren op verwante gebeurtenissen.

1. Als u live master-manifest-updates wilt inschakelen, stelt u de updatefrequentie (in minuten) in door de `NetworkConfiguration.masterUpdateInterval` eigenschap in te stellen.
1. U kunt succesvolle manifestupdates optioneel bijhouden door te luisteren naar de `MediaPlayerItemEvent.MASTER_UPDATED` gebeurtenis.
