---
title: SWF Hash-calculator
description: SWF Hash-calculator
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '52'
ht-degree: 0%

---

# SWF Hash-calculator{#swf-hash-calculator}

Het hulpprogramma Hash Calculator van SWF heeft de samenvatting berekend van een SWF-toepassing in een bestand. Voer de opdracht uit om de hasher uit te voeren:

```
Hasher.bat filename.swf
```

of de opdracht:

```
java -jar libs/flashaccess-hasher.jar filename.swf
```

Het nut output het volgende bericht:

```
SWF Hash: hash-of-swf
```

Deze waarde kan worden gebruikt om de SWF-samenvatting op te geven in [!DNL flashaccess-tenant.xml].
