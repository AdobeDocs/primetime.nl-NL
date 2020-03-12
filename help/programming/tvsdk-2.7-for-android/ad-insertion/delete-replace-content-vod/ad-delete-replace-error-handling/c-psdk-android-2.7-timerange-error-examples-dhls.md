---
description: TVSDK reageert op onjuiste tijdbereikspecificaties door de tijdbereiken waar nodig samen te voegen of te vervangen.
seo-description: TVSDK reageert op onjuiste tijdbereikspecificaties door de tijdbereiken waar nodig samen te voegen of te vervangen.
seo-title: Voorbeelden van tijdbereikfouten
title: Voorbeelden van tijdbereikfouten
uuid: f6cc1e61-8f42-4559-b643-2134180a8c5e
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Voorbeelden van tijdbereikfouten{#time-range-error-examples}

TVSDK reageert op onjuiste tijdbereikspecificaties door de tijdbereiken waar nodig samen te voegen of te vervangen.

**Tijdbereik VERWIJDEREN**

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

