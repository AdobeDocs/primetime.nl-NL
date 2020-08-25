---
title: TVSDK-conversie - 1.3 naar 2.0 voor JavaScript
seo-title: TVSDK-conversie - 1.3 naar 2.0 voor JavaScript
description: Veel methode-handtekeningen en API-elementnamen zijn gewijzigd voor 2.0. Bekijk deze tabellen om alle details van de API-wijziging te bekijken.
seo-description: Veel methode-handtekeningen en API-elementnamen zijn gewijzigd voor 2.0. Bekijk deze tabellen om alle details van de API-wijziging te bekijken.
uuid: d2d1742d-c90c-43f5-94fc-8c4a57cb8ed4
contentOwner: asgupta
products: SG_PRIMETIME
topic-tags: migration
discoiquuid: c732f54d-116c-43f3-bec4-5e71af208426
translation-type: tm+mt
source-git-commit: cfd6da49e85e13e29e8458ee98231a8b476867db
workflow-type: tm+mt
source-wordcount: '5058'
ht-degree: 0%

---


# TVSDK-conversie - 1.3 naar 2.0 voor JavaScript {#tvsdk-conversion-to-for-javascript}

Veel methode-handtekeningen en API-elementnamen zijn gewijzigd voor 2.0. Bekijk deze tabellen om alle details van de API-wijziging te bekijken.

## Callbackfuncties implementeren in JavaScript {#implement-callback-functions-in-javascript}

De commentaren in methodedocumentatie stellen de handtekening voor callbacks voor die u moet uitvoeren.

Voor JavaScript is de API-syntaxis gebaseerd op de web-id. Voor een TVSDK-interface worden de methodenamen *methodName*() genoemd. Voor methodes die door uw toepassing moeten worden uitgevoerd, wordt een lees-schrijfattribuut genoemd ** methodNameCallbackFunc toegevoegd aan de interface en uw toepassing zou het moeten plaatsen om aan een functie te richten die de methode uitvoert. Bijvoorbeeld:

```shell
// An app implementable interface
interface ContentFactory
{
    /*
     * AdPolicySelector retrieveAdPolicySelector(MediaPlayerItem item);
     */
    attribute Object retrieveAdPolicySelectorCallbackFunc;
 
    /*
     * ContentResolverList retrieveResolvers(MediaPlayerItem item);
     */
    attribute Object retrieveResolversCallbackFunc;
 
    /*
     * OpportunityGeneratorList retrieveGenerators(MediaPlayerItem item);
     */
    attribute Object retrieveGeneratorsCallbackFunc;
};

// this is how to implement it
var factory = new AdobePSDK.ContentFactory();
factory.retrieveAdPolicySelectorCallbackFunc = function(item)
{
    // return your adPolicySelector according to the item
    return adPolicySelector;
}
 
mediaPlayerItemConfig = new AdobePSDK.MediaPlayerItemConfig ();
playerConfig.adFactory = factory;
// Use this config to load new MediaResource
```

## Wijzigingen in API-element voor advertentieworkflow voor 2.0 {#advertising-workflow-api-element-changes-for}

In deze tabellen worden de API-elementen voor de advertentieworkflow voor de JavaScript-TVSDK vergeleken tussen versie 1.3 en 2.0.

Tabellen in dit onderwerp:

* TimedMetadata
* AdSignalingMode
* AdvertisingMetadata
* CustomRangeMetadata
* ReplaceTimeRange
* Plaatsing
* Opportunity
* Voorbehoud
* Tijdlijn / TijdlijnItem / Tijdlijnmarkeerteken
* AdBreak
* Advertentie / AdAsset / AdClick / AdList / AdAssetList / AdBannerAsset
* AdBreakTimelineItem / AdTimelineItem
* AdBreakPolicy / AdBreakWatchedPolicy / AdPolicy / AdPolicyMode / AdPolicyInfo / AdPolicySelector
* TimelineOperation
* AdBreakPlacement
* AuditudeSettings

