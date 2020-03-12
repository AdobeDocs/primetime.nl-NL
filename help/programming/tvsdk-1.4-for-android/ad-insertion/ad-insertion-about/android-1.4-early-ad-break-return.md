---
description: Voor live streaming en invoegen moet u mogelijk een ad-einde verlaten voordat alle advertenties in het einde worden afgespeeld.
seo-description: Voor live streaming en invoegen moet u mogelijk een ad-einde verlaten voordat alle advertenties in het einde worden afgespeeld.
seo-title: Een vroege terugkeer voor een onderbreking implementeren
title: Een vroege terugkeer voor een onderbreking implementeren
uuid: 41b70ee1-290b-4732-899e-32b234ec1d9a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Een vroege terugkeer voor een onderbreking implementeren {#implement-an-early-ad-break-return}

Voor live streaming en invoegen moet u mogelijk een ad-einde verlaten voordat alle advertenties in het einde worden afgespeeld.

De duur van de advertentiepauze bij bepaalde sportevenementen is bijvoorbeeld mogelijk niet bekend voordat de pauze begint. TVSDK biedt een standaardduur, maar als de game wordt hervat voordat het einde van het einde van het einde is bereikt, moet het ad-einde worden verlaten. Een ander voorbeeld is een noodsignaal tijdens een pauze in een live stream.

1. Abonneren op de splice out/in-advertentiemarkeringen ( `#EXT-X-CUE-OUT`, `#EXT-X-CUE-IN`, en `#EXT-X-CUE`).

   Voor meer informatie over hoe te om uit/in te spuiten en tellers, zie de generators van de [Kans en inhoudsoplossers](../../../tvsdk-1.4-for-android/content-resolver/android-1.4-content-resolver-about.md).
1. Gebruik een aangepaste instelling `ContentFactory`.
1. In `retrieveGenerators()`, gebruik `SpliceInPlacementOpportunityGenerator`.

   Bijvoorbeeld:

   ```java
   public List<OpportunityGenerator> retrieveGenerators(MediaPlayerItem item) { 
       List<OpportunityGenerator> generators = new ArrayList<OpportunityGenerator>(); 
       generators.add(SpliceInPlacementOpportunityDetector(item)); 
       return generators; 
   }
   ```

   Voor meer informatie over het gebruiken van een douane `ContentFactory`, zie stap 1 in [Voer een ontdekkingsreiziger](../../../tvsdk-1.4-for-android/content-resolver/android-1.4-opp-detector-impl.md) van de douanekans uit.

1. Implementeer en neem een include-bestand op `ContentFactory`en `retrieveResolvers` `AuditudeResolver` `SpliceInCustomResolver`gebruik deze code op dezelfde manier.

   Bijvoorbeeld:

   ```java
   List<ContentResolver> contentResolvers = new ArrayList<ContentResolver>(); 
   contentResolvers.add(new AuditudeResolver(getActivity().getApplicationContext())); 
   contentResolvers.add(new SpliceInCustomResolver()); 
   return contentResolvers;
   ```

