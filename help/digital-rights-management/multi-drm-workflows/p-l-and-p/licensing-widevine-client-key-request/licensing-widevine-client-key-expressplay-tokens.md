---
description: U kunt ExpressSplaytokens voor hun gecodeerde inhoud genereren door tokenverzoeken naar de juiste Expressplaytokenserver te verzenden.
title: Expressplaytokens
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '131'
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