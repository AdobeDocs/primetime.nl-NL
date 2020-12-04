---
description: TVSDK handelt fouten in het tijdbereik af op basis van het specifieke probleem, door de onjuist gedefinieerde tijdbereiken samen te voegen of opnieuw te ordenen.
seo-description: TVSDK handelt fouten in het tijdbereik af op basis van het specifieke probleem, door de onjuist gedefinieerde tijdbereiken samen te voegen of opnieuw te ordenen.
seo-title: Foutafhandeling voor verwijderen en vervangen van toevoegen
title: Foutafhandeling voor verwijderen en vervangen van toevoegen
uuid: e2e06f13-9813-4d86-b6fe-3d09f3bdb100
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---


# Verwijderen en vervangen van foutafhandeling toevoegen{#ad-deletion-and-replacement-error-handling}

TVSDK handelt fouten in het tijdbereik af op basis van het specifieke probleem, door de onjuist gedefinieerde tijdbereiken samen te voegen of opnieuw te ordenen.

TVSDK behandelt `timeRanges` fouten door standaardsamenvoeging en opnieuw rangschikken te doen. Eerst worden door de klant gedefinieerde tijdbereiken gesorteerd op de tijd *begin*. Op basis van deze sorteervolgorde worden aangrenzende bereiken samengevoegd en worden deze samengevoegd als er subsets en snijpunten zijn tussen de bereiken.

TVSDK verwerkt fouten in het tijdbereik als volgt:

* Buiten bestelling - TVSDK past de tijdbereiken opnieuw aan.
* Subset - TVSDK voegt de tijdbereiksubsets samen.
* Doorsnede - TVSDK voegt de elkaar kruisende tijdbereiken samen.
* Conflict tussen bereiken vervangen - TVSDK kiest de vervangingsduur vanaf de vroegste `timeRange` in de conflicterende groep.

TVSDK handelt signaalconflict met metagegevens voor advertenties als volgt af:

* Als de ad signalerende wijze met de tijd-waaier meta-gegevens in conflict brengt, heeft de tijd-waaier meta-gegevens altijd prioriteit. Bijvoorbeeld, als de advertentie signalerende wijze als serverkaart of duidelijke aanwijzingen wordt geplaatst, en er ook de tijdwaaiers van de TUSSENVOEGSEL in de meta-gegevens zijn, is het resulterende gedrag dat de waaiers duidelijk zijn, en geen advertenties worden opgenomen.
* Voor de waaiers van de VERVANGING, als de signalerende wijze als serverkaart of duidelijke aanwijzingen wordt geplaatst, worden de waaiers vervangen zoals die in de waaiers van de VERVANGING worden gespecificeerd, en er is geen invoeging door serverkaart of duidelijke aanwijzingen. Zie [Signaalmodus toevoegen](../../../tvsdk-1.4-for-android/ad-insertion/ad-insertion-metadata/android-1.4-ad-signaling-mode.md).

Wanneer de server geen geldige `AdBreaks` retourneert:

* TVSDK genereert en verwerkt een `NOPTimelineOperation` voor de lege `AdBreak`. Geen advertentie wordt afgespeeld.

Voor tijdbereiken met live streams:

* Hoewel deze C3-functie voor verwijderen/vervangen alleen wordt ondersteund voor VOD, worden tijdbereiken ook verwerkt voor live streams als deze zijn opgegeven in de metagegevens voor advertenties.

## Voorbeelden van fouten in tijdbereik {#time-range-error-examples}

TVSDK reageert op onjuiste tijdbereikspecificaties door de tijdbereiken waar nodig samen te voegen of te vervangen.

In het volgende voorbeeld worden vier elkaar kruisende DELETE-tijdbereiken gedefinieerd. TVSDK voegt de vier tijdbereiken samen in één, zodat de daadwerkelijke schrappingswaaier van 0 tot 50 s is.

```
"time-ranges": {
    "type": "delete",
    "time-range-list": [ {
        "begin": 10000,
        "end": 35000
    }, {
        "begin": 20000,
        "end": 50000
    }, {
        "begin": 0,
        "end": 30000
    }, {
        "begin": 30000,
        "end": 40000
    } ]
}
```

In het volgende voorbeeld worden vier REPLACE-tijdbereiken gedefinieerd met conflicterende tijdbereiken. In dit geval vervangt TVSDK 0-50 seconden door 25 seconden aan advertenties. De waarde gaat in de sorteervolgorde naar de eerste vervangende duur, omdat er conflicten optreden in volgende bereiken.

```
"time-ranges": {
    "type": "replace",
    "time-range-list": [ {
        "begin": 10000,
        "end": 35000,
        "replace-duration": 15000
    }, {
        "begin": 20000,
        "end": 50000,
        "replace-duration": 20000
    }, {
        "begin": 0,
        "end": 30000,
        "replace-duration": 25000
    }, {
        "begin": 30000,
        "end": 40000,
        "replace-duration": 30000
    } ]
}
```
