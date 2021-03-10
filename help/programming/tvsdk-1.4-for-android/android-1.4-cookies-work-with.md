---
description: U kunt TVSDK gebruiken om willekeurige gegevens in koekjeskopballen voor zittingsbeheer, poorttoegang, etc. te verzenden.
title: Werken met cookies
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '246'
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

1. Maak een `cookieManager` en voeg uw cookies voor de URI&#39;s toe aan uw `cookieStore`.

   Bijvoorbeeld:

   >[!IMPORTANT]
   >
   >Wanneer 302 omleiding wordt toegelaten, kan het advertentieverzoek aan een domein worden opnieuw gericht dat van het domein verschillend is waartot het koekje behoort.

   ```java
   CookieManager cookieManager= new CookieManager(); 
   CookieHandler.setDefault(cookieManager);  
   HttpCookie cookie=new HttpCookie("lang","fr"); 
   cookie.setDomain("twitter.com");  
   cookie.setPath("/"); 
   cookie.setVersion(0); 
   cookieManager.getCookieStore().add(newURI("https://twitter.com/"),cookie);
   ```

   TVSDK vraagt deze cookieManager bij uitvoering op, controleert of er cookies zijn gekoppeld aan de URL en gebruikt deze automatisch.

   Een andere optie is om `cookieHeaders` in `NetworkConfiguration` te gebruiken om een willekeurige kokerkoord van de koekjeskopbal te plaatsen dat voor verzoeken moet worden gebruikt. Standaard wordt deze cookieheader alleen met belangrijke aanvragen verzonden. Om de koekjeskopbal met alle verzoeken te verzenden, gebruik `NetworkConfiguration` methode `setUseCookieHeadersForAllRequests`:

```java
   NetworkConfiguration networkConfiguration = new NetworkConfiguration(); 
    
   Metadata cookie = new MetadataNode(); 
   cookie.setValue("reqPayload", “1234567”); 
   networkConfiguration.setCookieHeaders(cookie); 
   networkConfiguration.setUseCookieHeadersForAllRequests( true ); 
    
   // Set NetworkConfiguration as Metadata:                                                                   
   MetadataNode resourceMetadata = new MetadataNode(); 
   resourceMetadata.setNode(DefaultMetadataKeys.NETWORK_CONFIGURATION.getValue(),  
                            networkConfiguration); 
    
   // Call MediaResource.createFromURL to set the metadata: 
   MediaResource resource = MediaResource.createFromURL(url, resourceMetadata); 
   // Load the resource 
   mediaPlayer.replaceCurrentItem(resource);
```
