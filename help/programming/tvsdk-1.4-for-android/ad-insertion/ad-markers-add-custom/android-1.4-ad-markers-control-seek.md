---
description: U kunt het standaardgedrag negeren voor de manier waarop TVSDK via advertenties zoekt wanneer u aangepaste advertentiemarkeringen gebruikt.
title: Afspeelgedrag bepalen voor zoeken op aangepaste advertentiemarkeringen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# Afspeelgedrag bepalen voor zoeken op aangepaste advertentiemarkeringen{#control-playback-behavior-for-seeking-over-custom-ad-markers}

U kunt het standaardgedrag negeren voor de manier waarop TVSDK via advertenties zoekt wanneer u aangepaste advertentiemarkeringen gebruikt.

Wanneer een gebruiker gedeelten zoekt die afkomstig zijn van de plaatsing van aangepaste advertentiemarkeringen, slaat TVSDK de advertenties standaard over. Dit kan verschillen van het huidige afspeelgedrag voor standaard en eindpunten.

U kunt TVSDK de opdracht geven de afspeelkop te verplaatsen naar het begin van de laatst overgeslagen aangepaste advertentie wanneer de gebruiker voorbij een of meer aangepaste advertenties zoekt.

1. Een instantie Metadata configureren met de `DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED` opsomming ingesteld op de tekenreekswaarde &quot;true&quot; (niet als een Booleaanse waarde) `true`).

   ```java
   Metadata metadata = new MetadataNode(); 
   metadata.setValue(DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED.getValue(),"true");
   ```

1. Een `MediaResource` instantie, de extra configuratieopties doorgeven aan `TimeRangeCollection.toMetadata`. Deze methode ontvangt aanvullende configuratieopties via een andere algemene metagegevensstructuur.

   ```java
   MediaResource mediaResource =  
     MediaResource.createFromUrl("www.example.com/video/test_video.m3u8", 
                                 timeRanges.toMetadata(metadata));
   ```
