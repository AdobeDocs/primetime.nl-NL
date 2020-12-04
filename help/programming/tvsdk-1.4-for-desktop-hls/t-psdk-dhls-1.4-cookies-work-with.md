---
description: U kunt TVSDK gebruiken om willekeurige gegevens in koekjeskopballen voor zittingsbeheer, poorttoegang, etc. te verzenden.
seo-description: U kunt TVSDK gebruiken om willekeurige gegevens in koekjeskopballen voor zittingsbeheer, poorttoegang, etc. te verzenden.
seo-title: Werken met cookies
title: Werken met cookies
uuid: 7586a5a7-9914-403b-86a9-fbdd28664b07
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '256'
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

1. Gebruik de eigenschap `cookieHeaders` in `NetworkConfiguration` om een cookie in te stellen. De eigenschap `cookieHeaders` is een object Metagegevens en u kunt sleutelwaardeparen aan dit object toevoegen om in de cookie-header te worden opgenomen.

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

