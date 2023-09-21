---
title: Globaal configuratiebestand
description: Globaal configuratiebestand
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Globaal configuratiebestand{#global-configuration-file}

De grootste invloed op de prestaties die u kunt maken, is door instellingen te gebruiken in het algemene configuratiebestand, flashaccess-global.xml. Tot deze instellingen behoren de `<Caching>` en `<Logging>` elementen.

* `<Caching>` De `<Caching>` element bestuurt caching van configuratiedossiers in geheugen. De `<Caching>` element heeft de volgende syntaxis:

  ```
  <Caching refreshDelaySeconds="..." numTenants="..."/>
  ```

   * `refreshDelaySeconds` controleert hoe vaak de server updates aan de configuratiedossiers controleert. Een lage waarde voor `refreshDelaySeconds` een hogere waarde kan de prestaties negatief beïnvloeden. Voor meer informatie over `refreshDelaySeconds`, zie &quot;[Configuratiebestanden bijwerken](../../aaxs-protected-streaming/updating-configuration-files/updating-configuration-files-overview.md)&quot;.

   * `numTenants` geeft het aantal huurders aan. Een waarde die lager is dan het aantal huurders heeft waarschijnlijk invloed op de prestaties omdat aanvragen bij de resterende huurders resulteren in een fout in het cachegeheugen. Een cache-fout voor configuratiegegevens heeft een negatief effect op de prestaties. Daarom adviseert de Adobe dat u deze waarde hoger dan het aantal huurders plaatst die voor de server worden gevormd, tenzij er geheugenbeperkingen zijn om te overwegen.

* `<Logging>` De `<Logging>` het element specificeert het registrerenniveau en hoe vaak de logboekdossiers worden gewist. De `<Logging>` element heeft de volgende syntaxis:

  ```
  <Logging level="..." rollingFrequency=""/>
  ```

   * `level` geeft de berichten aan die moeten worden geregistreerd. Een waarde van &quot;DEBUG&quot;produceert veel logboekberichten, en kan prestaties negatief beïnvloeden. Adobe beveelt een instelling van &quot;WARN&quot; aan voor optimale prestaties. Deze waarde loopt echter wel het risico dat essentiële runtime-informatie verloren gaat, zoals licentiecontroles. Als u waardevolle logboekgegevens wilt behouden met minimale gevolgen voor de prestaties, gebruikt u de waarde &quot;INFO&quot;.
   * `rollingFrequency` geeft aan hoe vaak logbestanden worden *gewalst*. Rollen is het proces waar een nieuw logboekdossier het actieve logboek wordt, terwijl het eerder actieve logboekdossier niet meer wordt geschreven aan en beschouwd als gewalst. Het rolinterval kan worden ingesteld op &quot;MINUTELY&quot;, &quot;HOURLY&quot;, &quot;TWICE-DAILY&quot;, &quot;DAILY&quot;, &quot;WEEKLY&quot;, &quot;MONTHLY&quot; of &quot;NEVER&quot;.

Zie *De Adobe Access SDK gebruiken voor het beveiligen van inhoud* voor meer tips over het optimaliseren van prestaties.