### TimedMetadata {#timedmetadata}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p> <strong>TimedMetadata</strong>: interface TimedMetadata {<br /> const unsigned short METADATA_TYPE_TAG = 0; <br /> const unsigned short METADATA_TYPE_ID3 = 1; <br /> kenmerk readonly, kenmerk unsigned short type; <br /> kenmerk read-only, lange tijd;<br /> kenmerk readonly, DomString-id;<br /> alleen-lezen kenmerk DomString-naam;<br /> kenmerk readonly, DomString-inhoud; <br /> metagegevens kenmerk kenmerk kenmerk Alleen-lezen;<br /> }; </p> </td> 
   <td><p>interface TimedMetadata {<br /> const unsigned short METADATA_TYPE_TAG = 0;<br /> const unsigned short METADATA_TYPE_ID3 = 1;<br /> kenmerk readonly, kenmerk unsigned short metadataType;<br /> kenmerk read-only, lange tijd;<br /> kenmerk read-only long id;<br /> alleen-lezen kenmerk DomString-naam;<br /> <br /> metagegevens kenmerk kenmerk kenmerk Alleen-lezen;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>TimedMetadataList</strong>: (Geen wijziging voor 2.0)</td> 
   <td><p>interface TimedMetadataList {<br /> readonly attributen unsigned long length;<br /> getter TimedMetadata(unsigned long index);<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### AdSignalingMode {#adsignalingmode}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>Interface AdSignalingMode { <br /> const unsigned short MODE_DEFAULT, <br /> const unsigned short MODE_MANIFEST_CUES , <br /> const unsigned short MODE_SERVER_MAP , <br /> const unsigned short MODE_CUSTOM_RANGES <br /> };</p> </td> 
   <td>Deze vervangt MetadataKeys::MANIFEST_CUES key.</td> 
  </tr> 
 </tbody> 
</table>

### AdvertisingMetadata {#advertisingmetadata}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>Interface AdvertisingMetadata { <br /> -kenmerkmodus AdSignalingMode; <br /> kenmerk AdBreakWatchedPolicy enBreakAsWatched; <br /> attribute boolean livePreroll; <br /> attribute boolean delayAdLoading ; <br /> };</p> </td> 
   <td>Deze functionaliteit is afkomstig van<p>MetadataKeys::ADVERTISING_METADATA</p> key.</td> 
  </tr> 
 </tbody> 
</table>

### CustomRangeMetadata {#customrangemetadata}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>Interface CustomRangeMetadata { <br /> const unsigned short TYPE_MARK_RANGE; <br /> const unsigned short TYPE_DELETE_RANGE; <br /> const unsigned short TYPE_REPLACE_RANGE; <br /> kenmerk zonder teken kort type; <br /> attribuut boolean adjustSeekPosition; <br /> kenmerk TimeRangeList timeRangeList; <br /> };</p> </td> 
   <td>(Nieuw voor 2.0)</td> 
  </tr> 
 </tbody> 
</table>

### ReplaceTimeRange {#replacetimerange}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface ReplaceTimeRange {, <br /> kenmerk unsigned long begin; <br /> kenmerk read-only, kenmerk unsigned long end; <br /> kenmerk unsigned long duration; <br /> kenmerk unsigned long replaceDuration; <br /> };</p> </td> 
   <td>(Nieuw voor 2.0)</td> 
  </tr> 
 </tbody> 
</table>

### Plaatsing {#placement}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>Interface Placement { <br /> const unsigned short TYPE_MID_ROLL; <br /> const unsigned short TYPE_PRE_ROLL; <br /> const unsigned short TYPE_POST_ROLL; <br /> const unsigned short TYPE_SERVER_MAP; <br /> const unsigned short TYPE_CUSTOM_RANGE;<br /> kenmerk readonly, kenmerk unsigned short type; <br /> kenmerk read-only, lange tijd; <br /> kenmerk read-only, lange duur; <br /> const unsigned short MODE_DEFAULT; <br /> const unsigned short MODE_INSERT; <br /> const unsigned short MODE_REPLACE; <br /> const unsigned short MODE_DELETE; <br /> const unsigned short MODE_MARK; <br /> const unsigned short MODE_FREE_REPLACE; <br /> kenmerk readonly, niet-ondertekende korte modus; <br /> alleen-lezen kenmerk TimeRange; <br /> };</p> </td> 
   <td>(Nieuw voor 2.0)</td> 
  </tr> 
 </tbody> 
</table>

### Opportunity {#opportunity}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface Opportunity { <br /> readonly attribute DomString id; <br /> kenmerk Alleen-lezen plaatsing; <br /> alleen-lezen-kenmerk, Objectinstellingen; <br /> kenmerk Alleen-lezen Object customParameters; <br /> }; </p> </td> 
   <td>(Nieuw voor 2.0)</td> 
  </tr> 
 </tbody> 
</table>

### Voorbehoud {#reservation}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface Reservation { <br /> readonly attribute TimeRange; <br /> kenmerk read-only, lange hold; <br /> }; </p> </td> 
   <td> (Nieuw voor 2.0)</td> 
  </tr> 
 </tbody> 
</table>

### Tijdlijn / TijdlijnItem / Tijdlijnmarkeerteken {#timeline-timelineitem-timelinemarker}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p><strong>Tijdlijn</strong>: interface Timeline <br /> {readonly attribute TimelineMarkerList timelineMarkers; <br /> alleen-lezen kenmerk TimelineItemList timelineItems; <br /> double convertToLocalTime( dubbele tijd); <br /> double convertToVirtualTime( dubbele tijd); <br /> };</p> </td> 
   <td><p>interface Timeline {<br /> readonly attribute TimelineMarkerList timelineMarkers;<br /> <br /> <br /> <br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p> <strong>TimelineItem</strong>: interface TimelineItem:<br /> TimelineMarker {<br /> alleen-lezen kenmerk long id; <br /> kenmerk readonly, TimeRange virtualRange; <br /> kenmerk readonly TimeRange localRange; <br /> read-only, kenmerk booleaans gecontroleerd; <br /> read-only, kenmerk boolean temporary; <br /> }; </p> </td> 
   <td>(Nieuw voor 2.0)</td> 
  </tr> 
  <tr> 
   <td><strong>Tijdlijnmarkeerteken</strong>: (Geen wijziging voor 2.0)</td> 
   <td><p>kenmerk double-time van interface TimelineMarker {<br /> alleen-lezen;<br /> kenmerk read-only dubbele duur;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### AdBreak {#adbreak}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface AdBreak {<br /><br /> readonly <br /> <br /> kenmerk double duration;<br /> alleen-lezen kenmerk AdList-advertenties;<br /> <br /> <br /> alleen-lezen kenmerk AdInsertionType insertType;<br /> }; </p> </td> 
   <td><p>interface AdBreak {<br /> readonly attribuut double time;<br /> kenmerk readonly double replaceDuration;<br /> <br /> kenmerk read-only dubbele duur;<br /> alleen-lezen kenmerk AdList enList;<br /> <br /> readOnly-kenmerk DomString-gegevens;<br /> <br /> }; </p> </td> 
  </tr> 
 </tbody> 
</table>

### Advertentie / AdAsset / AdClick / AdList / AdAssetList / AdBannerAsset {#ad-adasset-adclick-adlist-adassetlist-adbannerasset}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p> <strong>Advertentie</strong>: interface Ad {<br /> readonly attribute AdAsset primaryAsset;<br /> kenmerk Alleen-lezen: AdAssetList companionAssets;<br /> <br /> kenmerk read-only dubbele duur;<br /> kenmerk readonly, DomString-id;<br /> const unsigned short ADTYPE_LINEAR = 0;<br /> const unsigned short ADTYPE_NONLINEAR = 1;<br /> <br /> kenmerk readonly, kenmerk unsigned short adType;<br /> alleen-lezen kenmerk AdInsertionType enInsertionType; <br /> <br /> kenmerk readonly boolean klikbaar; <br /> alleen-lezen kenmerk boolean isCustomAdMarker;<br /> }; </p> </td> 
   <td><p>interface Ad {<br /> readonly attribute AdAsset primaryAsset;<br /> kenmerk Alleen-lezen: AdAssetList companionAssets;<br /> <br /> kenmerk read-only dubbele duur;<br /> kenmerk readonly, DomString-id;<br /> const unsigned short ADTYPE_LINEAR = 0;<br /> const unsigned short ADTYPE_NONLINEAR = 1;<br /> <br /> kenmerk readonly, kenmerk unsigned short type;<br /> alleen-lezen kenmerk AdInsertionType insertType; <br /> alleen-lezen kenmerkobjectcontrole;<br /> <br /> <br /> }; </p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdAsset</strong>: (Geen wijziging voor 2.0)</td> 
   <td><p>interface AdAsset {<br /> readonly attribute DomString id;<br /> kenmerk read-only dubbele duur;<br /> kenmerk Alleen-lezen MediaResource-bron;<br /> alleen-lezen kenmerk AdClick enClick;<br /> metagegevens kenmerk kenmerk kenmerk Alleen-lezen;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdClick</strong>: (Geen wijziging voor 2.0)</td> 
   <td><p>interface AdClick {<br /> readonly attribute DomString id;<br /> kenmerk readonly, DomString-titel;<br /> alleen-lezen kenmerk DomString-url;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>Advertentielijst</strong>: (Geen wijziging voor 2.0)</td> 
   <td><p>interface AdList {<br /> readonly attribute unsigned long length;<br /> getter Ad (niet-ondertekende lange index);<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdAssetList</strong>: (Geen wijziging voor 2.0)</td> 
   <td><p>interface AdAssetList {<br /> readonly attribute unsigned long length;<br /> getter AdAsset(unsigned long index);<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p><strong>AdBannerAsset</strong>: interface AdBannerAsset: AdAsset<br /> {<br /> readonly attribute int width;<br /> alleen-lezen kenmerk int hoogte;<br /> readOnly, kenmerk DomString staticUrl;<br /> kenmerk readonly, DomString-hoogte;<br /> kenmerk readonly, DomString-breedte;<br /> };</p> </td> 
   <td> Nieuw in 2.0</td> 
  </tr> 
 </tbody> 
</table>

### AdBreakTimelineItem / AdTimelineItem {#adbreaktimelineitem-adtimelineitem}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p> <strong>AdBreakTimelineItem</strong>: interface AdBreakTimelineItem: TimelineItem { <br /> alleen-lezen kenmerk AdBreak adBreak; <br /> alleen-lezen kenmerk AdTimelineItemList-items; <br /> }; </p> </td> 
   <td> (Nieuw voor 2.0)</td> 
  </tr> 
  <tr> 
   <td><p><strong>AdTimelineItem</strong>: interface AdTimelineItem : TimelineItem { <br /> alleen-lezen kenmerk AdBreak adBreak; <br /> alleen-lezen kenmerk Advertentie; <br /> }; </p> </td> 
   <td> (Nieuw voor 2.0)</td> 
  </tr> 
  <tr> 
   <td><p><strong>AdBreakTimelineItemList</strong>: interface AdBreakTimelineItemList { <br /> alleen-lezen kenmerk lange lengte zonder teken; <br /> getter AdBreakTimelineItem (index zonder teken); <br /> };</p> </td> 
   <td> (Nieuw voor 2.0)</td> 
  </tr> 
 </tbody> 
</table>

### AdBreakPolicy / AdBreakWatchedPolicy / AdPolicy / AdPolicyMode / AdPolicyInfo / AdPolicySelector {#adbreakpolicy-adbreakwatchedpolicy-adpolicy-adpolicymode-adpolicyinfo-adpolicyselector}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface AdBreakPolicy {<br /> readonly attribute short AD_BREAK_POLICY_SKIP;<br /> kenmerk read-only, short AD_BREAK_POLICY_PLAY;<br /> kenmerk read-only short AD_BREAK_POLICY_REMOVE;<br /> kenmerk read-only: short AD_BREAK_POLICY_REMOVE_AFTER_PLAY;<br /> };</p> </td> 
   <td><p> interface AdPolicyConstants {<br /> readonly attribute short AD_BREAK_POLICY_SKIP;<br /> kenmerk read-only, short AD_BREAK_POLICY_PLAY;<br /> kenmerk read-only short AD_BREAK_POLICY_REMOVE;<br /> read-only attribuut short AD_BREAK_POLICY_REMOVE_AFTER_PLAY;}<br /> ..</p> </td> 
  </tr> 
  <tr> 
   <td><p> interface AdBreakWatchedPolicy {<br /> readonly attribute short AD_BREAK_AS_WATCHED_ON_BEGIN;<br /> kenmerk read-only short AD_BREAK_AS_WATCHED_ON_END;<br /> kenmerk readonly, short AD_BREAK_AS_WATCHED_NEVER;<br /> }; </p> </td> 
   <td><p> ...<br /> kenmerk read-only: short AD_BREAK_AS_WATCHED_ON_BEGIN;<br /> kenmerk read-only short AD_BREAK_AS_WATCHED_ON_END;<br /> kenmerk readonly, short AD_BREAK_AS_WATCHED_NEVER;<br /> ...</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicy {<br /> readonly attribute short AD_POLICY_PLAY;<br /> kenmerk read-only: short AD_POLICY_PLAY_FROM_AD_BEGIN;<br /> kenmerk read-only: short AD_POLICY_PLAY_FROM_AD_BREAK_BEGIN; kenmerk read-only: short AD_POLICY_SKIP_TO_NEXT_AD_IN_BREAK;<br /> <br /> kenmerk readonly, short AD_POLICY_SKIP_AD_BREAK;<br /> };</p> </td> 
   <td><p> ... <br /> read-only attribuut short AD_POLICY_PLAY;<br /> kenmerk read-only: short AD_POLICY_PLAY_FROM_AD_BEGIN;<br /> kenmerk read-only: short AD_POLICY_PLAY_FROM_AD_BREAK_BEGIN;<br /> kenmerk read-only: short AD_POLICY_SKIP_TO_NEXT_AD_IN_BREAK;<br /> kenmerk readonly, short AD_POLICY_SKIP_AD_BREAK;<br /> ...</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicyMode {<br /> readonly attribute short AD_POLICY_MODE_PLAY;<br /> read-only attribuut short AD_POLICY_MODE_SEEK;<br /> read-only attribuut short AD_POLICY_MODE_TRICKPLAY;<br /> };</p> </td> 
   <td><p> ...<br /> {readonly attribute short AD_POLICY_MODE_PLAY;<br /> read-only attribuut short AD_POLICY_MODE_SEEK;<br /> read-only attribuut short AD_POLICY_MODE_TRICKPLAY;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicyInfo {<br /> alleen-lezen kenmerk AdBreakTimelineItemList <br /> en BreakTimelineItems;<br /> alleen-lezen kenmerk AdTimelineItem enTimelineItem;<br /> kenmerk readonly double currentTime;<br /> kenmerk readonly double seekToTime;<br /> kenmerk Alleen-lezen dubbele frequentie;<br /> kenmerk short-mode alleen-lezen; //AdPolicyMode<br /> };</p> </td> 
   <td><p>interface AdPolicyInfo {<br /> readonly attribute AdBreakPlacementList <br /> en BreakPlacements;<br /> alleen-lezen kenmerk Advertentie;<br /> kenmerk readonly double currentTime;<br /> kenmerk readonly double seekToTime;<br /> kenmerk Alleen-lezen dubbele frequentie;<br /> kenmerk short-mode alleen-lezen; //AdPolicyMode<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicySelector {<br /> /**<br /> * AdbreakPolicy selectPolicyForAdBreak(<br /> * AdPolicyInfo enPolicyInfo);<br /> */<br /> attribute Object selectPolicyForAdBreakCallbackFunc;<br /> /**<br /> * AdBreakTimelineItemList selectAdBreaksToPlay(<br /> * AdPolicyInfo enPolicyInfo);<br /> */<br /> attribute Object selectAdBreaksToPlayCallbackFunc;<br /> /**<br /> * AdPolicy selectPolicyForSeekIntoAd(AdPolicyInfo enPolicyInfo);<br /> */<br /> attribute Object selectPolicyForSeekIntoAdCallbackFunc; <br /> /**<br /> * AdBreakWatchedPolicy selectWatchedPolicyForAdBreak(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectWatchedPolicyForAdBreakCallbackFunc;<br /> };</p> </td> 
   <td><p>interface AdPolicySelector {<br /> /**<br /> * AdbreakPolicy selectPolicyForAdBreak(<br /> * AdPolicyInfo enPolicyInfo);<br /> */<br /> attribute Object selectPolicyForAdBreakFuncCallback;<br /> /**<br /> * AdBreakPlacementList selectAdBreaksToPlay(<br /> * AdPolicyInfo enPolicyInfo);<br /> */<br /> attribute Object selectAdBreaksToPlayCallback;<br /> /**<br /> * AdPolicy selectPolicyForSeekIntoAd(AdPolicyInfo enPolicyInfo);<br /> */<br /> attribute Object selectPolicyForSeekIntoAdCallback; <br /> /**<br /> * AdBreakAsWatched selectWatchedPolicyForAdBreak(<br /> * AdPolicyInfo enPolicyInfo);<br /> */<br /> attribute Object selectWatchedPolicyForAdBreakCallback;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### TimelineOperation {#timelineoperation}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface TimelineOperation { <br /> readonly attribute Placement placement ; <br /> };</p> </td> 
   <td> (Nieuw voor 2.0)</td> 
  </tr> 
 </tbody> 
</table>

### AdBreakPlacement {#adbreakplacement}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface AdBreakPlacement : TimelineOperation {<br /> alleen-lezen kenmerk AdBreak adBreak;<br /> kenmerk Alleen-lezen plaatsing; // kenmerk double-time van kenmerk TimelineOperation<br /> alleen-lezen;<br /> kenmerk read-only dubbele duur;<br /> };</p> </td> 
   <td><p>interface AdBreakPlacement {<br /> alleen-lezen kenmerk AdBreak adBreak;<br /> kenmerk Alleen-lezen plaatsing;<br /> kenmerk Alleen-lezen dubbele tijd;<br /> kenmerk read-only dubbele duur;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### AuditudeSettings {#auditudesettings}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface AuditudeSettings: AdvertisingMetadata { <br /> -kenmerk DomString zoneId; <br /> kenmerk DomString mediaId; <br /> kenmerk DomString defaultMediaId ; <br /> attribuut DomString domain; <br /> kenmerk Object targetInfo ; <br /> attribuut Object customParameters ; <br /> attribute Boolean creativePackingEnabled ;<br /> attribute Boolean showStaticBanners ;<br /> };</p> </td> 
   <td>Functionaliteit is opgegeven door MetadataKeys::AUDITUDE_METADATA_KEY.</td> 
  </tr> 
 </tbody> 
</table>

## Wijzigingen in API-element voor aanpassing voor 2.0 {#customization-api-element-changes-for}

In deze tabellen worden de aanpassing-API-elementen voor de JavaScript-TVSDK vergeleken tussen versie 1.3 en 2.0.

Tabellen in dit onderwerp:

* MediaPlayerItemConfig
* ContentFactory
* NetworkConfiguration

### MediaPlayerItemConfig {#mediaplayeritemconfig}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API's</th> 
   <th>1.3 API's</th> 
  </tr> 
  <tr> 
   <td><p>interface MediaPlayerItemConfig {<br /> kenmerk ContentFactory en Factory;<br /> attribute StringList subscribeTags;<br /> <br /> kenmerk StringList enTags;<br /> <br /> <br /> attribuut AdSignalingMode enSignalingMode;<br /> attribute CustomRangeMetadata customRangeMetadata;<br /> attribuut NetworkConfiguration networkConfiguration;<br /> kenmerk AdvertisingMetadata advertenceMetadata;<br /> attribute Boolean useHardwareDecoder;<br /> };</p> </td> 
   <td><p>interface MediaPlayerConfig {<br /><br /> <br /> <br /> attributen StringList enTags;<br /> attribute StringList subscribedTags;<br /> kenmerk MediaPlayerClientFactory clientFactory;<br /> <br /> <br /> <br /> <br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### ContentFactory {#contentfactory}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API's</th> 
   <th>1.3 API's</th> 
  </tr> 
  <tr> 
   <td><p>interface ContentFactory {<br /> /*<br /> * AdPolicySelector retrieveAdPolicySelector(<br /> * MediaPlayerItem item);<br /> */<br /> attribute Object retrieveAdPolicySelectorCallbackFunc;<br /> };</p> </td> 
   <td><p>interface MediaPlayerClientFactory {<br /> /*<br /> * AdPolicySelector retrieveAdPolicySelector(<br /> * MediaPlayerItem item);<br /> */<br /> attribute Object retrieveAdPolicySelectorFunc;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### NetworkConfiguration {#networkconfiguration}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API's</th> 
   <th>1.3 API's</th> 
  </tr> 
  <tr> 
   <td><p>interface NetworkConfiguration<br /> {<br /> attribute boolean forceNativeNetworking;<br /> attribute boolean useRedirectedUrl;<br /> attribute Object cookieHeader;<br /> attribute boolean readSetCookieHeader;<br /> kenmerk int masterUpdateInterval; <br /> attribuut boolean useCookieHeaderForAllRequests;<br /> attribute int readLimit;<br /> };</p> </td> 
   <td>In 1.3 werd een deel van deze functionaliteit geleverd door MetadataKeys</td> 
  </tr> 
 </tbody> 
</table>

## Wijzigingen in DRM API-element voor 2.0 {#drm-api-element-changes-for}

In deze tabellen worden de DRM API-elementen voor de JavaScript-TVSDK vergeleken tussen versie 1.3 en 2.0.

Tabellen in dit onderwerp:

* Initialisatie DRM-workflow
* DRMAcquireLicenseSettings / DRMAuthenticationMethod
* DRMMetadata
* DRMPlaybackTimeWindow
* DRMLicense
* DRMLicenseDomain
* DRMPopolicy
* DRMManager

### Initialisatie DRM-workflow {#drm-workflow-initialization}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API's</th> 
   <th>1.3 API's</th> 
  </tr> 
  <tr> 
   <td>De toepassing moet AdobePSDK.initisDRMWorkflow aanroepen om de DRM-workflow te starten. Zonder deze oproep worden DRM-video's niet afgespeeld.<p>interface AdobePSDK<br /> {<br /> void initiDRMWorkFlow(<br /> DomString appStoratePath, <br /> DomString publisherId, <br /> DomString appId, <br /> DomString appVersion, <br /> booleaanse privacyModeOn);<br /> };</p> </td> 
   <td>De initialisering werd gedaan intern en geen expliciete vraag werd vereist.</td> 
  </tr> 
 </tbody> 
</table>

### DRMAcquireLicenseSettings/DRMAuthenticationMethod {#drmacquirelicensesettings-drmauthenticationmethod}

| 2.0 API&#39;s | 1.3 API&#39;s |
|--- |--- |
| **DRMAcquireLicenseSettings** |  |
| Geen wijziging voor 2.0. | enum DRMAcquireLicenseSettings <br>{<br> const unsigned int FORCE_REFRESH = 0;<br> const unsigned int LOCAL_ONLY = 1;<br> const unsigned int ALLOW_SERVER = 2;<br> }; |
| **DRMAuthenticationMethod** |  |
| Geen wijziging voor 2.0. | enum DRMAuthenticationMethod <br>{<br> const unsigned int UNKNOWN = 0;<br> const zonder teken in ANONYMOUS = 1;<br> const unsigned int USERNAME_AND_PASSWORD = 2;<br> } |

### DRMMetadata {#drmmetadata}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API's</th> 
   <th>1.3 API's</th> 
  </tr> 
  <tr> 
   <td>Geen wijziging voor 2.0.</td> 
   <td><p>interface DRMMetadata<br /> {<br /> readonly attributen DomString serverUrl;<br /> kenmerk readonly, DomString licenseId;<br /> alleen-lezen kenmerk DRMPopolicyArray-beleid; <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMPlaybackTimeWindow {#drmplaybacktimewindow}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API's</th> 
   <th>1.3 API's</th> 
  </tr> 
  <tr> 
   <td><p>interface DRMPlaybackTimeWindow {<br /> readonly attribute int playbackPeriodInSeconds;<br /> readOnly, kenmerk long playbackStartDate;<br /> readOnly, kenmerk long playbackEndDate;<br /> };</p> </td> 
   <td><p>interface DRMPlaybackTimeWindow {<br /> readonly attribute int periodInSeconds;<br /> readOnly, kenmerk int startDate;<br /> readOnly, kenmerk int endDate;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMLicense {#drmlicense}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API's</th> 
   <th>1.3 API's</th> 
  </tr> 
  <tr> 
   <td>Geen wijziging voor 2.0.</td> 
   <td><p>interface DRMLicense {<br /> readonly attribute Uint8Array bytes;<br /> readOnly, kenmerk Date licenseStartDate;<br /> kenmerk readonly Date licenseEndDate;<br /> kenmerk readonly Date offlineStorageStartDate;<br /> alleen-lezen kenmerk Date offlineStorageEndDate; <br /> kenmerk readonly, DomString serverUrl;<br /> kenmerk readonly, DomString licenseID;<br /> readOnly-kenmerk DomString policyID;<br /> readOnly, kenmerk DRMPlaybackTimeWindow playbackTimeWindow;<br /> kenmerk Alleen-lezen Object customProperties;<br /> }; </p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMLicenseDomain {#drmlicensedomain}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API's</th> 
   <th>1.3 API's</th> 
  </tr> 
  <tr> 
   <td><p>interface DRMLicenseDomain {<br /> readonly attribute DomString authenticationDomain;<br /> kenmerk readOnly DRMAuthenticationMethod authenticationMethod; <br /> kenmerk readonly, DomString serverUrl;<br /> };</p> </td> 
   <td><p>interface DRMLicenseDomain {<br /> readonly attribute DomString authDomain;<br /> readOnly, kenmerk DRMAuthenticationMethod authMethod; <br /> readOnly-kenmerk DomString serverURL;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMPopolicy {#drmpolicy}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API's</th> 
   <th>1.3 API's</th> 
  </tr> 
  <tr> 
   <td><p>interface DRMPopolicy<br /> {<br /> readonly attribute DomString authenticationDomain;<br /> kenmerk readOnly DRMAuthenticationMethod authenticationMethod;<br /> <br /> kenmerk readonly, DomString displayName;<br /> read-only attribute DRMLicenseDomain licenseDomain;<br /> };</p> </td> 
   <td><p>interface DRMPopolicy<br /> {<br /> readonly attribute DomString authDomain;<br /> readOnly, kenmerk DRMAuthenticationMethod authMethod;<br /> readOnly-kenmerk DomString dispName;<br /> read-only attribute DRMLicenseDomain licenseDomain;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMManager {#drmmanager}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API's</th> 
   <th>1.3 API's</th> 
  </tr> 
  <tr> 
   <td><p>interface DRMManager: EventTarget {<br /> void verwervingLicense(DRMMetadata metadata, <br /> DRMAcquireLicenseSettings setting, <br /> DRMAquireLicenseListener listener);<br /> void verwervingPreviewLicense(DRMMetadata-metagegevens, <br /> DRMAquireLicenseListener-listener);<br /> void authenticate (DRMMetadata-metagegevens, <br /> DomString url,<br /> DomString&amp;authenticationDomain, <br /> DomString-gebruiker, <br /> DomString-wachtwoord, <br /> DRMAuthenticateListener-listener);<br /> <br /> DRMMetadata createMetadataFromBytes(<br /> Uint8Array-array, DRMErrorListener-listener);<br /> void initialize(DRMOperationCompleteListener-listener);<br /> kenmerk long maxOperationTime;<br /> <br /> void joinLicenseDomain(<br /> DRMLicenseDomain licenseDomain, <br /> boolean forceRefresh, <br /> DRMOperationCompleteListener listener);<br /> void leaveLicenseDomain(<br /> DRMLicenseDomain licenseDomain, <br /> DRMOperationCompleteListener listener);<br /> <br /> void resetDRM(DRMOperationCompleteListener listener);<br /> void returnLicense(DomString serverURL, <br /> DomString licenseID, <br /> DomString policyID, <br /> boolean commitImmediatically,<br /> DRMReturnLicenseListener listener);<br /> void setAuthenticationToken(<br /> DRMMetadata-metagegevens, <br /> DomString-verificatiedomein, <br /> Uint8Array-token, <br /> DRMOperationCompleteListener-listener);<br /> void storeLicenseBytes(Uint8Array, <br /> DRMOperationCompleteListener listener);<br /> };</p> </td> 
   <td><p>interface DRMManager: EventTarget {<br /> void verwervingLicense(DRMMetadata metadata, <br /> DRMAcquireLicenseSettings setting, <br /> EventContext eventContext);<br /> void verwervingPreviewLicense(DRMMetadata-metagegevens, <br /> EventContext eventContext);<br /> void authenticate (DRMMetadata-metagegevens, <br /> DomString url,<br /> DomString&amp;authenticationDomain, <br /> DomString-gebruiker, <br /> DomString-wachtwoord, <br /> EventContext-gebeurtenisContext);<br /> <br /> DRMMetadata createMetadataFromBytes(<br /> Uint8Array-array, EventContext eventContext);<br /> void initialize(EventContext eventContext);<br /> kenmerk long maxOperationTime;<br /> <br /> void joinLicenseDomain(<br /> DRMLicenseDomain licenseDomain, <br /> boolean forceRefresh, <br /> EventContext eventContext);<br /> void leaveLicenseDomain(<br /> DRMLicenseDomain licenseDomain, <br /> EventContext eventContext);<br /> <br /> void resetDRM(EventContext eventContext);<br /> void returnLicense(DomString serverURL, <br /> DomString licenseID,<br /> DomString policyID, <br /> boolean commitImmediatically,<br /> EventContext eventContext);<br /> void setAuthenticationToken(<br /> DRMMetadata-metagegevens, <br /> DomString-verificatiedomein, <br /> uint8Array-token, <br /> EventContext-gebeurteniscontext);<br /> void storeLicenseBytes(Uint8Array licenseBytes, <br /> EventContext eventContext);<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>klasse DRMErrorListener: <br /> public psdkutils::PSDKInterfaceWithUserData {<br /> public:<br /> virtual void onDRMError(uint32_t major, <br /> uint32_t minor, <br /> const psdkutils: PSDKString&amp; errorString, <br /> const psdkutils::PSDKString&amp; errorServerUrl) = 0;<br /> <br /> beveiligd:<br /> virtual ~DRMErrorListener() {}<br /> }</p> </td> 
   <td>Gebeurtenis/interface/beschrijving 
    <ul> 
     <li>kEventDRMOperationError<p>/ DRMOperationErrorEvent</p> <p>Wanneer een fout tijdens één van de asynchrone methodes van DRMManger voorkomt.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>klasse DRMOperationCompleteListener: <br /> public DRMErrorListener {<br /> public:<br /> virtuele void onDRMOperationComplete() = 0;<br /> <br /> beveiligd:<br /> virtual ~DRMOperationCompleteListener() {}<br /> };</p> </td> 
   <td>Gebeurtenis/interface/beschrijving 
    <ul> 
     <li>kEventDRMInitializationComplete<p>/ PSDKEvent</p> <p>Wanneer de initialisatie van DRM is voltooid.</p> </li> 
     <li>kEventDRMJoinLicenseDomainComplete<p>/ PSDKEvent</p> <p>Wanneer de joinLicenseDomain()-actie met succes is voltooid.</p> </li> 
     <li>kEventDRMLeaveLicenseDomainComplete<p>/ PSDKEvent</p> <p>Wanneer de handeling leaveLicenseDomain() correct is voltooid.</p> </li> 
     <li>kEventDRMResetCompletePSDKEvent<p>/ PSDKEvent</p> <p>Wanneer resetDRM()-actie correct is voltooid.</p> </li> 
     <li>kEventDRMAuthenticationTokenSet<p>/ PSDKEvent</p> <p>Wanneer de handeling setAuthenticationTokenSet() correct is voltooid.</p> </li> 
     <li>kEventDRMLicenseStored<p>/ PSDKEvent</p> <p>Wanneer de handeling storeLicenseBytes() correct is voltooid.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>klasse DRMAuthenticateListener: <br /> public DRMErrorListener {<br /> public:<br /> virtual void onAuthenticationComplete(<br /> psdkutils::PSDKImmutableByteArray* <br /> authenticationToken) = 0;<br /> <br /> beveiligd:<br /> virtual ~DRMAuthenticateListener() {}<br /> }</p> </td> 
   <td>Gebeurtenis/interface/beschrijving 
    <ul> 
     <li>kEventDRMAuthenticationComplete<p>/ DRMAuthenticationCompleteEvent</p> <p>Wanneer DRMManager::authenticate de methodevraag succesvol is.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>klasse DRMAquireLicenseListener: <br /> public DRMErrorListener {<br /> public:<br /> virtuele void onLicenseAcquired(const DRMLicense*) = 0;<br /> <br /> beveiligd:<br /> virtual ~DRMAquireLicenseListener() {}<br /> };</p> </td> 
   <td>Gebeurtenis/interface/beschrijving 
    <ul> 
     <li>kEventDRMPreviewLicenseAcquired<p>/ DRMLicenseAcquiredEvent</p> <p>Wanneer DRMManager::verwervingPreviewLicense is aangeroepen.</p> </li> 
     <li>kEventDRMLicenseAcquired<p>/ DRMLicenseAcquiredEvent</p> <p>Wanneer DRMManager::verwervingLicense, aanroep van de methode succesvol is.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>klasse DRMReturnLicenseListener: <br /> public DRMErrorListener {<br /> public:<br /> virtuele void onLicenseReturnComplete(uint32_t numGeretourneerd ) = 0;<br /> <br /> beveiligd:<br /> virtual ~DRMReturnLicenseListener() {}<br /> };</p> </td> 
   <td>Gebeurtenis/interface/beschrijving 
    <ul> 
     <li>kEventDRMLicenseReturnComplete<p>/ DRMLicenseReturnCompleteEvent</p> <p>Wanneer DRMManager::returnLicense, aanroep van de methode succesvol is.</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Algemene wijzigingen in API-element voor afspelen voor 2.0 {#generic-playback-api-element-changes-for}

In deze tabellen worden de algemene API-afspeelelementen vergeleken tussen JavaScript TVSDK 1.3 en 2.0.

Tabellen in dit onderwerp:

* MediaResource
* MediaPlayer
* ABRControlParameters
* BufferControlParameters
* TextFormat
* MediaPlayerItemLoader

### MediaResource {#mediaresource}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API's</th> 
   <th>1.3 API's</th> 
  </tr> 
  <tr> 
   <td><p>interface MediaResource {<br /> kenmerk DomString url; <br /> kenmerk zonder teken kort type;<br /> metagegevens kenmerkobject;<br /> const unsigned short TYPE_HLS;<br /> const unsigned short TYPE_HDS;<br /> const unsigned short TYPE_DASH;<br /> const unsigned short TYPE_CUSTOM;<br /> const unsigned short TYPE_UNKNOWN;<br /> };</p> </td> 
   <td><p>interface MediaResource {<br /> kenmerk DomString url;<br /> attribuut DomString type;<br /> metagegevens kenmerkobject;<br /> <br /> <br /> <br /> <br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### MediaPlayer {#mediaplayer}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API's</th> 
   <th>1.3 API's</th> 
  </tr> 
  <tr> 
   <td><p>interface MediaPlayer: EventTarget<br /> {<br /> void prepareToPlay( dubbele positie);<br /> void play();<br /> void pause();<br /> void seek( dubbele positie);<br /> void seekToLocal( dubbele positie);<br /> void reset();<br /> void release();<br /> void replaceCurrentItem(MediaPlayerItem item);<br /> void replaceCurrentResource(MediaResource-bron, <br /> MediaPlayerItemConfig-config); <br /> void suspend();<br /> void restore();<br /> void notifyClick();<br /> <br /> readonly attribute TimeRange playbackRange;<br /> alleen-lezen kenmerk TimeRange seekableRange;<br /> kenmerk readonly double currentTime;<br /> kenmerk readonly double localTime;<br /> readonly attribute TimeRange bufferedRange;<br /> readOnly, kenmerk DRMManager drmManager;<br /> readOnly, kenmerk MediaPlayerItem currentItem;<br /> <br /> // PlayerStatus<br /><br /> <br /> const unsigned short PLAYER_STATUS_INITIALIZED;<br /> const unsigned short PLAYER_STATUS_PREPARING;<br /> const unsigned short PLAYER_STATUS_PREPARED;<br /> const unsigned short PLAYER_STATUS_PLAYING;<br /> const unsigned short PLAYER_STATUS_PAUSED;<br /> const unsigned short PLAYER_STATUS_SEEKING;<br /> const unsigned short PLAYER_STATUS_COMPLETE;<br /> const unsigned short PLAYER_STATUS_ERROR;<br /> const unsigned short PLAYER_STATUS_RELEASED;<br /> <br /> kenmerk readonly, kenmerk unsigned short status;<br /> <br /> kenmerk unsigned short volume;<br /> kenmerk ABRControlParameters abrControlParameters;<br /> attribuut BufferControlParameters bufferControlParameters;<br /> <br /> const unsigned short VISIBLE; //Voor CC-zichtbaarheidsconst<br /> zonder teken kort ONZICHTBAAR; //Voor CC visibility<br /> -kenmerk unsigned short ccVisibility<br /> attribute TextFormat ccStyle;<br /> alleen-lezen kenmerk PlaybackMetrics playbackMetrics;<br /> <br /> dubbel tarief;<br /> kenmerk MediaPlayerView;<br /> kenmerk Alleen-lezen tijdlijn;<br /> kenmerk double currentTimeUpdateInterval; <br /> // het plaatsen van dit zal niet voor 2.0<br /> } worden gesteund;</p> </td> 
   <td><p>interface MediaPlayer: EventTarget<br /> {<br /> void prepareToPlay( int positie);<br /> void play();<br /> void pause();<br /> void seek( int position);<br /> void seekToLocalTime( int position);<br /> void reset();<br /> void release();<br /> void replaceCurrentItem(MediaResource-bron);<br /> <br /> <br /> <br /> <br /> <br /> <br /> readonly attribute TimeRange playbackRange;<br /> alleen-lezen kenmerk TimeRange seekableRange;<br /> kenmerk readonly double currentTime;<br /> kenmerk readonly double localTime;<br /> readonly attribute TimeRange bufferedRange;<br /> readOnly, kenmerk DRMManager drmManager;<br /> readOnly, kenmerk MediaPlayerItem currentItem;<br /> <br /> // PlayerState<br /> const unsigned short PLAYER_STATE_IDLE;<br /> const unsigned short PLAYER_STATE_INITIALIZING;<br /> const unsigned short PLAYER_STATE_INITIALIZED;<br /> const unsigned short PLAYER_STATE_PREPARING;<br /> const unsigned short PLAYER_STATE_PREPARED;<br /> const unsigned short PLAYER_STATE_PLAYING;<br /> const unsigned short PLAYER_STATE_PAUSED;<br /> const unsigned short PLAYER_STATE_SEEKING;<br /> const unsigned short PLAYER_STATE_COMPLETE;<br /> const unsigned short PLAYER_STATE_ERROR;<br /> const unsigned short PLAYER_STATE_RELEASED;<br /> const unsigned short PLAYER_STATUS_SUSPENDED;<br /> kenmerk readonly, kenmerk unsigned short state;<br /> <br /> kenmerk unsigned short volume;<br /> kenmerk ABRControlParameters abrControlParameters;<br /> attribuut BufferControlParameters bufferControlParameters;<br /> <br /> alleen-lezen zonder teken kort ZICHTBAAR; //Voor CC-zichtbaarheid<br /> alleen lezen zonder teken kort ONZICHTBAAR; //Voor CC visibility<br /> -kenmerk unsigned short ccVisibility<br /> attribute TextFormat ccStyle;<br /> alleen-lezen kenmerk PlaybackMetrics playbackMetrics;<br /> kenmerk MediaPlayerConfig mediaPlayerConfig;<br /> dubbel tarief;<br /> kenmerk MediaPlayerView;<br /> kenmerk Alleen-lezen tijdlijn;<br /> <br /> <br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface MediaPlayerStatus<br /> {<br /> // PlayerStatus<br /> const unsigned short PLAYER_STATUS_IDLE;<br /> const unsigned short PLAYER_STATUS_INITIALIZING;<br /> const unsigned short PLAYER_STATUS_INITIALIZED;<br /> const unsigned short PLAYER_STATUS_PREPARING;<br /> const unsigned short PLAYER_STATUS_PREPARED;<br /> const unsigned short PLAYER_STATUS_PLAYING;<br /> const unsigned short PLAYER_STATUS_PAUSED;<br /> const unsigned short PLAYER_STATUS_SEEKING;<br /> const unsigned short PLAYER_STATUS_COMPLETE;<br /> const unsigned short PLAYER_STATUS_ERROR;<br /> const unsigned short PLAYER_STATUS_RELEASED;<br /> const unsigned short PLAYER_STATUS_SUSPENDED;<br /> };</p> </td> 
   <td>(Nieuw voor 2.0)</td> 
  </tr> 
 </tbody> 
</table>

#### Gebeurtenissen ondersteund door MediaPlayer {#events-supported-by-mediaplayer}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 Naam van gebeurtenis</th> 
   <th>2.0 Interface</th> 
   <th> </th> 
   <th>1.3 Naam van gebeurtenis</th> 
   <th>1.3 Interface</th> 
  </tr> 
  <tr> 
   <td><p>(geschrapt voor 2.0)</p> </td> 
   <td> </td> 
   <td> </td> 
   <td>voorbereid</td> 
   <td>Gebeurtenis</td> 
  </tr> 
  <tr> 
   <td><p>itemUpdated</p> <p>Wanneer een mediaspeler-item wordt bijgewerkt.</p> </td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>bijgewerkt</p> <p>Wanneer de mediaspeler de media heeft bijgewerkt.</p> </td> 
   <td>Gebeurtenis</td> 
  </tr> 
  <tr> 
   <td>timedMetadataAvailable</td> 
   <td>TimedMetadataEvent</td> 
   <td> </td> 
   <td>TtedMetadata</td> 
   <td>TimedMetadataEvent</td> 
  </tr> 
  <tr> 
   <td>timelineUpdated</td> 
   <td>Gebeurtenis</td> 
   <td> </td> 
   <td>TextLineUpdated</td> 
   <td>Gebeurtenis</td> 
  </tr> 
  <tr> 
   <td>Verwijderd in 2.0</td> 
   <td> </td> 
   <td> </td> 
   <td>playStart</td> 
   <td>Gebeurtenis</td> 
  </tr> 
  <tr> 
   <td>Verwijderd voor 2.0</td> 
   <td> </td> 
   <td> </td> 
   <td>playComplete</td> 
   <td>Gebeurtenis</td> 
  </tr> 
  <tr> 
   <td>statusChanged</td> 
   <td>StatusEvent</td> 
   <td> </td> 
   <td>stateChanged</td> 
   <td>StateEvent</td> 
  </tr> 
  <tr> 
   <td>sizeAvailable</td> 
   <td>SizeEvent</td> 
   <td> </td> 
   <td>size</td> 
   <td>SizeEvent</td> 
  </tr> 
  <tr> 
   <td>adBreakStarted</td> 
   <td>AdBreakEvent</td> 
   <td> </td> 
   <td>adBreakStart</td> 
   <td>AdBreakEvent</td> 
  </tr> 
  <tr> 
   <td>adStarted</td> 
   <td>AdEvent</td> 
   <td> </td> 
   <td>adStart</td> 
   <td>AdEvent</td> 
  </tr> 
  <tr> 
   <td>adProgress</td> 
   <td>AdProgressEvent</td> 
   <td> </td> 
   <td>adProgress</td> 
   <td>AdProgressEvent</td> 
  </tr> 
  <tr> 
   <td>adCompleted</td> 
   <td>AdEvent</td> 
   <td> </td> 
   <td>progressComplete</td> 
   <td>AdEvent</td> 
  </tr> 
  <tr> 
   <td>adBreakCompleted</td> 
   <td>AdBreakEvent</td> 
   <td> </td> 
   <td>adBreakComplete</td> 
   <td>AdBreakEvent</td> 
  </tr> 
  <tr> 
   <td>timeChanged</td> 
   <td>TimeEvent</td> 
   <td> </td> 
   <td>buffer</td> 
   <td>ProgressEvent</td> 
  </tr> 
  <tr> 
   <td>bufferingBegin</td> 
   <td>Gebeurtenis</td> 
   <td> </td> 
   <td>Progress</td> 
   <td>Gebeurtenis</td> 
  </tr> 
  <tr> 
   <td>bufferingEnd</td> 
   <td>Gebeurtenis</td> 
   <td> </td> 
   <td>bufferComplete</td> 
   <td>Gebeurtenis</td> 
  </tr> 
  <tr> 
   <td>seekBegin</td> 
   <td>SeekEvent</td> 
   <td> </td> 
   <td>seekStart</td> 
   <td>Gebeurtenis</td> 
  </tr> 
  <tr> 
   <td>seekEnd</td> 
   <td>SeekEvent</td> 
   <td> </td> 
   <td>seekComplete</td> 
   <td>TimeEvent</td> 
  </tr> 
  <tr> 
   <td>loadInformationAvailable</td> 
   <td>LoadInformationEvent</td> 
   <td> </td> 
   <td>loadInfo</td> 
   <td>LoadInfoEvent</td> 
  </tr> 
  <tr> 
   <td>operationFailed</td> 
   <td>NotificationEvent</td> 
   <td> </td> 
   <td>operationFailed</td> 
   <td>ErrorEvent</td> 
  </tr> 
  <tr> 
   <td>drmMetadataInfoAvailable</td> 
   <td>DRMMetadataEvent</td> 
   <td> </td> 
   <td>drmMetadata</td> 
   <td>DRMMetadataEvent</td> 
  </tr> 
  <tr> 
   <td>reserveringReached</td> 
   <td>ReservationEvent</td> 
   <td> </td> 
   <td>timelineHolderReached</td> 
   <td>TimelineHolderEvent</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td>bitrateChanged</td> 
   <td>BitrateChangedEvent</td> 
  </tr> 
  <tr> 
   <td>rateSelected</td> 
   <td>PlaybackRateEvent</td> 
   <td> </td> 
   <td>rateSelected</td> 
   <td>PlaybackRateEvent</td> 
  </tr> 
  <tr> 
   <td>ratePplaying</td> 
   <td>PlaybackRateEvent</td> 
   <td> </td> 
   <td>ratePplaying</td> 
   <td>PlaybackRateEvent</td> 
  </tr> 
  <tr> 
   <td>adBreakSkipped</td> 
   <td>AdBreakEvent</td> 
   <td> </td> 
   <td>adBreakSkipped</td> 
   <td>AdBreakEvent</td> 
  </tr> 
  <tr> 
   <td>Klik<br /> wanneer de gebruiker op een advertentie klikt.</td> 
   <td>AdClickedEvent</td> 
   <td> </td> 
   <td><p>Nieuw in 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>profileChanged<br /> When the playback profile changes.</td> 
   <td>ProfileEvent</td> 
   <td> </td> 
   <td><p>Nieuw in 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>seekPositionAdjusted<br /> Wanneer de zoekpositie wordt aangepast vanwege interne of externe regels.</td> 
   <td>SeekEvent</td> 
   <td> </td> 
   <td><p>Nieuw in 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>audioBijgewerkt<br /> wanneer een item van een mediaspeler wordt bijgewerkt. Voor bepaalde streams die audiotracks bevatten die alleen tijdens het afspelen kunnen worden gedetecteerd, wordt deze gebeurtenis geactiveerd wanneer nieuwe audiotracks beschikbaar zijn.</td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>Nieuw in 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>captionsUpdated <br /> Wanneer een media player-item wordt bijgewerkt. Voor live/lineaire streams moet de client de mediabron periodiek vernieuwen om de nieuwe beschikbare inhoud te detecteren. Wanneer dit gebeurt, zouden bepaalde media kenmerken kunnen veranderen.</td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>Nieuw in 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>masterUpdated <br /> Wanneer een media player-item wordt bijgewerkt. Voor live/lineaire streams moet de client de mediabron periodiek vernieuwen om de nieuwe beschikbare inhoud te detecteren. Wanneer dit gebeurt, zouden bepaalde media kenmerken kunnen veranderen.</td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>Nieuw in 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>playbackRangeUpdated<br /> Wanneer een media playerpunt wordt bijgewerkt. Voor live/lineaire streams moet de client de mediabron periodiek vernieuwen om de nieuwe beschikbare inhoud te detecteren. Wanneer dit gebeurt, zouden bepaalde media kenmerken kunnen veranderen.</td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>Nieuw in 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>timedEvent<br /> Verzonden wanneer gebeurtenissen met tijdslimiet worden gegenereerd.</td> 
   <td>TimedEvent</td> 
   <td> </td> 
   <td><p>Nieuw in 2.0</p> </td> 
  </tr> 
 </tbody> 
</table>

### ABRControlParameters {#abrcontrolparameters}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API's</th> 
   <th>1.3 API's</th> 
  </tr> 
  <tr> 
   <td><p>interface ABRControlParameters<br /> {<br /> const unsigned short ABR_POLICY_CONSERVATIVE = 0;<br /> const unsigned short ABR_POLICY_MODERATE = 1;<br /> const unsigned short ABR_POLICY_AGGRESIVE = 2;<br /> <br /> kenmerk unsigned short abrPolicy;<br /> kenmerk unsigned int initialBitRate;<br /> kenmerk unsigned int minBitRate;<br /> kenmerk unsigned int maxBitRate;<br /> const unsigned short DEFAULT_ABR_INITIAL_BITRATE;<br /> const unsigned short DEFAULT_ABR_MIN_BITRATE;<br /> const unsigned short DEFAULT_ABR_MAX_BITRATE;<br /> const ABRPopolicy DEFAULT_ABR_POLICY;<br /> };</p> </td> 
   <td><p>interface ABRControlParameters<br /> {<br /> const unsigned short ABR_POLICY_CONSERVATIVE = 0;<br /> const unsigned short ABR_POLICY_MODERATE = 1;<br /> const unsigned short ABR_POLICY_AGGRESIVE = 2;<br /> <br /> kenmerk unsigned short abrPolicy;<br /> kenmerk unsigned int initialBitRate;<br /> kenmerk unsigned int minBitRate;<br /> kenmerk unsigned int maxBitRate;<br /> <br /> <br /> <br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### BufferControlParameters {#buffercontrolparameters}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API's</th> 
   <th>1.3 API's</th> 
  </tr> 
  <tr> 
   <td><p>interface BufferControlParameters<br /> {<br /> attribuut double initialBufferTime;<br /> kenmerk double playBufferTime;<br /> const double DEFAULT_INITIAL_BUFFER_TIME;<br /> const double DEFAULT_PLAY_BUFFER_TIME;<br /> };</p> </td> 
   <td><p>interface BufferControlParameters<br /> {<br /> attribuut double initialBufferTime;<br /> kenmerk double playBufferTime;<br /> <br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### TextFormat {#textformat}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API's</th> 
   <th>1.3 API's</th> 
  </tr> 
  <tr> 
   <td>Geen wijziging voor 2.0</td> 
   <td><p>interface TextFormat<br /> {<br /> // Kleurconst<br /> zonder teken short COLOR_DEFAULT = 0 ;<br /> const unsigned short COLOR_BLACK = 1;<br /> const unsigned short COLOR_GRAY = 2;<br /> const unsigned short COLOR_WHITE = 3;<br /> const unsigned short COLOR_BRIGHT_WHITE = 4;<br /> const unsigned short COLOR_DARK_RED = 5;<br /> const unsigned short COLOR_RED = 6;<br /> const unsigned short COLOR_BRIGHT_RED = 7;<br /> const unsigned short COLOR_DARK_GREEN = 8;<br /> const unsigned short COLOR_GREEN = 9;<br /> const unsigned short COLOR_BRIGHT_GREEN = 10 ;<br /> const unsigned short COLOR_DARK_BLUE = 11;<br /> const unsigned short COLOR_BLUE = 12;<br /> const unsigned short COLOR_BRIGHT_BLUE = 13;<br /> const unsigned short COLOR_DARK_YELLOW = 14;<br /> const unsigned short COLOR_YELLOW = 15;<br /> const unsigned short COLOR_BRIGHT_YELLOW = 16;<br /> const unsigned short COLOR_DARK_MAGENTA = 17;<br /> const unsigned short COLOR_MAGENTA = 18;<br /> const unsigned short COLOR_BRIGHT_MAGENTA = 19;<br /> const unsigned short COLOR_DARK_CYAN = 20 ;<br /> const unsigned short COLOR_CYAN = 21;<br /> const unsigned short COLOR_BRIGHT_CYAN = 22 ;<br /> <br /> readOnly-kenmerk unsigned short fontColor;<br /> kenmerk readOnly, kenmerk unsigned short backgroundColor;<br /> readOnly, kenmerk unsigned short fillColor;<br /> kenmerk readOnly, kenmerk zonder teken short edgeColor;<br /> <br /> // Size<br /> const unsigned short SIZE_DEFAULT = 0;<br /> const unsigned short SIZE_SMALL = 1;<br /> const unsigned short SIZE_MEDIUM = 2;<br /> const unsigned short SIZE_LARGE = 3;<br /> <br /> kenmerk read-only, korte grootte zonder teken;<br /> <br /> // FontEdge<br /> const unsigned short FONT_EDGE_DEFAULT = 0;<br /> const unsigned short FONT_EDGE_NONE = 1;<br /> const unsigned short FONT_EDGE_RAISED = 2;<br /> const unsigned short FONT_EDGE_DEPRESSED = 3;<br /> const unsigned short FONT_EDGE_UNIFORM = 4;<br /> const unsigned short FONT_EDGE_DROP_SHADOW_LEFT = 5;<br /> const unsigned short FONT_EDGE_DROP_SHADOW_RIGHT = 6;<br /> kenmerk readOnly, kenmerk unsigned short fontEdge;<br /> <br /> // Font<br /> const unsigned short FONT_DEFAULT = 0;<br /> const unsigned short FONT_MONOSPACED_WITH_SERIFS = 1;<br /> const unsigned short FONT_PROPORTIONAL_WITH_SERIFS = 2;<br /> const unsigned short FONT_MONSPACED_WITHOUT_SERIFS = 3;<br /> const unsigned short FONT_CASUAL = 4;<br /> const unsigned short FONT_CURSIVE = 5;<br /> const unsigned short FONT_SMALL_CAPITALS = 6;<br /> kenmerk read-only, niet-ondertekend kort lettertype;<br /> kenmerk Alleen-lezen, kenmerk unsigned short fontOpacity;<br /> kenmerk readonly, kenmerk unsigned short backgroundOpacity;<br /> readOnly, kenmerk unsigned short fillOpacity;<br /> read-only attribuut unsigned short DEFAULT_OPACITY;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### MediaPlayerItemLoader {#mediaplayeritemloader}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API's</th> 
   <th>1.3 API's</th> 
  </tr> 
  <tr> 
   <td><p>interface MediaPlayerItemLoader:<br /> {<br /> void load(MediaResource-bron, lange resourceId,<br /> ItemLoaderListener-listener, <br /> MediaPlayerItemConfig-config);<br /> void cancel();<br /> readOnly, kenmerk MediaPlayerItem currentItem;<br /> };</p> </td> 
   <td>Nieuw voor 2.0</td> 
  </tr> 
  <tr> 
   <td><p>interface ItemLoaderListener<br /> {<br /> //onLoadCompleteCallbackFunc(MediaPlayerItem)<br /> var onLoadCompleteCallbackFunc;<br /> //onErrorCallbackFunc(PSDKErrorCode)<br /> var onErrorCallbackFunc;<br /> }</p> </td> 
   <td>Nieuw voor 2.0</td> 
  </tr> 
 </tbody> 
</table>

## Wijzigingen in API-element voor mediakenmerken voor 2.0 {#media-characteristics-api-element-changes-for}

In deze tabellen worden de mediakenmerken-API-elementen voor de C++-TVSDK vergeleken tussen versies 1.3 en 2.0.

Tabellen in dit onderwerp:

* MediaPlayerItem
* Track, AudioTrack, ClosedCaptionsTrack
* Profiel
* DRMMetadataInfo

### MediaPlayerItem {#mediaplayeritem}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API's</th> 
   <th>1.3 API's</th> 
  </tr> 
  <tr> 
   <td><p>interface MediaPlayerItem {<br /> readonly attribute MediaResource resource;<br /> kenmerk read-only long resourceId;<br /> read-only attribute boolean live;<br /> <br /> alleen-lezen kenmerk boolean hasAlternateAudio;<br /> kenmerk readonly AudioTrackList audioTracks;<br /> kenmerk Alleen-lezen: AudioTrack selectedAudioTrack;<br /> void selectAudioTrack(AudioTrack); <br /> <br /> alleen-lezen kenmerk boolean hasClosedCaptions;<br /> kenmerk readonly; ClosedCaptionsTrackList closedCaptionsTracks;<br /> kenmerk readonly; ClosedCaptionsTrack selectedClosedCaptionsTrack;<br /> void selectClosedCaptionsTrack(<br /> ClosedCaptionsTrack-track); <br /> <br /> alleen-lezen kenmerk boolean hasTimedMetadata;<br /> kenmerk readonly, TimedMetadataList timedMetadata;<br /> read-only attribuut boolean dynamic;<br /> <br /> readonly attribute boolean isProtected;<br /> readOnly-kenmerk DRMMetadataInfoList drmMetadataInfos;<br /> alleen-lezen kenmerkprofielen ProfileList;<br /> alleen-lezen kenmerkprofiel selectedProfile;<br /> <br /> readOnly, kenmerk booleaanse trucPlaySupported;<br /> Alleen-lezen kenmerk FloatArray availablePlaybackRates;<br /> kenmerk Alleen-lezen float selectedPlaybackRate;<br /> <br /> <br /> kenmerk readOnly MediaPlayer;<br /> kenmerk readonly MediaPlayerItemConfig config;<br /> };</p> </td> 
   <td><p>interface MediaPlayerItem {<br /> readonly attribute MediaResource resource;<br /> kenmerk read-only long resourceId;<br /> read-only attribute boolean live;<br /> <br /> alleen-lezen kenmerk boolean hasAlternateAudio;<br /> kenmerk readonly AudioTrackList audioTracks;<br /> kenmerk AudioTrack selectedAudioTrack;<br /> <br /> <br /> alleen-lezen kenmerk boolean hasClosedCaptions;<br /> readOnly-kenmerk ClosedCaptionsTrackList ccTracks;<br /> kenmerk ClosedCaptionsTrack selectedCCTrack;<br /> <br /> <br /> <br /> alleen-lezen kenmerk boolean hasTimedMetadata;<br /> kenmerk readonly, TimedMetadataList timedMetadata;<br /> read-only attribuut boolean dynamic;<br /> <br /> readonly attribute boolean isProtected;<br /> readOnly-kenmerk DRMMetadataInfoList drmMetadataInfos;<br /> alleen-lezen kenmerkprofielen ProfileList;<br /> <br /> <br /> readOnly, kenmerk booleaanse trucPlaySupported;<br /> readOnly-kenmerk Int32Array availablePlaybackRates;<br /> <br /> alleen-lezen kenmerk StringList enTags;<br /> <br /> kenmerk readOnly MediaPlayer;<br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### Track / AudioTrack / ClosedCaptionsTrack {#track-audiotrack-closedcaptionstrack}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API's</th> 
   <th>1.3 API's</th> 
  </tr> 
  <tr> 
   <td><p>interface Track<br /> {<br /> readonly attribute DomString name;<br /> kenmerk readonly, DomString-taal;<br /> Booleaanse standaardwaarde, kenmerk readonly;<br /> alleen-lezen kenmerk boolean autoSelect;<br /> }; </p> </td> 
   <td>Nieuw voor 2.0</td> 
  </tr> 
  <tr> 
   <td><p>interface AudioTrack: Track<br /> {<br /> readonly attribute DomString name; //FromTrack<br /> readonly attribute DomString language;//FromTrack<br /> readonly attribute boolean default; // Van track<br /> alleen-lezen kenmerk boolean autoSelect;//FromTrack<br /> alleen-lezen kenmerk <br /> unsigned int pid;<br /> };</p> </td> 
   <td><p>interface AudioTrack<br /> {<br /> readonly attribute DomString name;<br /> kenmerk readonly, DomString-taal; <br /> Booleaanse standaardwaarde, kenmerk readonly;<br /> alleen-lezen kenmerk boolean autoSelect;<br /> read-only attribuut boolean geforceerd;<br /> <br /> };</p> </td> 
  </tr> 
  <tr> 
   <td>Geen wijziging voor 2.0</td> 
   <td><p>interface AudioTrackList<br /> {<br /> kenmerk read-only lengte zonder teken;<br /> getter AudioTrack (unsigned long index);<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface ClosedCaptionsTrack: Track<br /> {<br /> readonly attribute DomString name; //FromTrack<br /> readonly attribute DomString language;//FromTrack<br /> readonly attribute boolean default; // FromTrack<br /> readonly attribute boolean autoSelect;//FromTrack<br /> <br /> const <br /> unsigned short SERVICE_608_CAPTIONS = 0;<br /> const unsigned short SERVICE_708_CAPTIONS = 1;<br /> const unsigned short SERVICE_WEB_VTT_CAPTIONS = 2;<br /> readOnly, kenmerk unsigned short serviceType;<br /> read-only attribuut boolean geforceerd;<br /> };</p> </td> 
   <td><p>interface ClosedCaptionsTrack<br /> {<br /> readonly attribute DomString name;<br /> kenmerk readonly, DomString-taal;<br /> Booleaanse standaardwaarde, kenmerk readonly;<br /> <br /> <br /> alleen-lezen kenmerk boolean actief;<br /> <br /> <br /> <br /> <br /> <br /> };</p> </td> 
  </tr> 
  <tr> 
   <td>Geen wijziging voor 2.0</td> 
   <td><p>interface ClosedCaptionsTrackList<br /> {<br /> alleen-lezen kenmerk lange lengte zonder teken;<br /> getter ClosedCaptionsTrack(unsigned long index);<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### Profiel {#profile}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API's</th> 
   <th>1.3 API's</th> 
  </tr> 
  <tr> 
   <td>Profiel: Geen wijziging voor 2.0</td> 
   <td><p>interfaceprofiel<br /> {<br /> readonly attribute unsigned int width;<br /> kenmerk readonly, hoogte niet-ondertekende int;<br /> kenmerk readonly, kenmerk unsigned int bitRate;<br /> }; </p> </td> 
  </tr> 
  <tr> 
   <td>Profiellijst: Geen wijziging voor 2.0</td> 
   <td><p>interface ProfileList<br /> {<br /> readonly attributen unsigned long length;<br /> getter profiel (lange index zonder teken);<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMMetadataInfo {#drmmetadatainfo}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API's</th> 
   <th>1.3 API's</th> 
  </tr> 
  <tr> 
   <td><strong>DRMMetadataInfo</strong>: Geen wijziging voor 2.0</td> 
   <td><p>interface DRMMetadataInfo<br /> { <br /> readonly attributen DRMMetadata metadata;<br /> kenmerk readOnly lang prefetchTimestamp;<br /> readonly attribuut TimeRange timeRange;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>DRMMetadataInfoList</strong>: Geen wijziging voor 2.0</td> 
   <td><p>interface DRMMetadataInfoList<br /> {<br /> readonly attribuut unsigned long length;<br /> getter DRMMetadataInfo(unsigned long index);<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

## C++-fouten toewijzen aan uitzonderingen in verschillende talen {#mapping-c-errors-to-exceptions-in-different-languages}

U kunt C++ foutencodes aan uitzonderingen in verschillende talen in kaart brengen.

C++ PSDK heeft &quot;geen werpen&quot;beleid voor zijn APIs. De meeste API-methoden retourneren een PSDKErrorCode-waarde om aan te geven of de methode met succes is uitgevoerd. Asynchrone fouten worden via de foutgebeurtenissen op de hoogte gebracht.

De ActionScript en JAVA PSDK hebben een ander beleid. De meeste fouten genereren een ArgumentError of IllegalStateException om aan te geven dat het synchrone gedeelte van de methode niet kon worden uitgevoerd. Deze uitzonderingen worden niet afgevangen, en de toepassingscode is verantwoordelijk voor de behandeling van de uitzonderingen. Zij dragen gewoonlijk nuttige informatie over waarom de methodevraag ontbrak. Als de opdracht prepareToPlay bijvoorbeeld in een ongeldige status wordt aangeroepen, wordt de volgende uitzondering gegenereerd:

```shell
throw new IllegalStateException("Invalid player state. prepareToPlay method 
must be called only once after replaceCurrentItem or replaceCurrentResource method.");
```

De ActionScript/JAVA genereert ook uitzonderingen van constructors om aan te geven dat een intern object onjuist is gemaakt. Deze uitzonderingen worden intern behandeld, en zij worden niet verspreid aan de toepassing. De uitzonderingen worden opgenomen in een waarschuwingsbericht dat naar de toepassing wordt verzonden

Als er bijvoorbeeld geen geldig mediabestand is gevonden voor het ontvangen advertentie-antwoord, kan er geen geldig ad-asset-object of advertentie worden gemaakt. Als gevolg hiervan wordt geen advertentie op de tijdlijn geplaatst en wordt een melding NotificationEvent.OperationFailed verzonden.

Fout- of waarschuwingscodes die asynchroon zijn ontvangen van de Adobe Video Engine (AVE) worden als normale gebeurtenissen naar de toepassing verzonden. De meldingsgebeurtenis bevat alle ontvangen foutcodes en eventuele aanvullende metagegevens, zoals de URL, de bron-id, de handle, enzovoort. Als de fout ernstig is en het afspelen van de huidige media niet kan worden voortgezet, gaat MediaPlayer over naar de status ERROR en de callback onStatusChanged- of MediaPlayerStatusChanged.STATUS_CHANGED-gebeurtenis wordt verzonden. Als het afspelen kan worden voortgezet, wordt een normale meldingsgebeurtenis verzonden.

<table> 
 <tbody> 
  <tr> 
   <th>C++-fout (PSDKError-code)</th> 
   <th> </th> 
   <th>Java</th> 
   <th>ActionScript</th> 
   <th>JavaScript</th> 
  </tr> 
  <tr> 
   <td>kECInvalidArgument</td> 
   <td> </td> 
   <td>IllegalArgumentException</td> 
   <td>ArgumentError</td> 
   <td>Uitzondering met code = 1, description = "INVALID_ARGUMENT" en additionalInfo= &lt;as passed by method which throw this exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECNullPointer</td> 
   <td> </td> 
   <td>IllegalArgumentException</td> 
   <td>ArgumentError</td> 
   <td>Uitzondering met code = 2, description = "GENERIC_ERROR" en additionalInfo= &lt;as passed by method which throw this exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECIllegalState</td> 
   <td> </td> 
   <td>IllegalStateException</td> 
   <td>IllegalStateException</td> 
   <td>Uitzondering met code = 3, description = "ILLEGAL_STATE" en additionalInfo= &lt;as passed by method which throw this exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECInterfaceNotFound</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Uitzondering met code = 4, description = "GENERIC_ERROR" en additionalInfo= &lt;as passed by method which throw this exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECCreationFailed</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Uitzondering met code = 5, description = "CREATION_FAILED" en additionalInfo= &lt;as passed by method which throw this exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECUnsupportedOperation</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Uitzondering met code = 5, description = "CREATION_FAILED" en additionalInfo= &lt;as passed by method which throw this exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECDataNotAvailable</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Uitzondering met code = 7, description = "DATA_NOT_AVAILABLE" en additionalInfo= &lt;as passed by method which throw this exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECSeekError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Uitzondering met code = 8, description = "SEEK_ERROR" en additionalInfo= &lt;as passed by method which throw this exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECUnsupportedFeature</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Uitzondering met code = 9, description = "UNSUPPORTED_FEATURE" en additionalInfo= &lt;as passed by method which throw this exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECRangeError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Uitzondering met code = 10, description = "RANGE_ERROR" en additionalInfo= &lt;as passed by method which throw this exception</td> 
  </tr> 
  <tr> 
   <td>kECCodecNotSupported</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Uitzondering met code = 11, description = "CODEC_NOT_SUPPORTED" en additionalInfo= &lt;as passed by method which throw this exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECMediaError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Uitzondering met code = 12, description = "MEDIA_ERROR" en additionalInfo= &lt;as passed by method which throw this exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECNetworkError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Uitzondering met code = 13, description = "NETWORK_ERROR" en additionalInfo= &lt;as passed by method which throw this exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECGenericError</td> 
   <td> </td> 
   <td>MediaPlayerNotification.Error of MediaPlayerNotification.Warning</td> 
   <td>MediaError of NotificationEvent</td> 
   <td>Uitzondering met code = 14, description = "GENERIC_ERROR" en additionalInfo= &lt;as passed by method which throw this exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECInvalidSeekTime</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Uitzondering met code = 15, description = "INVALID_SEEK_TIME" en additionalInfo= &lt;as passed by method which throw this exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECAudioTrackError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Uitzondering met code = 16, description = "AUDIO_TRACK_ERROR" en additionalInfo= &lt;as passed by method which throw this exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECAAccessFromDifferent<p>ThreadError</p> </td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Uitzondering met code = 17, description = "GENERIC_ERROR" en additionalInfo= &lt;as passed by method which throw this exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECElementNotFound</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Uitzondering met code = 18, description = "GENERIC_ERROR" en additionalInfo= &lt;as passed by method which throw this exception</td> 
  </tr> 
  <tr> 
   <td>kECNotImplemented</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Uitzondering met code = 19, description = "GENERIC_ERROR" en additionalInfo= &lt;as passed by method which throw this exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECPlaybackOperationFailed</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Uitzondering met code = 200, description = "PLAYBACK_OPERATION_FAILED" en additionalInfo= &lt;as passed by method which throw this exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECNativeWarning</td> 
   <td> </td> 
   <td>MediaPlayerNotification.Warning</td> 
   <td>NotificationEvent</td> 
   <td>Uitzondering met code = 201, description = "NATIVE_WARNING" en additionalInfo= &lt;as passed by method which throw this exception</td> 
  </tr> 
  <tr> 
   <td>kECAdResolverFailed</td> 
   <td> </td> 
   <td>MediaPlayerNotification.Warning</td> 
   <td>-</td> 
   <td>Uitzondering met code = 202, description = "AD_RESOLVER_FAILED" en additionalInfo= &lt;as passed by method which throw this exception&gt;</td> 
  </tr> 
 </tbody> 
</table>

## Wijzigingen in het element Hulpprogramma en Help-API voor 2.0 {#utility-and-helper-api-element-changes-for}

In deze tabellen worden de elementen van de API van het hulpprogramma en de Help voor de JavaScript-TVSDK vergeleken tussen versie 1.3 en 2.0.

Tabellen in dit onderwerp:

* Versie
* TimeRange
* QOSProvider
* DeviceInformation
* LoadInfo
* Weergave
* Afspeelgegevens

### Versie {#version}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API's</th> 
   <th>1.3 API's</th> 
  </tr> 
  <tr> 
   <td><p>interface Version<br /> {<br /> readonly attribute DomString version;<br /> kenmerk readonly, beschrijving van DomString;<br /> kenmerk read-only long major;<br /> kenmerk readonly, lange ondergeschikte;<br /> kenmerk read-only, lange revisie;<br /> readonly, kenmerk long apiVersion;<br /> };</p> </td> 
   <td><p>interface Version<br /> {<br /> readonly attribute DomString version;<br /> kenmerk readonly, beschrijving van DomString;<br /> readOnly, kenmerk DomString major;<br /> readOnly, kenmerk DomString minor;<br /> kenmerk readonly, DomString-revisie;<br /> readonly attribute DomString apiVersion;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### TimeRange {#timerange}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API's</th> 
   <th>1.3 API's</th> 
  </tr> 
  <tr> 
   <td>Geen wijziging voor 2.0</td> 
   <td><p>interface TimeRange<br /> {<br /> readonly attributen unsigned long begin;<br /> kenmerk read-only, kenmerk unsigned long end;<br /> kenmerk readonly is kenmerk unsigned long duration;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### QOSProvider {#qosprovider}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API's</th> 
   <th>1.3 API's</th> 
  </tr> 
  <tr> 
   <td>Geen wijziging voor 2.0</td> 
   <td><p>interface QOSProvider<br /> {<br /> void attachMediaPlayer(MediaPlayer-speler);<br /> void detachMediaPlayer();<br /> <br /> alleen-lezen kenmerk DeviceInformation deviceInformation;<br /> alleen-lezen kenmerk PlaybackInformation playbackInformation;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DeviceInformation {#deviceinformation}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API's</th> 
   <th>1.3 API's</th> 
  </tr> 
  <tr> 
   <td><p>interface DeviceInformation<br /> {<br /> readonly attribute DomString os;<br /> <br /> <br /> <br /> kenmerk readonly, DomString-id;<br /> alleen-lezen kenmerk int densityDPI;<br /> kenmerk readonly int heightPixels;<br /> kenmerk readonly int widthPixels;<br /> alleen-lezen kenmerk boolean seekToKeyFrame;<br /> };</p> </td> 
   <td><p>interface DeviceInformation<br /> {<br /> readonly attribute DomString os;<br /> kenmerk readonly int sdk;<br /> alleen-lezen kenmerk DomString-model;<br /> kenmerk readonly, fabrikant van DomString;<br /> kenmerk readonly, DomString-id;<br /> alleen-lezen kenmerk int densityDPI;<br /> kenmerk readonly int heightPixels;<br /> kenmerk readonly int widthPixels;<br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### LoadInfo {#loadinfo}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API's</th> 
   <th>1.3 API's</th> 
  </tr> 
  <tr> 
   <td>Geen wijziging voor 2.0</td> 
   <td><p>interface LoadInfo<br /> {<br /> alleen-lezen kenmerk DomString url;<br /> alleen-lezen kenmerk int-grootte;<br /> kenmerk readonly, double downloadDuration;<br /> kenmerk readonly int periodIndex;<br /> kenmerk read-only double mediaDuration;<br /> kenmerk readonly, short TRACK_TYPE_FRAGMENT;<br /> kenmerk readonly, short TRACK_TYPE_TRACK;<br /> read-only kenmerk short TRACK_TYPE_MANIFEST;<br /> kenmerk Alleen-lezen, kort type;<br /> kenmerk readonly, DomString trackName;<br /> kenmerk readonly, DomString trackType;<br /> kenmerk readonly int trackIndex;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### Weergave {#view}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API's</th> 
   <th>1.3 API's</th> 
  </tr> 
  <tr> 
   <td>Geen wijziging voor 2.0</td> 
   <td><p>interface View<br /> {<br /> readonly attribute unsigned short x;<br /> kenmerk readonly zonder teken kort y;<br /> kenmerk readonly, kenmerk unsigned short width;<br /> kenmerk readonly, kenmerk unsigned short height;<br /> <br /> void setSize(unsigned short width, unsigned short height);<br /> void setPos(unsigned short x, unsigned short y);<br /> }</p> </td> 
  </tr> 
 </tbody> 
</table>

### Afspeelgegevens {#playbackinformation}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API's</th> 
   <th>1.3 API's</th> 
  </tr> 
  <tr> 
   <td><p>interface PlaybackInformation<br /> {<br /> readonly attribuut double timeToFirstByte;<br /> kenmerk readonly double timeToLoad;<br /> kenmerk readonly double timeToStart;<br /> kenmerk readonly double timeToFail;<br /> kenmerk readonly int totalSecondsPlayed;<br /> kenmerk readonly int totalSecondsSpent;<br /> kenmerk read-only double frameRate;<br /> readOnly, kenmerk int droppedFrameCount;<br /> readOnly-kenmerk int waargenomenBandwidth;<br /> kenmerk Alleen-lezen in bitsnelheid;<br /> kenmerk readonly double bufferTime;<br /> kenmerk readonly int bufferLength;<br /> readOnly, kenmerk int emptyBufferCount;<br /> kenmerk readonly; double bufferingTime;<br /> };</p> </td> 
   <td><p>interface PlaybackInformation<br /> {<br /> readonly attribuut double timeToFirstByte;<br /> kenmerk readonly double timeToLoad;<br /> kenmerk readonly double timeToStart;<br /> kenmerk readonly double timeToFail;<br /> kenmerk readonly int totalSecondsPlayed;<br /> kenmerk readonly int totalSecondsSpent;<br /> kenmerk read-only double frameRate;<br /> readOnly, kenmerk int droppedFrameCount;<br /> <br /> kenmerk Alleen-lezen in bitsnelheid;<br /> kenmerk readonly double bufferTime;<br /> kenmerk readonly int bufferLength;<br /> readOnly, kenmerk int emptyBufferCount;<br /> kenmerk readonly; double bufferingTime;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

## Nuttige bronnen {#helpful-resources}

* Zie de volledige Help-documentatie op de pagina Learn &amp; Support [van](https://helpx.adobe.com/support/primetime.html) Adobe Primetime.
