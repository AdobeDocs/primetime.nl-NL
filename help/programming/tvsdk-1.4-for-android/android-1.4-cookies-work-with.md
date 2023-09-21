---
description: U kunt TVSDK gebruiken om willekeurige gegevens in koekjeskopballen voor zittingsbeheer, poorttoegang, etc. te verzenden.
title: Werken met cookies
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
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

1. Een `cookieManager` en voeg uw cookies voor de URI&#39;s toe aan uw `cookieStore`.

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

   Een andere optie is om te gebruiken `cookieHeaders` in `NetworkConfiguration` om een willekeurige headertekenreeks voor cookies in te stellen die moet worden gebruikt voor aanvragen. Standaard wordt deze cookieheader alleen met sleutelverzoeken verzonden. Als u de cookieheader met alle aanvragen wilt verzenden, gebruikt u de `NetworkConfiguration` methode `setUseCookieHeadersForAllRequests`:

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
