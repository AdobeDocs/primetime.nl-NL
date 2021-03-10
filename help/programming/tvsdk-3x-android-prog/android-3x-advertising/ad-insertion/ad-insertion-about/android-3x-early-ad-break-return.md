---
description: Voor live streaming en invoegen moet u mogelijk een ad-einde verlaten voordat alle advertenties in het einde worden afgespeeld.
title: Een vroege terugkeer voor een onderbreking implementeren
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 2%

---


# Een vroege return ad break {#implement-an-early-ad-break-return} implementeren

Voor live streaming en invoegen moet u mogelijk een ad-einde verlaten voordat alle advertenties in het einde worden afgespeeld.

De duur van de advertentiepauze bij bepaalde sportevenementen is bijvoorbeeld mogelijk niet bekend voordat de pauze begint. TVSDK biedt een standaardduur, maar als de game wordt hervat voordat het einde van het einde van het einde is bereikt, moet het ad-einde worden verlaten. Een ander voorbeeld is een noodsignaal tijdens een pauze in een live stream.

1. Abonneren op `#EXT-X-CUE-OUT`, `#EXT-X-CUE-IN` en `#EXT-X-CUE`, die de splice out/splice in tellers zijn.
Zie [Opportunity generators and content resolvers](../../ad-insertion/content-resolver/android-3x-content-resolver.md) voor meer informatie over het uitsplitsen/insplitsen van advertentiemarkeringen.
1. Gebruik een aangepaste `ContentFactory`.
1. In `retrieveGenerators`, gebruik `SpliceInPlacementOpportunityGenerator`.

   Bijvoorbeeld:

   ```java
   public List<OpportunityGenerator> retrieveGenerators(MediaPlayerItem item) { 
       List<OpportunityGenerator> generators = new ArrayList<OpportunityGenerator>(); 
       generators.add(SpliceInPlacementOpportunityDetector(item)); 
       return generators; 
   }
   ```

   Voor meer informatie over het gebruiken van een douane `ContentFactory`, zie stap 1 in [Voer een douanemogelijkheid teller](../../ad-insertion/content-resolver/android-3x-opp-detector-impl-android.md) uit.

1. Implementeer `retrieveResolvers` op dezelfde aangepaste `ContentFactory` en neem `AuditudeResolver` en `SpliceInCustomResolver` op.

   Bijvoorbeeld:

   ```java
   List<ContentResolver> contentResolvers = new ArrayList<ContentResolver>(); 
   contentResolvers.add(new AuditudeResolver(getActivity().getApplicationContext())); 
   contentResolvers.add(new SpliceInCustomResolver()); 
   return contentResolvers;
   ```
