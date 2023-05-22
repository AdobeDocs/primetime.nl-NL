---
title: SWF Hash-calculator
description: SWF Hash-calculator
copied-description: true
exl-id: 651b31bc-47b5-4388-aa00-27d3bd59da30
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
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
