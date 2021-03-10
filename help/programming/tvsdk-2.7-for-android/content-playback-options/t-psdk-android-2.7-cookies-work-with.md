---
description: U kunt TVSDK gebruiken om willekeurige gegevens in koekjeskopballen voor zittingsbeheer, poorttoegang, etc. te verzenden.
title: Werken met cookies
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '236'
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

Maak een `cookieManager` en voeg uw cookies voor de URI&#39;s toe aan uw cookieStore.

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

TVSDK vraagt dit `cookieManager` bij uitvoering, controleert of er cookies zijn gekoppeld aan de URL en gebruikt automatisch die cookies.

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

