---
description: U kunt TVSDK gebruiken om willekeurige gegevens in koekjeskopballen voor zittingsbeheer, poorttoegang, etc. te verzenden.
title: Werken met cookies
exl-id: 7f0e7d77-0718-4df7-8380-0e9351f588bc
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# Werken met cookies {#work-with-cookies}

U kunt TVSDK gebruiken om willekeurige gegevens in koekjeskopballen voor zittingsbeheer, poorttoegang, etc. te verzenden.

Hier volgt een voorbeeld van een aanvraag aan de sleutelserver met verificatie:

1. Uw klant meldt zich in een browser aan bij uw website en zijn aanmeldingsgegevens laten zien dat deze klant inhoud mag bekijken.
1. Op basis van wat de licentieserver verwacht, genereert uw toepassing een verificatietoken.

   Deze waarde wordt doorgegeven aan TVSDK.
1. TVSDK stelt deze waarde in in de cookie-header.
1. Wanneer TVSDK bij de sleutelserver een verzoek indient om een sleutel te krijgen om de inhoud te decoderen, bevat het verzoek de authentificatiewaarde in de koekjeskopbal.

   De toetsserver weet dat de aanvraag geldig is.

Werken met cookies:

1. Een `cookieManager` en voeg uw cookies voor de URI&#39;s toe aan uw cookieStore.

   Bijvoorbeeld:

   ```java
   CookieManager cookieManager=new CookieManager(); 
   CookieHandler.setDefault(cookieManager);  
   HttpCookie cookie=new HttpCookie("lang","fr"); 
   cookie.setDomain("twitter.com");  
   cookie.setPath("/"); 
   cookie.setVersion(0); 
   cookieManager.getCookieStore().add(newURI("https://twitter.com/"),cookie);
   ```

   >[!TIP]
   >
   >Wanneer 302 omleiding wordt toegelaten, kan het advertentieverzoek aan een domein worden opnieuw gericht dat van het domein verschillend is waartot het koekje behoort.

   TVSDK vraagt dit `cookieManager` controleert tijdens runtime of er cookies zijn gekoppeld aan de URL en gebruikt deze cookies automatisch.

   Als de cookies tijdens het afspelen in de toepassing moeten worden bijgewerkt, gebruikt u `networkConfiguration.setCookieHeaders` API&#39;s als de update worden weergegeven in de cookie store van JAVA.

   `networkConfiguration.setCookieHeaders` API stelt de cookies in op de C++ CookieStore van TVSDK.

   Wanneer u JAVA-cookies gebruikt en deze deelt tussen Application en TVSDK, gebruikt u JAVA CookieStore om de cookies alleen te beheren.

   Voordat het afspelen wordt geïnitialiseerd, stelt u de cookies in op CookieStore met gebruik van Cookie Manager zoals hierboven vermeld.

   Het cookie dat is opgeslagen in CookieStore wordt automatisch opgehaald door TVSDK.

   Als een koekjeswaarde later tijdens playback moet worden bijgewerkt, vraag het zelfde toevoegen methode van CookieStore met de zelfde sleutel en een nieuw waardegebied.

   Ook ingesteld
   `networkConfiguration.setReadSetCookieHeader`(false) voordat wordt aangeroepen
   `config.setNetworkConfiguration(networkConfiguration)`

   >[!NOTE]
   >
   >Nadat u deze &#39;setReadSetCookieHeader&#39; hebt ingesteld op false, stelt u de cookies voor de belangrijkste aanvragen in met behulp van JAVA-cookiebeheer.

   `onCookiesUpdated(CookiesUpdatedEvent cookiesUpdatedEvent)`
Deze callback-API wordt geactiveerd wanneer er een update is in C++ cookies (cookies die afkomstig zijn van http response). De toepassing moet naar deze callback luisteren en kan hun JAVA CookieStore dienovereenkomstig bijwerken zodat hun vraag van het Netwerk in JAVA de koekjes zoals hieronder kan gebruiken:

   ```
   private final CookiesUpdatedEventListener cookiesUpdatedEventListener = new CookiesUpdatedEventListener() {
   @Override
   public void onCookiesUpdated(CookiesUpdatedEvent cookiesUpdatedEvent) {
   List<HttpCookie> cookies = cookiesUpdatedEvent.getHttpCookies();
   for(int i = 0; i < cookies.size(); i++)
   { HttpCookie c = cookies.get(i); // To set this cookie on to the cookie store //c.setValue("newValue"); //If you want to modify the value of the cookie URI myuri = URI.create(cookiesUpdatedEvent.getDomainString()); cookieManager.getCookieStore().add(myuri,c); }
   }
   }
   ```
