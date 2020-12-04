---
seo-title: JSON-object voor machtigingsbron-id
title: JSON-object voor machtigingsbron-id
uuid: f5b659da-1732-404c-bf00-d32a0ae39aa1
description: Het volgende codeblok geeft een voorbeeld van een JSON-object wanneer de machtigingsbron-id een eenvoudige tekstreeks is.
seo-description: Het volgende codeblok geeft een voorbeeld van een JSON-object wanneer de machtigingsbron-id een eenvoudige tekstreeks is.
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---


# JSON-object voor machtigingsresource-id {#json-object-for-entitlement-resource-id}

Het volgende codeblok geeft een voorbeeld van een JSON-object wanneer de machtigingsbron-id een eenvoudige tekstreeks is. In dit geval is de bron-id de tekenreeks &quot;resource&quot;.

```
"metadata" : { 
"entitlement" : { 
"id" : "resource" 
} 
}
```

Het volgende codeblok geeft een voorbeeld van een JSON-object wanneer de machtigingsbron-id een HTML-gecodeerde mRSS-tekenreeks is.

```
<rss version="2.0" xmlns:media="https://search.yahoo.com/mrss/"> 
<channel> 
<title>REF_ADOBE</title> 
<item> 
<title>Adobe Primetime Reference</title> 
<guid>1234</guid> 
<media:rating scheme="urn:v-chip">TV-PG</media:rating> 
</item> 
</channel> 
</rss>
```

De volgende mRSS-tekenreeks wordt gebruikt als bron-id.

```
"metadata" : { 
    "entitlement" : { 
        "id" : "<rss version=&quot;2.0&quot; 
        xmlns:media=&quot; 
        https://search.yahoo.com/mrss/&quot; 
        ><channel><title>REF_ADOBE</title><item> 
        <title>Adobe Primetime Reference</title><guid> 
        1234</guid><media:rating scheme=&quot;urn:v-chip&quot;> 
        TV-PG</media:rating></item></channel></rss>" 
        } 
} 
```
