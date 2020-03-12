---
description: De aanvraag en het antwoord voor machtigingen worden doorgegeven via een wederzijds geverifieerde SSL-verbinding tussen de licentieserver en de machtigingsservice van de klant.
seo-description: De aanvraag en het antwoord voor machtigingen worden doorgegeven via een wederzijds geverifieerde SSL-verbinding tussen de licentieserver en de machtigingsservice van de klant.
seo-title: SEES Public API
title: SEES Public API
uuid: f3a17d61-04ee-4bdb-9d64-a98066c6d1c8
translation-type: tm+mt
source-git-commit: 15403abbd53486e1faa2146cda83f41bd8116632

---


# SEES Public API {#sees-public-api}

De aanvraag en het antwoord voor machtigingen worden doorgegeven via een wederzijds geverifieerde SSL-verbinding tussen de licentieserver en de machtigingsservice van de klant.

Het URI-schema HTTPS ( [https://tools.ietf.org/html/rfc7230#section-2.7.2](https://tools.ietf.org/html/rfc7230#section-2.7.2)) wordt gebruikt om het eindpunt van de machtiging te definiëren en de HTTP POST-aanvraagmethode ( [https://tools.ietf.org/html/rfc7231#section-4.3.3](https://tools.ietf.org/html/rfc7231#section-4.3.3)) wordt gebruikt voor de aanvraag. Het eindpunt van de machtiging en een markering die de &#39;back-end&#39;-machtiging aangeeft, zijn vereist en moeten in het beleid bij het verpakken worden opgenomen.

## Machtigingsaanvraag {#section_BFBFEF0795CA46D6842C479256B95F95}

De hoofdtekst van de machtigingsaanvraag is een JSON-object dat is gedefinieerd zoals hieronder wordt weergegeven.

**Objectdefinitie voor JSON-machtiging**

```
{ 
 "title" : "Entitlement Request", 
 "type" : "object", 
 "properties" : { 
  "messageID" : { 
   "type" : "string", 
   "description" : "Unique ID for this message (GUID).  Used to confirm that the subsequent response is actually for this request." 
  }, 
  "version" : { 
   "type" : "integer", 
   "description" : "Version number of the protocol, currently 1." 
  }, 
  "requestType" : { 
   "type" : "integer", 
   "description" : "Request type. 1 - time based entitlement request, 2 - device registration entitlement request 3 - device bound entitlement request." 
  }, 
  "contentID" : { 
   "type" : "string", 
   "description" : "Content ID (GUID) that was given to the content during packaging time." 
  }, 
  "customerCookie" : { 
   "type" : "string", 
   "description" : "Customer cookie. Cookie is just arbitrary string up to 32 characters long." 
  } 
    }, 
 "required" : ["messageID", "version", "contentID"] 
}
```

## Reactie op machtiging {#section_F15A9FD6BAD946B3B4C5C14612F90154}

De hoofdtekst van de machtigingsreactie is een JSON-object.

**JSON-objectdefinitie voor machtigingsreactie**

```
{ 
  "title" : "Entitlement Response", 
  "type" : "object", 
  "properties" : { 
    "messageID" : { 
    "type" : "string", 
    "description" : "Unique ID from the Entitlement Request message.   
      Must match, or entitlement will be denied." 
  }, 
  "version" : { 
    "type" : "integer", 
    "description" : "Version number of the protocol; must be <= the version number  
      from the Entitlement Request message." 
  }, 
  "isAllowed" : { 
    "type" : "boolean", 
    "description" : "Grant the license or not." 
  }, 
  "epTokenURL" : { 
    "type" : "string", 
    "description" : "ExpressPlay Token URL" 
  }, 
  "error" : { 
    "type" : "integer", 
    "description" : "An error number produced by the entitlement server.  
      Will be passed to the client as the 'code' field of the server error response." 
  }, 
  "errorText" : { 
    "type" : "string", 
    "description" : "Additional error information produced by the entitlement server.  
      Will be passed to the client as the 'text' field of the server error response." 
  }, 
  "required" : ["messageID", "version", "isAllowed", "epTokenURL"] 
}
```
