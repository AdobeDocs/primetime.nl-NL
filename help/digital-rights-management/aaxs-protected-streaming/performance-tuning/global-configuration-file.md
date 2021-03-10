---
title: Globaal configuratiebestand
description: Globaal configuratiebestand
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---


# Globaal configuratiebestand{#global-configuration-file}

De grootste invloed op de prestaties die u kunt maken, is door instellingen te gebruiken in het algemene configuratiebestand, flashaccess-global.xml. Deze instellingen omvatten de elementen `<Caching>` en `<Logging>`.

* `<Caching>` Het  `<Caching>` element controleert caching van configuratiedossiers in geheugen. Het element `<Caching>` heeft de volgende syntaxis:

   ```
   <Caching refreshDelaySeconds="..." numTenants="..."/>
   ```

   * `refreshDelaySeconds` controleert hoe vaak de server updates aan de configuratiedossiers controleert. Een lage waarde voor `refreshDelaySeconds` heeft een negatief effect op de prestaties, terwijl een hogere waarde de prestaties kan verbeteren. Voor meer informatie over `refreshDelaySeconds`, zie &quot;[Het bijwerken van configuratiedossiers](../../aaxs-protected-streaming/updating-configuration-files/updating-configuration-files-overview.md)&quot;.

   * `numTenants` geeft het aantal huurders aan. Een waarde die lager is dan het aantal huurders heeft waarschijnlijk invloed op de prestaties omdat aanvragen bij de resterende huurders resulteren in een fout in het cachegeheugen. Een cache-fout voor configuratiegegevens heeft een negatief effect op de prestaties. Daarom adviseert Adobe dat u deze waarde hoger dan het aantal huurders plaatst die voor de server worden gevormd, tenzij er geheugenbeperkingen zijn om te overwegen.

* `<Logging>` Het  `<Logging>` element specificeert het registrerenniveau en hoe vaak de logboekdossiers worden gewist. Het element `<Logging>` heeft de volgende syntaxis:

   ```
   <Logging level="..." rollingFrequency=""/>
   ```

   * `level` geeft de berichten aan die moeten worden geregistreerd. Een waarde van &quot;DEBUG&quot;produceert veel logboekberichten, en kan prestaties negatief beïnvloeden. Adobe beveelt een instelling van &quot;WARN&quot; aan voor optimale prestaties. Deze waarde loopt echter wel het risico dat essentiële runtime-informatie verloren gaat, zoals licentiecontroles. Als u waardevolle logboekgegevens wilt behouden met minimale gevolgen voor de prestaties, gebruikt u de waarde &quot;INFO&quot;.
   * `rollingFrequency` Hiermee geeft u aan hoe vaak logbestanden worden  *gewist*. Rollen is het proces waar een nieuw logboekdossier het actieve logboek wordt, terwijl het eerder actieve logboekdossier niet meer wordt geschreven aan en beschouwd als gewalst. Het rolinterval kan worden ingesteld op &quot;MINUTELY&quot;, &quot;HOURLY&quot;, &quot;TWICE-DAILY&quot;, &quot;DAILY&quot;, &quot;WEEKLY&quot;, &quot;MONTHLY&quot; of &quot;NEVER&quot;.

Zie *De SDK van de Toegang van de Adobe gebruiken voor het Beschermen van Inhoud* voor extra uiteinden op het optimaliseren van prestaties.
