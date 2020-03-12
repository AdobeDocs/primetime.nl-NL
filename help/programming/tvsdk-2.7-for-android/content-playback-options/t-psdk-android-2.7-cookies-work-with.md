---
description: U kunt TVSDK gebruiken om willekeurige gegevens in koekjeskopballen voor zittingsbeheer, poorttoegang, etc. te verzenden.
seo-description: U kunt TVSDK gebruiken om willekeurige gegevens in koekjeskopballen voor zittingsbeheer, poorttoegang, etc. te verzenden.
seo-title: Werken met cookies
title: Werken met cookies
uuid: a3b966fd-1263-458d-8303-b4e898372ee1
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

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

Maak een cookie `cookieManager` en voeg uw cookies voor de URI&#39;s toe aan uw cookieStore.

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

TVSDK vraagt dit `cookieManager` tijdens runtime af, controleert of er cookies aan de URL zijn gekoppeld en gebruikt deze cookies automatisch.

De gebeurtenis MediaPlayerEvent.COOKIES_UPDATED wordt geroepen wanneer C++ koekjes worden bijgewerkt. Deze cookiesUpdatedEvent heeft een methode getCookieString() die een tekenreekswaarde voor de cookie retourneert.

Hieronder ziet u een voorbeeldcodefragment:

```
private final CookiesUpdatedEventListener cookiesUpdatedEventListener = new CookiesUpdatedEventListener()  
{ 
@Override 
public void onCookiesUpdated(CookiesUpdatedEvent cookiesUpdatedEvent) 
 { 
 String cookieStr = cookiesUpdatedEvent.getCookieString();  
 logger.i(LOG_TAG + "::MediaPlayer.CookiesUpdatedEventListener#onCookiesUpdated()", "cookieStr " + cookieStr);  
 }  
};
```

