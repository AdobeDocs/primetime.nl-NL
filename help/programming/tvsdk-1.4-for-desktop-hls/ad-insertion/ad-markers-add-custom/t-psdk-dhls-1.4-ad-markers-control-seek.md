---
description: U kunt het standaardgedrag negeren voor de manier waarop TVSDK via advertenties zoekt wanneer u aangepaste advertentiemarkeringen gebruikt.
title: Afspeelgedrag bepalen voor zoeken op aangepaste advertentiemarkeringen
exl-id: c821e0be-1490-4b5f-8f9f-bffdfb1a982d
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# Afspeelgedrag bepalen voor zoeken op aangepaste advertentiemarkeringen{#control-playback-behavior-for-seeking-over-custom-ad-markers}

U kunt het standaardgedrag negeren voor de manier waarop TVSDK via advertenties zoekt wanneer u aangepaste advertentiemarkeringen gebruikt.

Wanneer een gebruiker gedeelten zoekt die afkomstig zijn van de plaatsing van aangepaste advertentiemarkeringen, slaat TVSDK de advertenties standaard over. Dit kan verschillen van het huidige afspeelgedrag voor standaard en eindpunten.

U kunt TVSDK de opdracht geven de afspeelkop te verplaatsen naar het begin van de laatst overgeslagen aangepaste advertentie wanneer de gebruiker voorbij een of meer aangepaste advertenties zoekt.

1. Een instantie Metadata configureren met de `DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED` opsomming ingesteld op de tekenreekswaarde &quot;true&quot; (niet als een Booleaanse waarde) `true`).

1. Een `MediaResource` instantie, de extra configuratieopties doorgeven aan `TimeRangeCollection.toMetadata`. Deze methode ontvangt aanvullende configuratieopties via een andere algemene metagegevensstructuur.
