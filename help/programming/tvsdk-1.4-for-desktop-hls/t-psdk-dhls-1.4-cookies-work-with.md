---
description: U kunt TVSDK gebruiken om willekeurige gegevens in koekjeskopballen voor zittingsbeheer, poorttoegang, etc. te verzenden.
title: Werken met cookies
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---


# Werken met cookies{#work-with-cookies}

U kunt TVSDK gebruiken om willekeurige gegevens in koekjeskopballen voor zittingsbeheer, poorttoegang, etc. te verzenden.

Hier is een voorbeeld met wat type authentificatie wanneer het doen van verzoeken aan de belangrijkste server:

1. Uw klant meldt zich in een browser aan bij uw website en zijn aanmeldingsgegevens laten zien dat hij of zij inhoud mag bekijken.
1. Uw toepassing genereert een verificatietoken op basis van wat door de licentieserver wordt verwacht. Geef die waarde door aan TVSDK.
1. TVSDK stelt die waarde in de cookieheader in.
1. Wanneer TVSDK bij de sleutelserver een verzoek indient om een sleutel te krijgen om de inhoud te decrypteren, bevat dat verzoek de authentificatiewaarde in de koekjeskopbal, zodat weet de belangrijkste server dat het verzoek geldig is.

Werken met cookies:

1. Gebruik de eigenschap `cookieHeaders` in `NetworkConfiguration` om een cookie in te stellen. De eigenschap `cookieHeaders` is een object Metagegevens en u kunt sleutelwaardeparen toevoegen aan dit object om in de cookiekop te worden opgenomen.

   Bijvoorbeeld:

   ```
   var metadata:Metadata = new Metadata(); 
   metadata.setValue(“val1”, “12345”); 
   metadata.setValue(“val2”, “abcd”); 
   
   networkConfiguration.cookieHeaders = metadata;
   ```

   Cookiekoppen worden standaard alleen met hoofdaanvragen verzonden. Om koekjeskopballen met alle verzoeken te verzenden, plaats `NetworkConfiguration` bezit `useCookieHeadersForAllRequests` aan waar.

1. Om ervoor te zorgen dat `NetworkConfiguration` werkt, plaats het als meta-gegevens:

   ```
   var networkConfiguration:NetworkConfiguration = new NetworkConfiguration(); 
   networkConfiguration.forceNativeNetworking = true; 
   var resourceMetadata:Metadata = new Metadata(); 
   resourceMetadata.setMetadata(DefaultMetadataKeys.NETWORK_CONFIGURATION_KEY,  
                                networkConfiguration);
   ```

1. Geef de metagegevens van de vorige stap op wanneer u een `MediaResource` maakt.

   Als u bijvoorbeeld de methode `createFromURL` gebruikt, voert u de volgende informatie in:

   ```
   var resource:MediaResource = MediaResource.createFromURL(url, resourceMetadata);
   ```

