---
seo-title: Globaal configuratiebestand
title: Globaal configuratiebestand
uuid: 48c45f56-55c2-4526-b854-5552caf21541
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Globaal configuratiebestand{#global-configuration-file}

De grootste invloed op de prestaties die u kunt maken, is door instellingen te gebruiken in het algemene configuratiebestand, flashaccess-global.xml. Deze instellingen omvatten de `<Caching>` elementen en `<Logging>` elementen.

* `<Caching>` Het `<Caching>` element controleert caching van configuratiedossiers in geheugen. Het `<Caching>` element heeft de volgende syntaxis:

   ```
   <Caching refreshDelaySeconds="..." numTenants="..."/>
   ```

   * `refreshDelaySeconds` controleert hoe vaak de server updates aan de configuratiedossiers controleert. Een lage waarde voor `refreshDelaySeconds` negatieve gevolgen voor de prestaties, terwijl een hogere waarde de prestaties kan verbeteren. Voor meer informatie over `refreshDelaySeconds`, zie &quot;het[Bijwerken van configuratiedossiers](../../aaxs-protected-streaming/updating-configuration-files/updating-configuration-files-overview.md)&quot;.

   * `numTenants` geeft het aantal huurders aan. Een waarde die lager is dan het aantal huurders heeft waarschijnlijk invloed op de prestaties omdat aanvragen bij de resterende huurders resulteren in een fout in het cachegeheugen. Een cache-fout voor configuratiegegevens heeft een negatief effect op de prestaties. Daarom raadt Adobe u aan om deze waarde hoger in te stellen dan het aantal huurders dat voor de server is geconfigureerd, tenzij er geheugenbeperkingen in acht moeten worden genomen.

* `<Logging>` Het `<Logging>` element specificeert het registrerenniveau en hoe vaak de logboekdossiers worden gewist. Het `<Logging>` element heeft de volgende syntaxis:

   ```
   <Logging level="..." rollingFrequency=""/>
   ```

   * `level` geeft de berichten aan die moeten worden geregistreerd. Een waarde van &quot;DEBUG&quot;produceert veel logboekberichten, en kan prestaties negatief beïnvloeden. Adobe raadt een instelling van &quot;WARN&quot; aan voor optimale prestaties. Deze waarde loopt echter wel het risico dat essentiële runtime-informatie verloren gaat, zoals licentiecontroles. Als u waardevolle logboekgegevens wilt behouden met minimale gevolgen voor de prestaties, gebruikt u de waarde &quot;INFO&quot;.
   * `rollingFrequency` Hiermee geeft u aan hoe vaak logbestanden worden *gewist*. Rollen is het proces waar een nieuw logboekdossier het actieve logboek wordt, terwijl het eerder actieve logboekdossier niet meer wordt geschreven aan en beschouwd als gewalst. Het rolinterval kan worden ingesteld op &quot;MINUTELY&quot;, &quot;HOURLY&quot;, &quot;TWICE-DAILY&quot;, &quot;DAILY&quot;, &quot;WEEKLY&quot;, &quot;MONTHLY&quot; of &quot;NEVER&quot;.

Zie De SDK van Adobe Access *gebruiken voor het beveiligen van inhoud* voor meer tips over het optimaliseren van prestaties.
