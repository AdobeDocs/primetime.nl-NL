---
description: U kunt metagegevens aanpassen en invoegen.
title: Metagegevens voor toevoegen en invoegen aanpassen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---

# Metagegevens voor toevoegen en invoegen aanpassen{#customize-ad-insertion-metadata}

U kunt metagegevens aanpassen en invoegen.

1. Stel een time-out in voor de metagegevens van advertenties voor onopgeloste mogelijkheden.

   De standaardwaarde voor deze time-out is 20 seconden.
1. Als u de waarde wilt wijzigen in 10 seconden, voert u het volgende in:

   ```js
   auditudeSettings.timeout = 10000; //this value is specified in milliseconds
   ```

   De `timeout` eigenschap wordt gedefinieerd in het dialoogvenster `AdvertisingMetadata` en deze time-out kan worden ingesteld voor alle aangepaste en uit de `AdvertisingMetadata` klasse. Als gebruikers bijvoorbeeld aangepaste instellingen voor een FreeWheel-oplosser definiëren, kunnen ze een standaardtime-out instellen met deze instelling.

1. Maken `MediaPlayerItemConfig` met de advertentie-instellingen in stap 2.

   ```js
   var config = new AdobePSDK.MediaPlayerItemConfig(); 
   config.advertisingMetadata = auditudeSettings;
   ```

1. Gebruik deze configuratie wanneer het roepen `replaceCurrentResource` op `MediaPlayer`.

   ```js
   player.replaceCurrentResource(mediaResource, config);
   ```
