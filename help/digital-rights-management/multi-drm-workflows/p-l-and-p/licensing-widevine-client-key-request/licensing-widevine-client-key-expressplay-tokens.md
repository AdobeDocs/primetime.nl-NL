---
description: U kunt ExpressSplaytokens voor hun gecodeerde inhoud genereren door tokenverzoeken naar de juiste Expressplaytokenserver te verzenden.
seo-description: U kunt ExpressSplaytokens voor hun gecodeerde inhoud genereren door tokenverzoeken naar de juiste Expressplaytokenserver te verzenden.
seo-title: Expressplaytokens
title: Expressplaytokens
uuid: 6103e1b2-127d-4758-a589-15f0f3c73db1
translation-type: tm+mt
source-git-commit: d0ba1f98b16f6350ae842ca2ce1261bf49dd8a66
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---


# Expressplaytokens {#expressplay-tokens}

U kunt ExpressSplaytokens voor hun gecodeerde inhoud genereren door tokenverzoeken naar de juiste Expressplaytokenserver te verzenden.

Een voorbeeld is de volgende URL:

```
https://wv-gen.service.expressplay.com/hms/wv/
token?customerAuthenticator=<your expressplay customer authenticator>
&kid=fd1a706ac2b36002888f6d4a414333c3
&contentKey=5438b719bf47a2f5678237477db2f9e6
&securityLevel=1
&hdcpOutputControl=0
```

De opslag-id van de inhoudscoderingssleutel of de CEKSID die aan de parameter `kid` wordt gegeven en de coderingssleutel voor inhoud of CEK die aan de parameter `contentKey` wordt gegeven, moeten overeenkomen met de opslag-id van de coderingssleutel voor inhoud en de coderingssleutel voor inhoud die voor het maken van pakketten wordt gebruikt. De volgende tekst is een voorbeeld van de tokenserverreactie:

```
https://wv.service.expressplay.com/hms/wv/rights/
?ExpressPlayToken=AQAAABIDKbgAAABQbt68jktab0YRY-r9mo6VP
 VqDDvkHq78x4V9_AyBUTtcNFHw5JtNKlKrMt-4HBdJ3Fopr7fqFSBp
 SJ4o-d8teAkUZUtW3Od5V-SHsCLnAlbFW84K71h2xNUiMAvRcUFBG3bjxMQ
```

U kunt dan

* de geretourneerde URL en query gebruiken als de URL van de licentieserver, of
* neem uit de vraag van URL en geef in ExpressPlayToken afzonderlijk als kopbal van de POST van HTTP door