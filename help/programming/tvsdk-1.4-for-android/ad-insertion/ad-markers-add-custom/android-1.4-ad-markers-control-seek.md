---
description: U kunt het standaardgedrag negeren voor de manier waarop TVSDK via advertenties zoekt wanneer u aangepaste advertentiemarkeringen gebruikt.
seo-description: U kunt het standaardgedrag negeren voor de manier waarop TVSDK via advertenties zoekt wanneer u aangepaste advertentiemarkeringen gebruikt.
seo-title: Afspeelgedrag bepalen voor zoeken op aangepaste advertentiemarkeringen
title: Afspeelgedrag bepalen voor zoeken op aangepaste advertentiemarkeringen
uuid: cf973caf-be29-46ce-bfa4-651e7653f8d4
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---


# Afspeelgedrag bepalen voor zoeken op aangepaste advertentiemarkeringen{#control-playback-behavior-for-seeking-over-custom-ad-markers}

U kunt het standaardgedrag negeren voor de manier waarop TVSDK via advertenties zoekt wanneer u aangepaste advertentiemarkeringen gebruikt.

Wanneer een gebruiker gedeelten zoekt die afkomstig zijn van de plaatsing van aangepaste advertentiemarkeringen, slaat TVSDK de advertenties standaard over. Dit kan verschillen van het huidige afspeelgedrag voor standaard en eindpunten.

U kunt TVSDK de opdracht geven de afspeelkop te verplaatsen naar het begin van de laatst overgeslagen aangepaste advertentie wanneer de gebruiker voorbij een of meer aangepaste advertenties zoekt.

1. Configureer een instantie Metadata met de opsomming `DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED` ingesteld op de tekenreekswaarde &quot;true&quot; (niet als een Booleaanse waarde `true`).

   ```java
   Metadata metadata = new MetadataNode(); 
   metadata.setValue(DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED.getValue(),"true");
   ```

1. Creeer en vorm een `MediaResource` instantie, die de extra configuratieopties tot `TimeRangeCollection.toMetadata` overgaat. Deze methode ontvangt aanvullende configuratieopties via een andere algemene metagegevensstructuur.

   ```java
   MediaResource mediaResource =  
     MediaResource.createFromUrl("www.example.com/video/test_video.m3u8", 
                                 timeRanges.toMetadata(metadata));
   ```

