---
description: TVSDK reageert op onjuiste tijdbereikspecificaties door de tijdbereiken waar nodig samen te voegen of te vervangen.
title: Voorbeelden van tijdbereikfouten
exl-id: 70bbd98b-4084-4a26-8420-fdbe9029194d
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---

# Voorbeelden van tijdbereikfouten{#time-range-error-examples}

TVSDK reageert op onjuiste tijdbereikspecificaties door de tijdbereiken waar nodig samen te voegen of te vervangen.

**DELETE-tijdbereik**

In het volgende voorbeeld worden vier elkaar kruisende DELETE-tijdbereiken gedefinieerd. TVSDK voegt de vier tijdbereiken samen in één, zodat de daadwerkelijke schrappingswaaier van 0 tot 50 s is.

```
"time-ranges": {
    "type": "delete",
    "time-range-list": [
        {
            "begin": 10000,
            "end": 35000
        },
        {
            "begin": 20000,
            "end": 50000
        },
        {
            "begin": 0,
            "end": 30000
        },
        {
            "begin": 30000,
            "end": 40000
        }
    ]
}
```

**Tijdbereik VERVANGEN**

In het volgende voorbeeld worden vier REPLACE-tijdbereiken gedefinieerd met conflicterende tijdbereiken. In dit geval vervangt TVSDK 0-50 seconden door 25 seconden aan advertenties. De waarde gaat in de sorteervolgorde naar de eerste vervangende duur, omdat er conflicten optreden in volgende bereiken.

```
"time-ranges": {
    "type": "replace",
    "time-range-list": [
        {
            "begin": 10000,
            "end": 35000,
            "replace-duration": 15000
        },
        {
            "begin": 20000,
            "end": 50000,
            "replace-duration": 20000
        },
        {
            "begin": 0,
            "end": 30000,
            "replace-duration": 25000
        },
        {
            "begin": 30000,
            "end": 40000,
            "replace-duration": 30000
        }
    ]
}
```
