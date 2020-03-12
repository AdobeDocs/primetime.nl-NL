---
description: U kunt metagegevens aanpassen en invoegen.
seo-description: U kunt metagegevens aanpassen en invoegen.
seo-title: Metagegevens voor toevoegen en invoegen aanpassen
title: Metagegevens voor toevoegen en invoegen aanpassen
uuid: 047470d3-45bd-48be-82ce-4e9d9fe6ea10
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Metagegevens voor toevoegen en invoegen aanpassen{#customize-ad-insertion-metadata}

U kunt metagegevens aanpassen en invoegen.

1. Stel een time-out in voor de metagegevens van advertenties voor onopgeloste mogelijkheden.

   De standaardwaarde voor deze time-out is 20 seconden.
1. Als u de waarde wilt wijzigen in 10 seconden, voert u het volgende in:

   ```js
   auditudeSettings.timeout = 10000; //this value is specified in milliseconds
   ```

   De `timeout` eigenschap wordt gedefinieerd in de `AdvertisingMetadata` klasse en deze time-out kan worden ingesteld voor alle aangepaste advertentie-instellingen die uit de `AdvertisingMetadata` klasse voortkomen. Als gebruikers bijvoorbeeld aangepaste instellingen voor een FreeWheel-oplosser definiëren, kunnen ze een standaardtime-out instellen met deze instelling.

1. Maak `MediaPlayerItemConfig` met de advertentie-instellingen in stap 2.

   ```js
   var config = new AdobePSDK.MediaPlayerItemConfig(); 
   config.advertisingMetadata = auditudeSettings;
   ```

1. Gebruik deze configuratie wanneer het roepen `replaceCurrentResource` op `MediaPlayer`.

   ```js
   player.replaceCurrentResource(mediaResource, config);
   ```

