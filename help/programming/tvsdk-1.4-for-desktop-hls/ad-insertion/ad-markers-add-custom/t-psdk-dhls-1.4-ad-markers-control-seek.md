---
description: U kunt het standaardgedrag negeren voor de manier waarop TVSDK via advertenties zoekt wanneer u aangepaste advertentiemarkeringen gebruikt.
seo-description: U kunt het standaardgedrag negeren voor de manier waarop TVSDK via advertenties zoekt wanneer u aangepaste advertentiemarkeringen gebruikt.
seo-title: Afspeelgedrag bepalen voor zoeken op aangepaste advertentiemarkeringen
title: Afspeelgedrag bepalen voor zoeken op aangepaste advertentiemarkeringen
uuid: 926299c6-9c23-457d-b836-08432e4e169e
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---


# Afspeelgedrag bepalen voor zoeken op aangepaste advertentiemarkeringen{#control-playback-behavior-for-seeking-over-custom-ad-markers}

U kunt het standaardgedrag negeren voor de manier waarop TVSDK via advertenties zoekt wanneer u aangepaste advertentiemarkeringen gebruikt.

Wanneer een gebruiker gedeelten zoekt die afkomstig zijn van de plaatsing van aangepaste advertentiemarkeringen, slaat TVSDK de advertenties standaard over. Dit kan verschillen van het huidige afspeelgedrag voor standaard en eindpunten.

U kunt TVSDK de opdracht geven de afspeelkop te verplaatsen naar het begin van de laatst overgeslagen aangepaste advertentie wanneer de gebruiker voorbij een of meer aangepaste advertenties zoekt.

1. Configureer een instantie Metadata met de opsomming `DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED` ingesteld op de tekenreekswaarde &quot;true&quot; (niet als een Booleaanse waarde `true`).

1. Creeer en vorm een `MediaResource` instantie, die de extra configuratieopties tot `TimeRangeCollection.toMetadata` overgaat. Deze methode ontvangt aanvullende configuratieopties via een andere algemene metagegevensstructuur.

