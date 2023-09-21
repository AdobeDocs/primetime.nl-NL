---
description: U kunt TVSDK gebruiken om willekeurige gegevens in koekjeskopballen voor zittingsbeheer, poorttoegang, etc. te verzenden.
title: Werken met cookies
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
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

1. Gebruik de `cookieHeaders` eigenschap in `NetworkConfiguration` een cookie instellen. De `cookieHeaders` eigenschap is een object Metadata en u kunt sleutelwaardeparen toevoegen aan dit object om in de cookie-header te worden opgenomen.

   Bijvoorbeeld:

   ```
   var metadata:Metadata = new Metadata(); 
   metadata.setValue(“val1”, “12345”); 
   metadata.setValue(“val2”, “abcd”); 
   
   networkConfiguration.cookieHeaders = metadata;
   ```

   Cookiekoppen worden standaard alleen met hoofdaanvragen verzonden. Als u cookie-headers wilt verzenden met alle aanvragen, stelt u de optie `NetworkConfiguration` eigenschap `useCookieHeadersForAllRequests` naar waar.

1. Om ervoor te zorgen dat `NetworkConfiguration` werkt, stelt u deze in als metagegevens:

   ```
   var networkConfiguration:NetworkConfiguration = new NetworkConfiguration(); 
   networkConfiguration.forceNativeNetworking = true; 
   var resourceMetadata:Metadata = new Metadata(); 
   resourceMetadata.setMetadata(DefaultMetadataKeys.NETWORK_CONFIGURATION_KEY,  
                                networkConfiguration);
   ```

1. Geef de metagegevens van de vorige stap op wanneer u een `MediaResource`.

   Als u bijvoorbeeld de opdracht `createFromURL` Voer de volgende gegevens in:

   ```
   var resource:MediaResource = MediaResource.createFromURL(url, resourceMetadata);
   ```
