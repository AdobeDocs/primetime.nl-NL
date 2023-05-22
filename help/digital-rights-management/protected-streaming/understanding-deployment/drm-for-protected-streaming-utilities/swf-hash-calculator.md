---
description: Het hulpmiddel van de Rekenmachine van de Hash van SWF berekent de samenvatting van een toepassing van de SWF die in een dossier wordt gevestigd.
title: SWF hash-calculator
exl-id: 245254fe-2fcb-41e8-94bd-0cbc8b39b2b5
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '65'
ht-degree: 0%

---

# SWF hash-calculator{#swf-hash-calculator}

Het hulpmiddel van de Rekenmachine van de Hash van SWF berekent de samenvatting van een toepassing van de SWF die in een dossier wordt gevestigd.

Typ de volgende tekst om de hasher uit te voeren:

```
Hasher.bat 
<i class="+ topic ph hi-d="" i "="">
  filename.swf
</i class="+ topic>
```

of

```
java -jar libs/flashaccess-hasher.jar 
<i class="+ topic ph hi-d="" i "="">
  filename.swf
</i class="+ topic>
```

Het hulpprogramma geeft het volgende bericht weer:

```
SWF Hash: 
<i class="+ topic ph hi-d="" i "="">
  hash-of-swf
</i class="+ topic>
```

U kunt deze waarde gebruiken om de SWF-samenvatting op te geven in [!DNL flashaccess-tenant.xml].
