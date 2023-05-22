---
description: U kunt deze functie inschakelen en controleren op verwante gebeurtenissen.
title: Live update master-manifest gebruiken
exl-id: 02cb3116-cc30-4139-841b-8d6297214b8b
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '56'
ht-degree: 0%

---

# Live update master-manifest gebruiken{#use-live-master-manifest-update}

U kunt deze functie inschakelen en controleren op verwante gebeurtenissen.

1. Als u live master-manifest updates wilt inschakelen, stelt u de updatefrequentie (in minuten) in door de instelling van de optie `NetworkConfiguration.masterUpdateInterval` eigenschap.
1. Optioneel, spoor succesvolle duidelijke updates door naar het `MediaPlayerItemEvent.MASTER_UPDATED` gebeurtenis.
