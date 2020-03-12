---
description: TVSDK handelt fouten in het tijdbereik af op basis van het specifieke probleem, door de onjuist gedefinieerde tijdbereiken samen te voegen of opnieuw te ordenen.
seo-description: TVSDK handelt fouten in het tijdbereik af op basis van het specifieke probleem, door de onjuist gedefinieerde tijdbereiken samen te voegen of opnieuw te ordenen.
seo-title: Foutafhandeling voor verwijderen en vervangen van toevoegen
title: Foutafhandeling voor verwijderen en vervangen van toevoegen
uuid: ab153591-0011-44b4-87f9-be0302c2295e
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Foutafhandeling voor verwijderen en vervangen van toevoegen {#ad-deletion-and-replacement-error-handling}

TVSDK handelt fouten in het tijdbereik af op basis van het specifieke probleem, door de onjuist gedefinieerde tijdbereiken samen te voegen of opnieuw te ordenen.

TVSDK behandelt `timeRanges` fouten door standaardsamenvoeging en herschikking uit te voeren. Eerst, sorteert het klant-bepaalde tijdwaaiers door de *begintijd* . Op basis van deze sorteervolgorde worden aangrenzende bereiken samengevoegd en worden deze samengevoegd als er subsets en snijpunten zijn tussen de bereiken.

TVSDK verwerkt fouten in het tijdbereik als volgt:

* Buiten bestelling - TVSDK past de tijdbereiken opnieuw aan.
* Subset - TVSDK voegt de tijdbereiksubsets samen.
* Doorsnede - TVSDK voegt de elkaar kruisende tijdbereiken samen.
* Conflict tussen bereik en bereik vervangen: TVSDK kiest de vervangingsduur vanaf de oudste `timeRange` in de conflicterende groep.

TVSDK handelt de signalerende-wijze conflicten als volgt af:

* Als de waaiers van de VERVANGING worden bepaald, verandert TVSDK automatisch de signalerende wijze in CUSTOM_RANGE.
* Als DELETE waaiers of de waaiers van de MARKERING worden bepaald en de signalerende wijze CUSTOM_RANGE is, schrapt TVSDK of merkt deze waaiers. Er is geen invoeging in dit geval.
* Als een DELETE-bereik of een MARK-bereik een vervangende duur definieert, negeert TVSDK deze duur.

Wanneer de server niet geldig retourneert `AdBreaks`:

* TVSDK genereert en verwerkt een `NOPTimelineOperation` voor het lege veld `AdBreak`. Geen advertentie wordt afgespeeld.

## Voorbeelden van tijdbereikfouten {#time-range-error-examples}

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
