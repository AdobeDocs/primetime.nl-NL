---
description: Voor live streaming en invoegen moet u mogelijk een ad-einde verlaten voordat alle advertenties in het einde worden afgespeeld.
seo-description: Voor live streaming en invoegen moet u mogelijk een ad-einde verlaten voordat alle advertenties in het einde worden afgespeeld.
seo-title: Een vroege terugkeer voor een onderbreking implementeren
title: Een vroege terugkeer voor een onderbreking implementeren
uuid: c67f2158-5df4-458c-a27a-6329c5d26638
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Een vroege terugkeer voor een onderbreking implementeren {#implement-an-early-ad-break-return}

Voor live streaming en invoegen moet u mogelijk een ad-einde verlaten voordat alle advertenties in het einde worden afgespeeld.

De duur van de advertentiepauze bij bepaalde sportevenementen is bijvoorbeeld mogelijk niet bekend voordat de pauze begint. TVSDK biedt een standaardduur, maar als de game wordt hervat voordat het einde van het einde van het einde is bereikt, moet het ad-einde worden verlaten. Een ander voorbeeld is een noodsignaal tijdens een pauze in een live stream.

1. Abonneren op `#EXT-X-CUE-OUT`, `#EXT-X-CUE-IN`en `#EXT-X-CUE`, die de splice out/splice in tellers zijn.

   Voor meer informatie over hoe te om uit/in te spuiten en tellers, zie de generators van de [Kans en inhoudsoplossers](../../ad-insertion/content-resolver/c-psdk-android-2.7-content-resolver-about.md).

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

   Voor meer informatie over het gebruiken van een douane `ContentFactory`, zie stap 1 in [Voer een aanpasbare teller](../../ad-insertion/content-resolver/t-psdk-android-2.7-opp-detector-impl-android.md)uit.

1. Implementeer en neem een include-bestand op `ContentFactory`en `retrieveResolvers` `AuditudeResolver` `SpliceInCustomResolver`gebruik deze code op dezelfde manier.

   Bijvoorbeeld:

   ```java
   List<ContentResolver> contentResolvers = new ArrayList<ContentResolver>(); 
   contentResolvers.add(new AuditudeResolver(getActivity().getApplicationContext())); 
   contentResolvers.add(new SpliceInCustomResolver()); 
   return contentResolvers;
   ```

