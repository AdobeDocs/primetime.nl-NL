---
description: Toevoegen lost advertenties voor video-op-verzoek (VOD), voor live streaming en voor lineair streamen met het bijhouden van advertenties en het afspelen van advertenties op. TVSDK doet de vereiste verzoeken aan de advertentieserver, ontvangt informatie over advertenties voor de opgegeven inhoud en plaatst de advertenties in fasen.
seo-description: Toevoegen lost advertenties voor video-op-verzoek (VOD), voor live streaming en voor lineair streamen met het bijhouden van advertenties en het afspelen van advertenties op. TVSDK doet de vereiste verzoeken aan de advertentieserver, ontvangt informatie over advertenties voor de opgegeven inhoud en plaatst de advertenties in fasen.
seo-title: Advertenties invoegen
title: Advertenties invoegen
uuid: 6e31cae5-7363-454f-82dd-e03c1e34cd3f
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Advertenties invoegen {#insert-ads}

Toevoegen lost advertenties voor video-op-verzoek (VOD), voor live streaming en voor lineair streamen met het bijhouden van advertenties en het afspelen van advertenties op. TVSDK doet de vereiste verzoeken aan de advertentieserver, ontvangt informatie over advertenties voor de opgegeven inhoud en plaatst de advertenties in fasen.

Een *`ad break`* bevat een of meer advertenties die achtereenvolgens worden afgespeeld. TVSDK voegt advertenties in de hoofdinhoud in als leden van een of meer advertentieafbrekingen.

>[!TIP]
>
>Als de advertentie fouten bevat, negeert TVSDK de advertentie.

## VOD-advertenties omzetten en invoegen {#section_157344F857C64F36B48AD441F6E7FABA}

TVSDK biedt ondersteuning voor verschillende gebruiksgevallen voor VOD en het oplossen en invoegen van VOD.

* Pre-roll en invoeging, waarbij advertenties aan het begin van de inhoud worden ingevoegd.
* Midden rol en toevoeging, waar minstens één advertentie in het midden van de inhoud wordt opgenomen.
* Na de rol en invoeging, waarbij ten minste één advertentie aan het einde van de inhoud wordt toegevoegd.

TVSDK verhelpt de advertenties, voegt de advertenties in op locaties die door de advertentieserver zijn gedefinieerd en berekent de virtuele tijdlijn voordat het afspelen start. Nadat het afspelen is gestart, kunnen er geen wijzigingen plaatsvinden, zoals advertenties die worden ingevoegd of ingevoegde advertenties die worden verwijderd.

## Actieve en lineaire en {#section_A6A1BB262D084462A1D134083556B7CC}

TVSDK biedt ondersteuning voor verschillende gebruiksgevallen voor live en lineair opheffen en invoegen.

* Pre-roll en invoeging, waarbij ten minste één advertentie aan het begin van de inhoud wordt ingevoegd.
* Midden rol en toevoeging, waar minstens één advertentie in het midden van de inhoud wordt opgenomen.

TVSDK lost de advertenties op en voegt de advertenties in wanneer een richtsnoerpunt in de levende of lineaire stroom wordt ontmoet. Standaard ondersteunt TVSDK de volgende aanwijzingen als geldige advertentiemarkeringen bij het omzetten en plaatsen van advertenties:

* # EXT-X-CUEPOINT
* # EXT-X-AD
* # EXT-X-CUE
* # EXT-X-CUE-OUT

Deze markeringen vereisen het meta-gegevensgebied `DURATION` in seconden en unieke identiteitskaart van de actie. Bijvoorbeeld:

```
#EXT-X-CUE DURATION=27 ID=identiferForThisCue ... 
```

Zie [Abonneren op aangepaste tags](../../tvsdk-3x-ios-prog/ios-3x-advertising/ios-3x-custom-tags-configure/ios-3x-custom-tags-subscribe.md)voor meer informatie over extra aanwijzingen.

## Clientadvertentie bijhouden {#section_12355C7A35F14C15A2A18AAC90FEC2F5}

TVSDK houdt automatisch advertenties bij voor VOD en live/lineair streamen.

Meldingen worden gebruikt om de toepassing te informeren over de voortgang van een advertentie, inclusief informatie over het begin en het einde van een advertentie.

## Een vroege terugkeer voor een onderbreking implementeren {#section_EEB9FE62CA7E4790B58D3CA906F43DCF}

Voor live streaming en invoegen moet u mogelijk een ad-einde verlaten voordat alle advertenties in het einde worden afgespeeld.

Hier volgen enkele voorbeelden van een vroege return ad break:

* De duur van de pauze bij bepaalde sportevenementen.

   Hoewel er een standaardduur is opgegeven, moet het ad-einde worden verlaten als de game wordt hervat voordat het einde van het einde is bereikt.
* Een noodsignaal tijdens een advertentiestop in een live stream.

De mogelijkheid om vroegtijdig een advertentie-einde te verlaten, wordt geïdentificeerd door een aangepaste tag in het manifest die als splice-in of een cue-intag wordt bekend. Met TVSDK kan de toepassing zich abonneren op deze splice-in-tags om een splice-in-mogelijkheid te bieden.

* U kunt als volgt de `#EXT-X-CUE-IN` tag gebruiken als splice-in-mogelijkheid en een vroege en eindemarkering implementeren:

   1. Abonneren op de tag.

      ```
      [PTSDKConfig setSubscribedTags:[NSArray arrayWithObject:@"#EXT-X-CUE-IN"]];
      ```

   1. Voeg de oplosser voor de insteekmogelijkheid toe.

      ```
      // self.player is the PTMediaPlayer instance created for content and ad playback 
      PTDefaultMediaPlayerClientFactory *clientFactory = self.player.mediaPlayerClientFactory; 
      
      // Set cue in opportunity resolver 
      [clientFactory registerOpportunityResolver:[PTDefaultAdSpliceInOpportunityResolver adSpliceInOpportunityResolverWithTag:@"#EXT-X-CUE-IN"]];
      ```

* Dezelfde tag delen voor splice-out en splice-in:

1. Wanneer de toepassing dezelfde actielijn deelt om cue-out/splice-out en cue-in/splice-in aan te geven, breidt u de `PTDefaultAdOpportunityResolver` methode uit `preparePlacementOpportunity` en implementeert u deze.

   [!TIP]

   In de volgende code wordt ervan uitgegaan dat de toepassing een implementatie voor de `isCueInOpportunity` methode heeft.

```
   - (PTPlacementOpportunity *)preparePlacementOpportunity:(PTTimedMetadata *)timedMetadata 
   { 
         if ([self isCueInOpportunity:timedMetadata]) 
         { 
               return [PTPlacementOpportunity advertisementSpliceInOpportunityWithTimedMetadata:timedMetadata]; 
           } 
           else 
           { 
               return [super preparePlacementOpportunity:timedMetadata]; 
         } 
   }
```

1. Registreer de verlengde opportuniteitsoplosser op de `PTDefaultMediaPlayerClientFactory` instantie.

```
   // self.player is the PTMediaPlayer instance created for content and ad playback 
       PTDefaultMediaPlayerClientFactory *clientFactory = self.player.mediaPlayerClientFactory; 
             
   // Clear existing resolver and register the new opportunity resolver 
   [clientFactory clearOpportunityResolvers]; 
   [clientFactory registerOpportunityResolver:[[PTDefaultExtendedAdOpportunityResolver new] autorelease]];
```
