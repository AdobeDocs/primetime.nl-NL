---
description: Dit onderwerp beschrijft prestaties-verwante overwegingen. Om het even welke montages in het globale configuratiedossier genoemd flashaccess-global.xml beïnvloeden prestaties.
title: Globaal configuratiebestand
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# Prestaties afstemmen {#performance-tuning}

Dit onderwerp beschrijft prestaties-verwante overwegingen. Om het even welke montages in het globale configuratiedossier genoemd flashaccess-global.xml beïnvloeden prestaties.

## Globaal configuratiebestand {#global-configuration-file}

Het configuratiebestand bevat de volgende instellingselementen:

* `<Caching>` De `<Caching>` element bestuurt caching van configuratiedossiers in geheugen. De `<Caching>` element ondersteunt de volgende syntaxis:

```
  <Caching refreshDelaySeconds="..." numTenants="..."/>
```

* `refreshDelaySeconds` Bepaalt hoe vaak de server controleert op updates van de configuratiebestanden. Een lage waarde voor `refreshDelaySeconds` de prestaties negatief beïnvloeden terwijl een hogere waarde de prestaties kan verbeteren.

  Zie *Configuratiebestanden bijwerken* voor meer informatie over `refreshDelaySeconds`.

* `numTenants` geeft het aantal huurders aan. Een waarde die lager is dan het aantal huurders heeft invloed op de prestaties omdat aanvragen bij de resterende huurders resulteren in cacheproblemen. Een geheim voorgeheugen mist voor om het even welke configuratiegegevens negatief beïnvloedt prestaties. Daarom wordt geadviseerd dat u deze waarde hoger dan het aantal huurders plaatst die voor de server worden gevormd tenzij er geheugenbeperkingen zijn die u moet overwegen.

* `<Logging>` De `<Logging>` het element specificeert het registrerenniveau en de frequentie waarmee de logboekdossiers worden gerold. De `<Logging>` element ondersteunt de volgende syntaxis:

  ```
  <Logging level="..." rollingFrequency="..."/>
  ```

* `<level>`  `level` geeft berichten aan voor een logboek. Een waarde van `DEBUG` Geeft vele logboekberichten op, die prestaties negatief kunnen beïnvloeden. U wordt aangeraden een instelling voor `WARN` voor optimale prestaties. Deze waarde kan echter resulteren in het verliezen van essentiële runtime-informatie, zoals licentiecontroles. Als u logboekinformatie met minimale prestatiesgevolgen wilt bewaren, moet u een waarde van toepassen `INFO`.

* `<rollingFrequency>`  `rollingFrequency` geeft aan hoe vaak logbestanden worden *gewalst*. *`Rolling`* is een proces dat om het even welk nieuw logboekdossier als actief logboek aanwijst. Daarom kan het eerder actieve logbestand niet meer worden gewijzigd en wordt het als *`rolled`*. U kunt het rolinterval instellen op `MINUTELY`, `HOURLY`, `TWICE-DAILY`, `DAILY`, `WEEKLY`, `MONTHLY`, of `NEVER`.

Zie *De Adobe Primetime DRM SDK gebruiken voor het beschermen van inhoud* voor tips over het optimaliseren van prestaties.
