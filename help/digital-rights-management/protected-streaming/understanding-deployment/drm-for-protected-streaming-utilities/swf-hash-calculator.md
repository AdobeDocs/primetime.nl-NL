---
description: Het hulpmiddel van de Rekenmachine van de Hash van SWF berekent de samenvatting van een toepassing van de SWF die in een dossier wordt gevestigd.
title: SWF hash-calculator
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
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
