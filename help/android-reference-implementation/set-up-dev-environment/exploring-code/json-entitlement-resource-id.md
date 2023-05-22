---
title: JSON-object voor machtigingsbron-id
description: Het volgende codeblok geeft een voorbeeld van een JSON-object wanneer de machtigingsbron-id een eenvoudige tekstreeks is.
exl-id: 396c43e7-404a-40f5-8113-a720e2c834e7
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---

# JSON-object voor machtigingsbron-id {#json-object-for-entitlement-resource-id}

Het volgende codeblok geeft een voorbeeld van een JSON-object wanneer de machtigingsbron-id een eenvoudige tekstreeks is. In dit geval is de bron-id de tekenreeks &quot;resource&quot;.

```
"metadata" : { 
"entitlement" : { 
"id" : "resource" 
} 
}
```

Het volgende codeblok geeft een voorbeeld van een JSON-object wanneer de machtigingsbron-id een met HTML gecodeerde mRSS-tekenreeks is.

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
