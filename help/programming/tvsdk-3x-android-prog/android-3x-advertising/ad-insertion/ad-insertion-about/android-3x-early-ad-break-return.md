---
description: Voor live streaming en invoegen moet u mogelijk een ad-einde verlaten voordat alle advertenties in het einde worden afgespeeld.
seo-description: Voor live streaming en invoegen moet u mogelijk een ad-einde verlaten voordat alle advertenties in het einde worden afgespeeld.
seo-title: Een vroege terugkeer voor een onderbreking implementeren
title: Een vroege terugkeer voor een onderbreking implementeren
uuid: 0e77414e-86f5-4979-9caa-eaf2f39144a2
translation-type: tm+mt
source-git-commit: 3fdae2b6babb578d2cacff970fd9c7b53ad2c5dc

---


# Een vroege terugkeer voor een onderbreking implementeren {#implement-an-early-ad-break-return}

Voor live streaming en invoegen moet u mogelijk een ad-einde verlaten voordat alle advertenties in het einde worden afgespeeld.

De duur van de advertentiepauze bij bepaalde sportevenementen is bijvoorbeeld mogelijk niet bekend voordat de pauze begint. TVSDK biedt een standaardduur, maar als de game wordt hervat voordat het einde van het einde van het einde is bereikt, moet het ad-einde worden verlaten. Een ander voorbeeld is een noodsignaal tijdens een pauze in een live stream.

1. Abonneren op `#EXT-X-CUE-OUT`, `#EXT-X-CUE-IN`en `#EXT-X-CUE`, die de splice out/splice in tellers zijn.
Voor meer informatie over hoe te om uit/in te spuiten en tellers, zie de generators van de [Kans en inhoudsoplossers](../../ad-insertion/content-resolver/android-3x-content-resolver.md).
1. Gebruik een aangepaste instelling `ContentFactory`.
1. In `retrieveGenerators`, gebruik `SpliceInPlacementOpportunityGenerator`.

   Bijvoorbeeld:

   ```java
   public List<OpportunityGenerator> retrieveGenerators(MediaPlayerItem item) { 
       List<OpportunityGenerator> generators = new ArrayList<OpportunityGenerator>(); 
       generators.add(SpliceInPlacementOpportunityDetector(item)); 
       return generators; 
   }
   ```

   Voor meer informatie over het gebruiken van een douane `ContentFactory`, zie stap 1 in [Voer een aanpasbare teller](../../ad-insertion/content-resolver/android-3x-opp-detector-impl-android.md)uit.

1. Implementeer en neem een include-bestand op `ContentFactory`en `retrieveResolvers` `AuditudeResolver` `SpliceInCustomResolver`gebruik deze code op dezelfde manier.

   Bijvoorbeeld:

   ```java
   List<ContentResolver> contentResolvers = new ArrayList<ContentResolver>(); 
   contentResolvers.add(new AuditudeResolver(getActivity().getApplicationContext())); 
   contentResolvers.add(new SpliceInCustomResolver()); 
   return contentResolvers;
   ```
