---
description: Dit onderwerp beschrijft prestaties-verwante overwegingen. Om het even welke montages in het globale configuratiedossier genoemd flashaccess-global.xml beïnvloeden prestaties.
title: Globaal configuratiebestand
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---


# Afstelling van prestaties {#performance-tuning}

Dit onderwerp beschrijft prestaties-verwante overwegingen. Om het even welke montages in het globale configuratiedossier genoemd flashaccess-global.xml beïnvloeden prestaties.

## Globaal configuratiebestand {#global-configuration-file}

Het configuratiebestand bevat de volgende instellingselementen:

* `<Caching>` Het  `<Caching>` element controleert caching van configuratiedossiers in geheugen. Het element `<Caching>` ondersteunt de volgende syntaxis:

```
  <Caching refreshDelaySeconds="..." numTenants="..."/>
```

* `refreshDelaySeconds` Bepaalt hoe vaak de server controleert op updates van de configuratiebestanden. Een lage waarde voor `refreshDelaySeconds` heeft een negatieve invloed op de prestaties terwijl een hogere waarde de prestaties kan verbeteren.

   Zie *Configuratiebestanden bijwerken* voor meer informatie over `refreshDelaySeconds`.

* `numTenants` geeft het aantal huurders aan. Een waarde die lager is dan het aantal huurders heeft invloed op de prestaties omdat aanvragen bij de resterende huurders resulteren in cacheproblemen. Een geheim voorgeheugen mist voor om het even welke configuratiegegevens negatief beïnvloedt prestaties. Daarom wordt geadviseerd dat u deze waarde hoger dan het aantal huurders plaatst die voor de server worden gevormd tenzij er geheugenbeperkingen zijn die u moet overwegen.

* `<Logging>` Het  `<Logging>` element specificeert het registrerenniveau en de frequentie waarmee de logboekdossiers worden gerold. Het element `<Logging>` ondersteunt de volgende syntaxis:

   ```
   <Logging level="..." rollingFrequency="..."/>
   ```

* `<level>`  `level` geeft berichten aan voor een logboek. De waarde `DEBUG` levert veel logberichten op, wat de prestaties negatief kan beïnvloeden. Voor optimale prestaties is het raadzaam een instelling van `WARN` toe te passen. Deze waarde kan echter resulteren in het verliezen van essentiële runtime-informatie, zoals licentiecontroles. Als u loggegevens wilt opslaan met minimale gevolgen voor de prestaties, moet u de waarde `INFO` toepassen.

* `<rollingFrequency>`  `rollingFrequency` Hiermee geeft u aan hoe vaak logbestanden worden  *gewist*. *`Rolling`* is een proces dat om het even welk nieuw logboekdossier als actief logboek aanwijst. Het eerder actieve logbestand kan daarom niet meer worden gewijzigd en wordt beschouwd als *`rolled`*. U kunt het rolinterval instellen op `MINUTELY`, `HOURLY`, `TWICE-DAILY`, `DAILY`, `WEEKLY`, `MONTHLY` of `NEVER`.

Zie *De Adobe Primetime DRM SDK gebruiken voor het beveiligen van inhoud* voor tips over het optimaliseren van prestaties.