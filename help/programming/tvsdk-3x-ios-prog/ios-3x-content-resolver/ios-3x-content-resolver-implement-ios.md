---
description: U kunt uw oplosmiddelen uitvoeren die op de standaardoplossers worden gebaseerd.
seo-description: U kunt uw oplosmiddelen uitvoeren die op de standaardoplossers worden gebaseerd.
seo-title: Een aangepaste opportuniteit/contentoplosser implementeren
title: Een aangepaste opportuniteit/contentoplosser implementeren
uuid: 0023f516-12f3-4548-93de-b0934789053b
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Een aangepaste opportuniteit/contentoplosser implementeren {#implement-a-custom-opportunity-content-resolver}

U kunt uw oplosmiddelen uitvoeren die op de standaardoplossers worden gebaseerd.

<!--<a id="fig_CC41E2A66BDB4115821F33737B46A09B"></a>-->

![](assets/ios_psdk_content_resolver.png)

1. Ontwikkel een douane en oplosser door de `PTContentResolver` abstracte klasse uit te breiden.

   `PTContentResolver` is een interface die door een content resolver-klasse moet worden geïmplementeerd. Een abstracte klasse met de zelfde naam is ook beschikbaar en behandelt automatisch de configuratie (die de afgevaardigde krijgt).

   >[!TIP]
   >
   >`PTContentResolver` wordt via de `PTDefaultMediaPlayerClientFactory` klasse weergegeven. Clients kunnen een nieuwe contentoplosser registreren door de `PTContentResolver` abstracte klasse uit te breiden. Door gebrek, en tenzij specifiek verwijderd, `PTDefaultAdContentResolver` wordt een geregistreerd in `PTDefaultMediaPlayerClientFactory`.

   ```
   @protocol PTContentResolver <NSObject> 
   @required 
   + (BOOL)shouldHandleOpportunity:(PTPlacementOpportunity *)opportunity;  
   //Detector returns YES/NO if it should handle the following placement opportunity 
   - (void)configWithPlayerItem:(PTMediaPlayerItem *)item  
                 delegate:(id<PTContentResolverDelegate> delegate); 
   - (void)process:(PTPlacementOpportunity *)opportunity; 
   - (void)timeout:(PTPlacementOpportunity *)opportunity;  
   //The timeout method gets invoked if the TVSDK decides that the  
   //PTContentResolver is taking too much time to respond. 
   @end 
   
   @interface PTContentResolver : NSObject <PTContentResolver> 
   
   @property (readonly) id<PTContentResolverDelegate> delegate; 
   @property (readonly) PTMediaPlayerItem *playerItem; 
   
   - (BOOL)shouldHandleOpportunity:(PTPlacementOpportunity *)opportunity; 
   - (void)configWithPlayerItem:(PTMediaPlayerItem *)item  
                  delegate:(id<PTContentResolverDelegate>) delegate; 
   - (void)process:(NSArray *)opportunities; 
   - (void)cancel:(NSArray *)opportunities; 
   @end
   ```

1. Voer uit `shouldResolveOpportunity` en terugkeer `YES` als het ontvangen zou moeten behandelen `PTPlacementOpportunity`.
1. Implementeren `resolvePlacementOpportunity`, waarmee de alternatieve inhoud of advertenties wordt geladen.
1. Nadat de advertenties zijn geladen, bereidt u een document voor `PTTimeline` met de informatie over de inhoud die u wilt invoegen.

       Hier volgt nuttige informatie over tijdlijnen:
   
   * Er kunnen meerdere typen `PTAdBreak`vóór, halverwege en na het rollen zijn.

      * A `PTAdBreak` heeft het volgende:

         * Een `CMTimeRange` met de begintijd en de duur van het einde.

            Deze wordt ingesteld als de eigenschap range van `PTAdBreak`.

         * `NSArray` van `PTAd`s.

            Deze wordt ingesteld als de eigenschap ads van `PTAdBreak`.
   * A `PTAd` vertegenwoordigt de advertentie en elk `PTAd` heeft het volgende:

      * Een `PTAdHLSAsset` set als de primaire eigenschap van het element van de advertentie.
      * Meerdere `PTAdAsset` varianten mogelijk als klikbare advertenties of banneradvertenties.
   Bijvoorbeeld:

   ```
   NSMutableArray *ptBreaks = [[[NSMutableArray alloc] init] autorelease]; 
   
   // Prepare the primary asset of the ad - links to ad m3u8 
   PTAdHLSAsset *ptAdAsset = [[[PTAdHLSAsset alloc] init] autorelease]; 
   ptAdAsset.source = AD_SOURCE_M3U8; 
   ptAdAsset.id = FAKE_NUMBER_ID; 
   ptAdAsset.format = @"video"; 
   
   // Prepare the ad itself. 
   PTAd *ptAd = [[[PTAd alloc] init] autorelease]; 
   ptAd.primaryAsset = ptAdAsset; 
   ptAd.primaryAsset.ad = ptAd; 
   
   // Prepare the break and add the ad created above. 
   PTAdBreak *ptBreak = [[[PTAdBreak alloc] init] autorelease]; 
   ptBreak.relativeRange = CMTimeRangeMake(BREAK_START_TIME, BREAK_DURATION_VALUE); 
   [ptBreak addAd:ptAd]; 
   
   // Add the break to array of breaks. 
   [ptBreaks addObject:adBreak]; 
   
   // Once all breaks have been prepared, they can be set on timeline 
   PTTimeline *_timeline = [[PTTimeline alloc] init]; 
   _timeline.adBreaks = ptBreaks;
   ```

1. Vraag `didFinishResolvingPlacementOpportunity`, die `PTTimeline`verstrekt.
1. Registreer uw aangepaste inhoud/advertentieoplosser aan de standaardfabriek van de mediaspeler door aan te roepen `registerContentResolver`.

   ```
   //Remove default content/ad resolver 
   [[PTDefaultMediaPlayerFactory defaultFactory] clearContentResolvers]; 
   
   //Create an instance of your content/ad resolver (id <PTContentResolver>) 
   CustomContentResolver *contentResolver = [[CustomContentResolver alloc] init]; 
   
   //Set custom content/ad resolver 
   [[PTDefaultMediaPlayerFactory defaultFactory] registerContentResolver:[contentResolver autorelease]];
   ```

1. Als u een aangepaste opportuniteitsoplosser hebt geïmplementeerd, registreert u deze in de standaardfabriek voor de mediaspeler.

   >[!TIP]
   >
   >U hoeft geen aangepaste opportuniteitsoplosser te registreren om een aangepaste inhoud/ad-oplosser te registreren.

   ```
   //Remove default opportunity resolver 
   [[PTDefaultMediaPlayerFactory defaultFactory] clearOpportunityResolvers]; 
   
   //Create an instance of your opportunity resolver (id <PTOpportunityResolver>) 
   CustomOpportunityResolver *opportunityResolver = [[CustomOpportunityResolver alloc] init]; 
   
   //Set custom opportunity resolver 
   [[PTDefaultMediaPlayerFactory defaultFactory]  
              registerOpportunityResolver:[opportunityResolver autorelease]];
   ```

Wanneer de speler de inhoud laadt en wordt bepaald dat deze van het type VOD of LIVE is, vindt een van de volgende situaties plaats:

* Als de inhoud VOD is, wordt de aangepaste inhoudoplosser gebruikt om de tijdlijn van de advertentie van de volledige video te krijgen.
* Als de inhoud LIVE is, wordt de oplosser van de douaneinhoud geroepen telkens als een plaatsingskans (richtsnoerpunt) in de inhoud wordt ontdekt.