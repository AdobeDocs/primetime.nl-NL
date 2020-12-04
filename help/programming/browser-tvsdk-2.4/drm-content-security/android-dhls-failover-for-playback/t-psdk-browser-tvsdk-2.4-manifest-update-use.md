---
description: U kunt deze functie inschakelen en controleren op verwante gebeurtenissen.
seo-description: U kunt deze functie inschakelen en controleren op verwante gebeurtenissen.
seo-title: Live update master-manifest gebruiken
title: Live update master-manifest gebruiken
uuid: 4ec665ab-b7ce-4a45-a251-13a07eb4d789
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '71'
ht-degree: 0%

---


# Live update master-manifest gebruiken{#use-live-master-manifest-update}

U kunt deze functie inschakelen en controleren op verwante gebeurtenissen.

1. Als u live master-manifest updates wilt inschakelen, stelt u de updatefrequentie (in minuten) in door de eigenschap `NetworkConfiguration.masterUpdateInterval` in te stellen.
1. U kunt succesvolle manifestupdates optioneel bijhouden door te luisteren naar de gebeurtenis `MediaPlayerItemEvent.MASTER_UPDATED`.
