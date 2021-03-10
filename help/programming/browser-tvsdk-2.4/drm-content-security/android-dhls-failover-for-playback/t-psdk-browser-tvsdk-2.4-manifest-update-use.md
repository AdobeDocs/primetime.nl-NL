---
description: U kunt deze functie inschakelen en controleren op verwante gebeurtenissen.
title: Live update master-manifest gebruiken
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '56'
ht-degree: 0%

---


# Live update master-manifest gebruiken{#use-live-master-manifest-update}

U kunt deze functie inschakelen en controleren op verwante gebeurtenissen.

1. Als u live master-manifest updates wilt inschakelen, stelt u de updatefrequentie (in minuten) in door de eigenschap `NetworkConfiguration.masterUpdateInterval` in te stellen.
1. U kunt succesvolle manifestupdates optioneel bijhouden door te luisteren naar de gebeurtenis `MediaPlayerItemEvent.MASTER_UPDATED`.
