---
description: Voordat u de meeste methoden van de TVSDK-speler kunt gebruiken, moet de speler een geldige status hebben.
seo-description: Voordat u de meeste methoden van de TVSDK-speler kunt gebruiken, moet de speler een geldige status hebben.
seo-title: Wacht op een geldige status
title: Wacht op een geldige status
uuid: e13201d7-b217-4d01-bdb7-a71855e3500e
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 0%

---


# Wacht op een geldige status{#wait-for-a-valid-state}

Voordat u de meeste methoden van de TVSDK-speler kunt gebruiken, moet de speler een geldige status hebben.

De speler doorloopt verschillende statussen. Wachten tot de speler de juiste status heeft, zorgt ervoor dat de mediabron correct is geladen. Als de speler niet in minstens de vereiste status is, werpen vele spelermethodes `IllegalStateException`.

De vereiste status is meestal `PTMediaPlayerStatusReady`.
