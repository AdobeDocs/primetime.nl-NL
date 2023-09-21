---
description: Voor live streaming en invoegen moet u mogelijk een ad-einde verlaten voordat alle advertenties in het einde worden afgespeeld.
title: Een vroege terugkeer voor een onderbreking implementeren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# Een vroege terugkeer voor een onderbreking implementeren {#implement-an-early-ad-break-return}

Voor live streaming en invoegen moet u mogelijk een ad-einde verlaten voordat alle advertenties in het einde worden afgespeeld.

De duur van de advertentiepauze bij bepaalde sportevenementen is bijvoorbeeld mogelijk niet bekend voordat de pauze begint. TVSDK biedt een standaardduur, maar als de game wordt hervat voordat het einde van het einde van het einde is bereikt, moet het ad-einde worden verlaten. Een ander voorbeeld is een noodsignaal tijdens een pauze in een live stream.

1. Abonneer u op de splice out/in-advertentiemarkeringen ( `#EXT-X-CUE-OUT`, `#EXT-X-CUE-IN`, en `#EXT-X-CUE`).

   Zie voor meer informatie over het uitsplitsen/insplitsen van advertentiemarkeringen [Opportuniteitsgeneratoren en contentoplosers](../../../tvsdk-1.4-for-android/content-resolver/android-1.4-content-resolver-about.md).
1. Een aangepaste `ContentFactory`.
1. In `retrieveGenerators()`, gebruikt u de `SpliceInPlacementOpportunityGenerator`.

   Bijvoorbeeld:

   ```java
   public List<OpportunityGenerator> retrieveGenerators(MediaPlayerItem item) { 
       List<OpportunityGenerator> generators = new ArrayList<OpportunityGenerator>(); 
       generators.add(SpliceInPlacementOpportunityDetector(item)); 
       return generators; 
   }
   ```

   Voor meer informatie over het gebruik van een aangepaste `ContentFactory`, zie stap 1 in [Een aangepaste opportuniteitsdetector implementeren](../../../tvsdk-1.4-for-android/content-resolver/android-1.4-opp-detector-impl.md) .

1. Op dezelfde aangepaste `ContentFactory`uitvoeren `retrieveResolvers` en omvatten `AuditudeResolver` en `SpliceInCustomResolver`.

   Bijvoorbeeld:

   ```java
   List<ContentResolver> contentResolvers = new ArrayList<ContentResolver>(); 
   contentResolvers.add(new AuditudeResolver(getActivity().getApplicationContext())); 
   contentResolvers.add(new SpliceInCustomResolver()); 
   return contentResolvers;
   ```
