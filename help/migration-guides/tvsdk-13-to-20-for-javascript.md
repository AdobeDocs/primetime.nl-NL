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


# TVSDK-conversie - 1,3 naar 2,0 voor JavaScript {#tvsdk-conversion-to-for-javascript}

Veel methode-handtekeningen en API-elementnamen zijn gewijzigd voor 2.0. Bekijk deze tabellen om alle details van de API-wijziging te bekijken.

## Callbackfuncties implementeren in JavaScript {#implement-callback-functions-in-javascript}

De commentaren in methodedocumentatie stellen de handtekening voor callbacks voor die u moet uitvoeren.

Voor JavaScript is de API-syntaxis gebaseerd op de web-id. Voor een interface van TVSDK, worden de methodenamen genoemd *methodName* (). Voor methodes die door uw toepassing moeten worden uitgevoerd, wordt een lees-schrijfattribuut genoemd *methodName* CallbackFunc toegevoegd aan de interface en uw toepassing zou het moeten plaatsen om aan een functie te richten die de methode uitvoert. Bijvoorbeeld:

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
   <td><p> <strong>TimedMetadata</strong>: interface TimedMetadata {<br /> const unsigned short METADATA_TYPE_TAG = 0;  <br /> const unsigned short METADATA_TYPE_ID3 = 1;  <br /> kenmerk readonly, kenmerk unsigned short type;  <br /> kenmerk readOnly lange tijd;kenmerk <br /> readonly DomString id;kenmerk <br /> readonly DomString name;kenmerk <br /> readonly DomString content;  <br /> readOnly-metagegevens kenmerk Object;<br /> }; </p> </td> 
   <td><p>interface TimedMetadata {<br /> const unsigned short METADATA_TYPE_TAG = 0 ;<br /> const unsigned short METADATA_TYPE_ID3 = 1 ;<br /> readonly attribute unsigned short metadataType;<br /> readonly attribute long time;<br /> readonly attribute long id;<br /> readonly attribute Dom name;<br /> <br /> read-only attributenObjectemetagegevens;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>TimedMetadataList</strong>: (Geen wijziging voor 2.0)</td> 
   <td><p>interface TimedMetadataList {<br /> kenmerk read-only lange lengte zonder teken;<br /> getter TimedMetadata(unsigned long index);<br /> };</p> </td> 
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
   <td><p>Interface AdSignalingMode { <br /> const unsigned short MODE_DEFAULT, <br /> const unsigned short MODE_MANIFEST_CUES, <br /> const unsigned short MODE_SERVER_MAP, <br /> const unsigned short MODE_CUSTOM_RANGES <br /> };</p> </td> 
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
   <td><p>Interface AdvertisingMetadata { <br /> attribuut AdSignalingMode wijze; <br />-kenmerk AdBreakWatchedPolicy enBreakAsWatched; <br /> attribuut boolean livePreroll; <br /> attribute boolean delayAdLoading; <br /> };</p> </td> 
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
   <td><p>Interface CustomRangeMetadata { <br /> const unsigned short TYPE_MARK_RANGE; <br /> const unsigned short TYPE_DELETE_RANGE; <br /> const unsigned short TYPE_REPLACE_RANGE; <br />-kenmerk korte type zonder teken; <br /> attribuut boolean adjustSeekPosition; <br />-kenmerk TimeRangeList timeRangeList; <br /> };</p> </td> 
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
   <td><p>interface ReplaceTimeRange { <br /> attributen unsigned long begin; <br /> kenmerk Alleen-lezen, lange-eindzijde zonder teken; <br /> kenmerk unsigned long duration; <br />-kenmerk unsigned long replaceDuration; <br /> };</p> </td> 
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
   <td><p>Interface Placement { <br /> const unsigned short TYPE_MID_ROLL; <br /> const unsigned short TYPE_PRE_ROLL; <br /> const unsigned short TYPE_POST_ROLL; <br /> const unsigned short TYPE_SERVER_MAP; <br /> const unsigned short TYPE_CUSTOM_RANGE;<br /> readonly attribute unsigned short type; <br /> kenmerk read-only lange tijd; <br /> kenmerk read-only lange duration; <br /> const unsigned short MODE_DEFAULT; <br /> const unsigned short MODE_INSERT; <br /> const unsigned short MODE_REPLACE; <br /> const unsigned short MODE_DELETE; <br /> const unsigned short MODE_MARK; <br /> const unsigned short MODE_FREE_REPLACE; <br /> kenmerk Alleen-lezen, korte modus zonder teken; <br /> readonly attribute TimeRange range; <br /> };</p> </td> 
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
   <td><p>interface Opportunity { <br /> readonly attribuut DomString id; <br /> Alleen-lezen kenmerkplaatsing; <br /> alleen-lezen kenmerkobjectinstellingen; <br /> kenmerk Alleen-lezen Object customParameters; <br /> }; </p> </td> 
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
   <td><p>interface Reservation { <br /> readonly attribuut TimeRange waaier; <br /> kenmerk read-only eigenschap long hold; <br /> }; </p> </td> 
   <td> (Nieuw voor 2.0)</td> 
  </tr> 
 </tbody> 
</table>

### Tijdlijn / Tijdlijnitem / Tijdlijnmarkeerteken {#timeline-timelineitem-timelinemarker}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p><strong>Tijdlijn</strong>: interfacetijdlijn  <br /> { alleen-lezen kenmerk TimelineMarkerList tijdlijnmarkeertekens;  <br /> alleen-lezen kenmerk TimelineItemList timelineItems;  <br /> double convertToLocalTime( dubbele tijd);  <br /> double convertToVirtualTime( dubbele tijd);  <br /> };</p> </td> 
   <td><p>interface Timeline {<br /> readonly attribute TimelineMarkerList timelineMarkers;<br /> <br /> <br /> <br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p> <strong>TimelineItem</strong>: interface TimelineItem:<br /> TimelineMarker {kenmerk <br /> read-only long id;  <br /> kenmerk readonly, TimeRange virtualRange;  <br /> kenmerk readonly TimeRange localRange;  <br /> read-only, kenmerk booleaans gecontroleerd;  <br /> read-only, kenmerk boolean temporary;  <br /> }; </p> </td> 
   <td>(Nieuw voor 2.0)</td> 
  </tr> 
  <tr> 
   <td><strong>Tijdlijnmarkeerteken</strong>: (Geen wijziging voor 2.0)</td> 
   <td><p>interface TimelineMarker {<br /> read-only attributen double time;<br /> readonly attributen double duration;<br /> };</p> </td> 
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
   <td><p>interface AdBreak {<br /> <br /> <br /> <br /> kenmerk read-only double duration;<br /> kenmerk readonly ADD;<br /> <br /> <br /> kenmerk AdInsertionType insertType;<br /> }; </p> </td> 
   <td><p>interface AdBreak {<br /> read-only attribuut double time;<br /> readonly attribute double replaceDuration;<br /> <br /> readonly attribute double duration;<br /> readonly attribute AdList adList;<br /> <br /> readonly attribute DomString data;<br /> <br /> }; </p> </td> 
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
   <td><p> <strong>Advertentie</strong>: interface Ad {<br /> readonly attribute AdAsset primaryAsset;<br /> readonly attribute AdAssetList companionAssets;<br /> <br /> readonly attribute double duration;<br /> readonly attribute DomString id;<br /> const unsigned short ADTYPE_LINEAR = 0;<br /> const unsigned short ADTYPE_NONLINEAR = 1;<br /> <br /> readonly attribute unsigned short adType;<br /> readonly attribuut AdInsertionType adInsertionType;  <br /> <br /> kenmerk readonly boolean klikbaar;  <br /> alleen-lezen kenmerk boolean isCustomAdMarker;<br /> }; </p> </td> 
   <td><p>interface Ad {<br /> read-only attribute AdAsset primaryAsset;<br /> readonly attribute AdAssetList companionAssets;<br /> <br /> readonly attribute double duration;<br /> readonly attribute DomString id;<br /> const unsigned short ADTYPE_LINEAR = 0;<br /> const unsigned short ADTYPE_TYPE_TYPE NONLINEAR = 1 ;<br /> <br /> kenmerk read-only type unsigned short type;<br /> kenmerk read-only AdInsertionType insertType; <br /> Alleen-lezen kenmerkobjecttracering;<br /> <br /> <br /> }; </p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdAsset</strong>: (Geen wijziging voor 2.0)</td> 
   <td><p>interface AdAsset {<br /> read-only attribuut DomString id;<br /> readonly attribuut double duration;<br /> readonly attribute MediaResource middel;<br /> readonly attribute AdClick enClick;<br /> readonly attribuut Object metadata;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdClick</strong>: (Geen wijziging voor 2.0)</td> 
   <td><p>interface AdClick {<br /> read-only attributen DomString id;<br /> readonly attributen DomString titel;<br /> read-only attributen DomString url;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>Advertentielijst</strong>: (Geen wijziging voor 2.0)</td> 
   <td><p>interface AdList {<br /> read-only attributen unsigned long length;<br /> getter Ad(unsigned long index);<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdAssetList</strong>: (Geen wijziging voor 2.0)</td> 
   <td><p>interface AdAssetList {<br /> kenmerk read-only lange lengte zonder teken;<br /> getter AdAsset(unsigned long index);<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p><strong>AdBannerAsset</strong>: interface AdBannerAsset: AdAsset<br /> {<br /> readonly attribute int width;<br /> readonly attribute int height;<br /> readonly attribute DomString staticUrl;<br /> readonly attribute DomString height;<br /> readonly attribute DomString width;<br /> };</p> </td> 
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
   <td><p> <strong>AdBreakTimelineItem</strong>: interface AdBreakTimelineItem: TimelineItem {  <br /> readonly attribute AdBreak adBreak;  <br /> alleen-lezen kenmerk AdTimelineItemList-items;  <br /> }; </p> </td> 
   <td> (Nieuw voor 2.0)</td> 
  </tr> 
  <tr> 
   <td><p><strong>AdTimelineItem</strong>: interface AdTimelineItem : TimelineItem {  <br /> readonly attribute AdBreak adBreak;  <br /> alleen-lezen kenmerk Advertentie;  <br /> }; </p> </td> 
   <td> (Nieuw voor 2.0)</td> 
  </tr> 
  <tr> 
   <td><p><strong>AdBreakTimelineItemList</strong>: interface AdBreakTimelineItemList {  <br /> readonly attribuut unsigned long length;  <br /> getter AdBreakTimelineItem (index zonder teken);  <br /> };</p> </td> 
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
   <td><p>interface AdBreakPolicy {<br /> readonly attribute short AD_BREAK_POLICY_SKIP;<br /> readonly attribute short AD_BREAK_POLICY_PLAY;<br /> readonly attribute short AD_BREAK_POLICY_REMOVE;<br /> readonly attribute short AD_BREAK_POLICY_REMOVE_AFTER LAY;<br /> };</p> </td> 
   <td><p> interface AdPolicyConstants {<br /> readonly attribute short AD_BREAK_POLICY_SKIP;<br /> readonly attribute short AD_BREAK_POLICY_PLAY;<br /> readonly attribute short AD_BREAK_POLICY_REMOVE;<br /> readonly attribute short AD_BREAK_POLICY_REMOVE_AFTER AFSPELEN;}<br /> ...</p> </td> 
  </tr> 
  <tr> 
   <td><p> interface AdBreakWatchedPolicy {<br /> readonly attribute short AD_BREAK_AS_WATCHED_ON_BEGIN;<br /> readonly attribute short AD_BREAK_AS_WATCHED_ON_END;<br /> readonly attribute short AD_BREAK_AS_WATCHED_NEVER;<br /> }; </p> </td> 
   <td><p> ...<br /> alleen-lezen kenmerk short AD_BREAK_AS_WATCHED_ON_BEGIN;<br /> alleen-lezen kenmerk short AD_BREAK_AS_WATCHED_ON_END;<br /> alleen-lezen kenmerk short AD_BREAK_AS_WATCHED_NEVER;<br />..</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicy {<br /> alleen-lezen kenmerk short AD_POLICY_PLAY;<br /> alleen-lezen kenmerk short AD_POLICY_PLAY_FROM_AD_BEGIN;<br /> alleen-lezen kenmerk short AD_POLICY_PLAY_FROM_AD_BREAK_BEGIN; read-only attribuut short AD_POLICY_SKIP_TO_NEXT_AD_IN_BREAK;<br /> <br /> readonly attribute short AD_POLICY_SKIP_AD_BREAK;<br /> };</p> </td> 
   <td><p> ... <br /> alleen-lezen kenmerk short AD_POLICY_PLAY;<br /> alleen-lezen kenmerk short AD_POLICY_PLAY_FROM_AD_BEGIN;<br /> alleen-lezen kenmerk short AD_POLICY_PLAY_FROM_AD_BREAK_BEGIN;<br /> alleen-lezen kenmerk short AD_POLICY_SKIP_TO_NEXT_AD_IN_ABREIN K;<br /> alleen-lezen kenmerk short AD_POLICY_SKIP_AD_BREAK;<br /> ...</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicyMode {<br /> alleen-lezen kenmerk short AD_POLICY_MODE_PLAY;<br /> alleen-lezen kenmerk short AD_POLICY_MODE_SEEK;<br /> alleen-lezen kenmerk short AD_POLICY_MODE_TRICKPLAY;<br /> };</p> </td> 
   <td><p> ...<br /> {readonly attribute short AD_POLICY_MODE_PLAY;<br /> readonly attribute short AD_POLICY_MODE_SEEK;<br /> readonly attribute short AD_POLICY_MODE_TRICKPLAY;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicyInfo {<br /> alleen-lezen kenmerk AdBreakTimelineItemList <br /> adBreakTimelineItems;<br /> alleen-lezen kenmerk AdTimelineItem adTimelineItem;<br /> alleen-lezen kenmerk dubbel-currentTime;<br /> alleen-lezen kenmerk dubbel tarief; <br /> kenmerk short mode alleen-lezen; //AdPolicyMode<br /> };<br /></p> </td> 
   <td><p>interface AdPolicyInfo {<br /> alleen-lezen kenmerk AdBreakPlacementList <br /> adBreakPlacements;<br /> alleen-lezen kenmerk Ad;<br /> alleen-lezen kenmerk double currentTime;<br /> alleen-lezen kenmerk double seekToTime;<br /> alleen-lezen kenmerk double rate;<br /> alleen-kenmerk korte modus; //AdPolicyMode<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicySelector {<br /> /**<br /> * AdbreakPolicy selectPolicyForAdBreak(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectPolicyForAdBreakCallbackFunc;<br /> /* 6/&gt; * AdBreakTimelineItemList selectAdBreaksToPlay(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> kenmerkobject selectAdBreaksToPlayCallbackFunc;<br /> /**<br /> * Ad Policy selectPolicyForSeekIntoAd(AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectPolicyForSeekIntoAdCallbackFunc; <br /> /**<br /> * AdBreakWatchedPolicy selectWatchedPolicyForAdBreak(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectWatchedPolicyForAdBreak akCallbackFunc;<br /> };<br /></p> </td> 
   <td><p>interface AdPolicySelector {<br /> /**<br /> * AdbreakPolicy selectPolicyForAdBreak(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectPolicyForAdBreakFuncCallback;<br /> /* 6/&gt; * AdBreakPlacementList selectAdBreaksToPlay(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectAdBreaksToPlayCallback;<br /> /**<br /> * AdPolicy PolicyForSeekIntoAd(AdPolicyInfo adPolicyInfo);<br /> */<br /> kenmerk Object selectPolicyForSeekIntoAdCallback; <br /> /**<br /> * AdBreakAsWatched selectWatchedPolicyForAdBreak(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> kenmerk Object selectWatchedPolicyForAdBreak akCallback;<br /> };<br /></p> </td> 
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
   <td><p>interface TimelineOperation { <br /> Alleen-lezen kenmerkplaatsing ; <br /> };</p> </td> 
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
   <td><p>interface AdBreakPlacement : TimelineOperation {<br /> read-only attribute AdBreak adBreak;<br /> read-only attribute Placement placement; // Van TimelineOperation<br /> kenmerk read-only double time;<br /> kenmerk read-only double duration;<br /> };</p> </td> 
   <td><p>interface AdBreakPlacement {<br /> read-only attribuut AdBreak adBreak;<br /> read-only kenmerkplaatsing;<br /> readonly attribuut double time;<br /> readonly attribuut double duration;<br /> };</p> </td> 
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
   <td><p>interface AuditudeSettings: AdvertisingMetadata { <br />-kenmerk DomString zoneId; <br /> kenmerk DomString mediaId; <br /> kenmerk DomString defaultMediaId; <br /> attribuut DomString domain; <br /> kenmerk Object targettingInfo; <br /> kenmerk Object customParameters; <br /> attribuut Boolean creativePackingEnabled ;<br /> attribuut Boolean showStaticBanners ;<br /> };</p> </td> 
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
   <td><p>interface MediaPlayerItemConfig {<br /> attributen ContentFactory en Factory;<br /> attributen StringList subscribeTags;<br /> <br /> attributen StringList enTags;<br /> <br /> <br /> &lt;a6/&gt; attributen AdSignalingMode en SignalingMode;<br /> attributen CustomRange Metadata customRangeMetadata;<br /> attribute NetworkConfiguration networkConfiguration Configuration;<br /> attribute AdvertisingMetadata advertenceMetadata;<br /> attribute Boolean useHardwareDecoder;<br /> };</p> </td> 
   <td><p>interface MediaPlayerConfig {<br /> <br /> <br /> <br /> attributen StringList adTags;<br /> attributen StringList subscribedTags;<br /> attributen MediaPlayerClientFactory clientFactory;<br /> <br /> <br /> <br /> <br /> a11/&gt; };<br /></p> </td> 
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
   <td><p>interface ContentFactory {<br /> /*<br /> * AdPolicySelector retrieveAdPolicySelector(<br /> * MediaPlayerItem item);<br /> */<br /> attributen Object retrieveAdPolicySelectorCallbackFunc;<br /> };</p> </td> 
   <td><p>interface MediaPlayerClientFactory {<br /> /*<br /> * AdPolicySelector retrieveAdPolicySelector(<br /> * MediaPlayerItem item);<br /> */<br /> attributen Object retrieveAdPolicySelectorFunc;<br /> };</p> </td> 
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
   <td><p>interface NetworkConfiguration<br /> {<br /> attribuut boolean forceNativeNetworking;<br /> attribuut boolean useRedirectedUrl;<br /> attribuut Object cookieHeader;<br /> attribuut boolean readSetCookieHeader;<br /> attribuut int masterUpdateInterval; <br /> attribuut boolean useCookieHeaderForAllRequests;<br /> attribuut int readLimit;<br /> };</p> </td> 
   <td>In 1.3 werd een deel van deze functionaliteit geleverd door MetadataKeys</td> 
  </tr> 
 </tbody> 
</table>

## DRM API-elementwijzigingen voor 2.0 {#drm-api-element-changes-for}

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

### DRM Workflowinitialisatie {#drm-workflow-initialization}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API's</th> 
   <th>1.3 API's</th> 
  </tr> 
  <tr> 
   <td>De toepassing moet AdobePSDK.initisDRMWorkflow aanroepen om de DRM-workflow te starten. Zonder deze oproep worden DRM-video's niet afgespeeld.<p>interface AdobePSDK<br /> {<br /> void initiDRMWorkFlow(<br /> DomString appStoratePath, <br /> DomString publisherId, <br /> DomString appId, <br /> DomString appVersion, <br /> boolean privacyModeOn); a7/&gt; };<br /></p> </td> 
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
| Geen wijziging voor 2.0. | enum DRMAuthenticationMethod <br>{<br> const unsigned int UNKNOWN = 0;<br> const unsigned int ANONYMOUS = 1;<br> const unsigned int USERNAME_AND_PASSWORD = 2;<br> } |

### DRMMetadata {#drmmetadata}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API's</th> 
   <th>1.3 API's</th> 
  </tr> 
  <tr> 
   <td>Geen wijziging voor 2.0.</td> 
   <td><p>interface DRMMetadata<br /> {<br /> read-only attribuut DomString serverUrl;<br /> readonly attribuut DomString licenseId;<br /> readonly attribuut DRMPPolicyArray beleid; <br /> };</p> </td> 
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
   <td><p>interface DRMPlaybackTimeWindow {<br /> read-only attribuut int playbackPeriodInSeconds;<br /> readonly attribuut long playbackStartDate;<br /> readonly attribuut long playbackEndDate;<br /> };</p> </td> 
   <td><p>interface DRMPlaybackTimeWindow {<br /> kenmerk readonly int periodInSeconds;<br /> kenmerk readonly int startDate;<br /> kenmerk readonly int endDate;<br /> };</p> </td> 
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
   <td><p>interface DRMLicense {<br /> read-only attributen Uint8Array bytes;<br /> readonly attributen Date licenseStartDate;<br /> readonly attribuut Date licenseEndDate;<br /> readonly attribuut Date offlineStorageStartDate;<br /> readonly attribuut Date offlineStorageEndDate; <br /> kenmerk Alleen-lezen DomString serverUrl;<br /> kenmerk alleen-lezen DomString licenseID;<br /> kenmerk alleen-lezen DomString policyID;<br /> kenmerk alleen-lezen DRMPlaybackTimeWindow playbackTimeWindow;<br /> kenmerk kenmerk Alleen-lezen Object customProperties;<br /> }; </p> </td> 
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
   <td><p>interface DRMLicenseDomain {<br /> alleen-lezen kenmerk DomString authenticationDomain;<br /> alleen-lezen kenmerk DRMAuthenticationMethod authenticationMethod; <br /> kenmerk Alleen-lezen DomString serverUrl;<br /> };</p> </td> 
   <td><p>interface DRMLicenseDomain {<br /> read-only attribuut DomString authDomain;<br /> readonly attribuut DRMAuthenticationMethod authMethod; <br /> kenmerk Alleen-lezen DomString serverURL;<br /> };</p> </td> 
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
   <td><p>interface DRMPopolicy<br /> {<br /> readonly attribute DomString authenticationDomain;<br /> readonly attribute DRMAuthenticationMethod authenticationMethod;<br /> <br /> readonly attribute DomString displayName;<br /> readonly attribute DRMLicenseDomain licenseDomain;<br /> };</p> </td> 
   <td><p>interface DRMPopolicy<br /> {<br /> read-only attribuut DomString authDomain;<br /> readonly attribute DRMAuthenticationMethod authMethod;<br /> readonly attribute DomString dispName;<br /> readonly attribute DRMLicenseDomain licenseDomain;<br /> };</p> </td> 
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
   <td><p>interface DRMManager: EventTarget {<br /> void verwervingLicense(DRMMetadata metadata, <br /> DRMAcquireLicenseSettings setting, <br /> DRMAquireLicenseListener listener);<br /> voidPreviewLicense(DRMMetadata metadata, <br /> DRMAquireLicenseListener listener);<br /> void authenticate(DRMMetadata metadata, <br /> DomString url,<br /> DomString &amp;authenticationDomain, <br /> DomString user, <br /> DomString password, <br /> DRMAuthenticateListener listener);<br /> <br /> DRMM etadata createMetadataFromBytes(<br /> Uint8Array-array, DRMErrorListener-listener);<br /> void initialize(DRMOperationCompleteListener-listener);<br /> attribute long maxOperationTime;<br /> <br /> void Domain(<br /> DRMLicenseDomain licenseDomain, <br /> boolean forceRefresh, <br /> DRMOperationCompleteListener listener);<br /> void leaveLicenseDomain(<br /> DRMLicenseDomain licenseDomain, <br /> DRMOperationCompleteListener listener);<br /> <br /> void resetDRM(DRMOperationCompleteListener listener);<br /> void returnLicense(DomString serverURL, <br /> DomString licenseID, <br /> DomPolicy Id, <br /> boolean commitDirect,<br /> DRMReturnLicenseListener listener);<br /> void setAuthenticationToken(<br /> DRMMetadata, <br /> DomString authenticationDomain, <br /> Uint8Array-token, <br /> DRMOperationCompleteListener-listener);<br /> void storeLicenseBytes(Uint8Array-licentieBytes, <br /> DRMOperationCompleteListener-listener);<br /> };</p> </td> 
   <td><p>interface DRMManager: EventTarget {<br /> void verwervingLicense(DRMMetadata metadata, <br /> DRMAcquireLicenseSettings setting, <br /> EventContext eventContext);<br /> voidPreviewLicense(DRMMetadata metadata, <br /> EventContext eventContext);<br /> void authenticate(DRMMetadata) a6/&gt; DomString url,<br /> DomString &amp;authenticationDomain, <br /> DomString user, <br /> DomString password, <br /> EventContextContext);<br /> <br /> DRMMetadata createMetadataFromBytes(<br /> Uint8Array-array, EventContext-eventContext);<br /> void initialize(EventContext eventContext);<br /> attribuut long maxOperationTime;<br /> <br /> void joinLicenseDomain(<br /> DRMLicenseDomain licenseDomain, <br /> booleaanse forceRefresh, <br /> EventContext eventContext);<br /> void leaveLicenseDomain(<br /> DRMLicenseDomain licenseDomain, <br /> EventContext eventContext);<br /> <br /> void resetDRM(EventContext Context);<br /> void returnLicense(DomString serverURL, <br /> DomString licenseID,<br /> DomString policyID, <br /> boolean commitDirect,<br /> EventContext);<br /> void setContext AuthenticationToken(<br /> DRMMetadata metadata, <br /> DomString authenticationDomain, <br /> Uint8Array token, <br /> EventContext eventContext);<br /> void storeLicenseBytes(Uint8Array licenseBytes, <br /> Event Context eventContext);<br /> };<br /></p> </td> 
  </tr> 
  <tr> 
   <td><p>klasse DRMErrorListener: <br /> public psdkutils::PSDKInterfaceWithUserData {<br /> public:<br /> virtual void onDRMError(uint32_t major, <br /> uint32_t minor, <br /> const psdkutils: PSDKString&amp; errorString, <br /> const psdkutils::PSDKString&amp; errorServerUrl) = 0;<br /> <br /> protected:<br /> virtual ~DRMErrorListener() {}<br /> }</p> </td> 
   <td>Gebeurtenis/interface/beschrijving 
    <ul> 
     <li>kEventDRMOperationError<p>/ DRMOperationErrorEvent</p> <p>Wanneer een fout tijdens één van de asynchrone methodes van DRMManger voorkomt.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>klasse DRMOperationCompleteListener: <br /> public DRMErrorListener {<br /> public:<br /> virtual void onDRMOperationComplete() = 0;<br /> <br /> protected:<br /> virtual ~DRMOperationCompleteListener() {}<br /> };</p> </td> 
   <td>Gebeurtenis/interface/beschrijving 
    <ul> 
     <li>kEventDRMInitializationComplete<p>/ PSDKEvent</p> <p>Wanneer de initialisatie van DRM is voltooid.</p> </li> 
     <li>kEventDRMJoinLicenseDomainComplete<p>/ PSDKEvent</p> <p>Wanneer de joinLicenseDomain()-actie correct is voltooid.</p> </li> 
     <li>kEventDRMLeaveLicenseDomainComplete<p>/ PSDKEvent</p> <p>Wanneer de handeling leaveLicenseDomain() correct is voltooid.</p> </li> 
     <li>kEventDRMResetCompletePSDKEvent<p>/ PSDKEvent</p> <p>Wanneer resetDRM()-actie correct is voltooid.</p> </li> 
     <li>kEventDRMAuthenticationTokenSet<p>/ PSDKEvent</p> <p>Wanneer de handeling setAuthenticationTokenSet() correct is voltooid.</p> </li> 
     <li>kEventDRMLicenseStored<p>/ PSDKEvent</p> <p>Wanneer de handeling storeLicenseBytes() correct is voltooid.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>klasse DRMAuthenticateListener: <br /> openbare DRMErrorListener {<br /> public:<br /> virtuele void onAuthenticationComplete(<br /> psdkutils::PSDKImmutableByteArray* <br /> authenticationToken) = 0;<br /> <br /> protected:<br /> virtueel ~DRMAuthenticate Listener() {}<br /> }</p> </td> 
   <td>Gebeurtenis/interface/beschrijving 
    <ul> 
     <li>kEventDRMAuthenticationComplete<p>/ DRMAuthenticationCompleteEvent</p> <p>Wanneer DRMManager::authenticate de methodevraag succesvol is.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>klasse DRMAquireLicenseListener: <br /> public DRMErrorListener {<br /> public:<br /> virtual void onLicenseAcquired(const DRMLicense*) = 0;<br /> <br /> protected:<br /> virtual ~DRMAquireLicenseListener() {}<br /> };</p> </td> 
   <td>Gebeurtenis/interface/beschrijving 
    <ul> 
     <li>kEventDRMPreviewLicenseAcquired<p>/ DRMLicenseAcquiredEvent</p> <p>Wanneer DRMManager::verwervingPreviewLicense is aangeroepen.</p> </li> 
     <li>kEventDRMLicenseAcquired<p>/ DRMLicenseAcquiredEvent</p> <p>Wanneer DRMManager::verwervingLicense, aanroep van de methode succesvol is.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>klasse DRMReturnLicenseListener: <br /> public DRMErrorListener {<br /> public:<br /> virtual void onLicenseReturnComplete(uint32_t numGeretourneerd ) = 0;<br /> <br /> protected:<br /> virtual ~DRMReturnLicenseListener() {}<br /> };</p> </td> 
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
   <td><p>interface MediaResource {<br /> attribuut DomString url; <br /> attribuut unsigned short type;<br /> attribute Object metadata;<br /> const unsigned short TYPE_HLS;<br /> const unsigned short TYPE_HDS;<br /> const unsigned short TYPE_DASH;<br /> const unsigned short TYPE_CUSTOM;<br /> const unsigned short TYPE_UNKNOWN; a8/&gt; };<br /></p> </td> 
   <td><p>interface MediaResource {<br /> attribuut DomString url;<br /> attribuut DomString type;<br /> attribuut Object metadata;<br /> <br /> <br /> <br /> <br /> <br /> &lt;a8/&gt; };</p> </td> 
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
   <td><p>interface MediaPlayer: EventTarget<br /> {<br /> void prepareToPlay( dubbele positie);<br /> void play();<br /> void pause();<br /> void seek( dubbele positie);<br /> void seekToLocal( dubbele positie);<br /> void reset();<br /> void release();<br /> void replaceCurrentItem(MediaPlayerItem punt);<br /> void replaceCurrentResource(MediaResource bron, <br /> MediaPlayerItemConfig config); <br /> void suspend();<br /> void restore();<br /> void notifyClick();<br /> <br /> readonly attribute TimeRange playbackRange;<br /> readonly attribute TimeRange seekableRange;<br /> readonly attribute double currentTime;<br /> readonly attribute double localTime;<br /> readonly attribute TimeRange bufferedRange;<br /> readonly attribute DRMManager drmManager;<br /> readonly attribute MediaPlayerItem currentItem;<br /> <br /> // PlayerStatus<br /> <br />/&gt; const unsigned short PLAYER_STATUS_INITIALIZED;<br /> const unsigned short PLAYER_STATUS_PREPARING;<br /> const unsigned short PLAYER_STATUS_PREPARED;<br /> const unsigned short PLAYER_STATUS_PLAYING; a12/&gt; const unsigned short PLAYER_STATUS_PAUSED;<br /> const unsigned short PLAYER_STATUS_SEEKING;<br /> const unsigned short PLAYER_STATUS_COMPLETE;<br /> const unsigned short PLAYER_STATUS_NL FOUT;<br /> const unsigned short PLAYER_STATUS_RELEASED;<br /> <br /> <br /><br /> kenmerk readonly, kenmerk unsigned short status;<br /> <br /> kenmerk unsigned short volume;<br /> kenmerk ABRControlParameters abrControlParameters;<br /> kenmerk BufferControlParameters bufferControlParameters;<br /> <br /> const unsigned short VISIBLE; //Voor CC visibility<br /> const unsigned short INVISIBLE; //Voor CC visibility<br /> kenmerk unsigned short ccVisibility;<br /> kenmerk TextFormat ccStyle;<br /> kenmerk readonly attribute PlaybackMetrics playbackMetrics;<br /> <br /> kenmerk double rate;<br /> kenmerk MediaPlayerView view;<br /> kenmerk Alleen-lezen timeline;<br /> attribute double currentTimeUpdateInterval; <br /> // het plaatsen van dit zal niet voor 2.0<br />} worden gesteund;</p> </td> 
   <td><p>interface MediaPlayer: EventTarget<br /> {<br /> void prepareToPlay( int position);<br /> void play();<br /> void pause();<br /> void seek( int position);<br /> void seekToLocalTime( int position);<br /> void reset();<br /> void release();&lt;a8/ &gt; void replaceCurrentItem(MediaResource source);<br /> <br /> <br /> <br /> <br /> <br /> <br /> readonly attribute TimeRange playbackRange;<br /> readonly attribute TimeRange seekable;&lt;a1 Het kenmerk Alleen-lezen van het kenmerk double currentTime;<br /> kenmerk read-only is het kenmerk double localTime;<br /> kenmerk readonly van het kenmerk TimeRange bufferedRange;<br /> <br /><br /> read-only attribuut DRMManager drmManager;<br /> read-only attribute MediaPlayerItem currentItem;<br /> <br /> // PlayerState<br /> const unsigned short PLAYER_STATE_IDLE;<br /> const unsigned short PLAYER_STATE_INITIALIZING;<br /> const unsigned short PLAYER_STATE_INITIALIZED;<br /> const unsigned short PLAYER_STATE_PREPARING;<br /> const unsigned short PLAYER_STATE_PREPARED;<br /> const unsigned short PLAYER_STATE_PLAYING;<br /> const unsigned short PLAYER_STATE_PAUSED;<br /> const unsigned short PLAYER_STATE_SEEKING;<br /> const unsigned short PLAYER_STATE_COMPLETE;<br /> const unsigned short PLAYER_STATE_ERROR;<br /> const unsigned short PLAYER_STATE_RELEASED;<br /> const unsigned short PLAYER_STATUS_SUSPENDED;<br /> read-only attribute unsigned short state;<br /> <br /> kenmerk unsigned short volume;<br /> kenmerk ABRControlParameters abrControlParameters;<br /> kenmerk BufferControlParameters bufferControlParameters;<br /> <br /> alleen gelezen unsigned short VISIBLE; //Voor CC-zichtbaarheid<br /> alleen-lezen zonder teken kort ONZICHTBAAR; //Voor CC visibility<br /> kenmerk unsigned short ccVisibility;<br /> kenmerk TextFormat ccStyle;<br /> kenmerk readonly attribute PlaybackMetrics playbackMetrics;<br /> kenmerk MediaPlayerConfig mediaPlayerConfig;<br /> kenmerk double rate;<br /> kenmerk MediaPlayerView;&lt;a1 1/&gt; alleen-lezen kenmerk tijdlijn;<br /> <br /> <br /> };<br /></p> </td> 
  </tr> 
  <tr> 
   <td><p>interface MediaPlayerStatus<br /> {<br /> // PlayerStatus<br /> const unsigned short PLAYER_STATUS_IDLE;<br /> const unsigned short PLAYER_STATUS_INITIALIZING;<br /> const unsigned short PLAYER_STATUS_INITIALIZED;<br /> const unsigned short PLAYER_STATUS_PREPARING;<br /> const unsigned short PLAYER_STATUS_PREPARED;<br /> const unsigned short PLAYER_STATUS_PLAYING;<br /> const unsigned short PLAYER_STATUS_PAUSED;<br /> const unsigned short PLAYER LAYER_STATUS_SEEKING;<br /> const unsigned short PLAYER_STATUS_COMPLETE;<br /> const unsigned short PLAYER_STATUS_ERROR;<br /> const unsigned short PLAYER_STATUS_RELEASED;<br /> const st unsigned short PLAYER_STATUS_SUSPENDED;<br /> };</p> </td> 
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
   <td>adComplete</td> 
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
   <td>vordering</td> 
   <td>ProgressEvent</td> 
  </tr> 
  <tr> 
   <td>bufferingBegin</td> 
   <td>Gebeurtenis</td> 
   <td> </td> 
   <td>buffer</td> 
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
   <td>adClick<br /> Wanneer de gebruiker op Advertentie klikt.</td> 
   <td>AdClickedEvent</td> 
   <td> </td> 
   <td><p>Nieuw in 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>profileChanged<br /> Wanneer het playbackprofiel verandert.</td> 
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
   <td>audioUpdated<br /> Wanneer een media playeritem wordt bijgewerkt. Voor bepaalde streams die audiotracks bevatten die alleen tijdens het afspelen kunnen worden gedetecteerd, wordt deze gebeurtenis geactiveerd wanneer nieuwe audiotracks beschikbaar zijn.</td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>Nieuw in 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>captionsUpdated <br /> When a media player item is updated. Voor live/lineaire streams moet de client de mediabron periodiek vernieuwen om de nieuwe beschikbare inhoud te detecteren. Wanneer dit gebeurt, zouden bepaalde media kenmerken kunnen veranderen.</td> 
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
   <td>playbackRangeUpdated<br /> Wanneer een punt van de media speler wordt bijgewerkt. Voor live/lineaire streams moet de client de mediabron periodiek vernieuwen om de nieuwe beschikbare inhoud te detecteren. Wanneer dit gebeurt, zouden bepaalde media kenmerken kunnen veranderen.</td> 
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
   <td><p>interface ABRControlParameters<br /> {<br /> const unsigned short ABR_POLICY_CONSERVATIVE = 0 ;<br /> const unsigned short ABR_POLICY_MODERATE = 1 ;<br /> const unsigned short ABR_POLICY_AGGRESIVE = 2 ;<br /> <br /> kenmerk unsigned short abr Beleid;<br /> kenmerk unsigned int initialBitRate;<br /> kenmerk unsigned int minBitRate;<br /> kenmerk unsigned int maxBitRate;<br /> const unsigned short DEFAULT_ABR_INITIAL_BITRATE;<br /> const unsigned short DEFAULT_ABR_MIN_BITRATE ITRATE;<br /> const unsigned short DEFAULT_ABR_MAX_BITRATE;<br /> const ABRPopolicy DEFAULT_ABR_POLICY;<br /> };</p> </td> 
   <td><p>interface ABRControlParameters<br /> {<br /> const unsigned short ABR_POLICY_CONSERVATIVE = 0 ;<br /> const unsigned short ABR_POLICY_MODERATE = 1 ;<br /> const unsigned short ABR_POLICY_AGGRESIVE = 2 ;<br /> <br /> kenmerk unsigned short abr Beleid;<br /> kenmerk unsigned int initialBitRate;<br /> kenmerk unsigned int minBitRate;<br /> kenmerk unsigned int maxBitRate;<br /> <br /> <br /> <br /> <br /> };</p> </td> 
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
   <td><p>interface BufferControlParameters<br /> {<br /> attribuut double initialBufferTime;<br /> attribuut double playBufferTime;<br /> const double DEFAULT_INITIAL_BUFFER_TIME;<br /> const double DEFAULT_PLAY_BUFFER_TIME;<br /> };</p> </td> 
   <td><p>interface BufferControlParameters<br /> {<br /> attribuut double initialBufferTime;<br /> attribuut double playBufferTime;<br /> <br /> <br /> };</p> </td> 
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
   <td><p>interface TextFormat<br /> {<br /> // Color<br /> const unsigned short COLOR_DEFAULT = 0 ;<br /> const unsigned short COLOR_BLACK = 1 ;<br /> const unsigned short COLOR_GRAY = 2 ;<br /> const unsigned short COLOR_WHITE = 3 ; 6/&gt; const unsigned short COLOR_BRIGHT_WHITE = 4 ;<br /> const unsigned short COLOR_DARK_RED = 5 ;<br /> const unsigned short COLOR_RED = 6 ;<br /> const unsigned short COLOR_BRIGHT_RED = 7 ;<br /> const unsigned short COLOR_DOR ARK_GREEN = 8 ;<br /> const unsigned short COLOR_GREEN = 9 ;<br /> const unsigned short COLOR_BRIGHT_GREEN = 10 ;<br /> const unsigned short COLOR_DARK_BLUE = 11 ;<br /> const short COLOR_BLUE = 12 ;<br /> const unsigned short COLOR_BRIGHT_BLUE = 13 ;<br /> const unsigned short COLOR_DARK_YELLOW = 14 ;<br /> const unsigned short COLOR_YELLOW = 15 ; 118/&gt; <br /><br /> const unsigned short COLOR_BRIGHT_YELLOW = 16 ;<br /> const unsigned short COLOR_DARK_MAGENTA = 17 ;<br /> const unsigned short COLOR_MAGENTA = 18 ;<br /> const unsigned short COLOR_BRIGHT_MAGENTA = 19<br /> const st unsigned short COLOR_DARK_CYAN = 20 ;<br /> const unsigned short COLOR_CYAN = 21 ;<br /> const unsigned short COLOR_BRIGHT_CYAN = 22 ;<br /> <br /> readonly attribute unsigned short fontColor;<br /> readonly attribute&lt;unsigned short backgroundColor; a9/&gt; alleen-lezen kenmerk unsigned short fillColor;<br /> alleen-lezen kenmerk unsigned short edgeColor;<br /> <br /> // Size<br /> const unsigned short SIZE_DEFAULT = 0;<br /> const unsigned short SIZE_SMALL = 1 ; 5/&gt; const unsigned short SIZE_MEDIUM = 2 ;<br /> <br /><br /> const unsigned short SIZE_LARGE = 3 ;<br /> <br /> readonly attribute unsigned short size;<br /> <br /> // FontEdge<br /> const unsigned short FONT_EDGE_DEFAULT = 0 ;<br /> const unsigned short FONT_EDGE_NONE = 1;<br /> const st unsigned short FONT_EDGE_RAISED = 2 ;<br /> const unsigned short FONT_EDGE_DEPRESSED = 3 ;<br /> const unsigned short FONT_EDGE_UNIFORM = 4 ;<br /> const unsigned short FONT_EDGE_DROP_SHADOW_LEFT = 5 ; a 10/&gt; const unsigned short FONT_EDGE_DROP_SHADOW_RIGHT = 6 ;<br /> readonly attribute unsigned short fontEdge;<br /> <br /> // Font<br /> const unsigned short FONT_DEFAULT = 0 ;<br /> const unsigned short FONT_MONOSPACED_WITH_SERIFS = 1 ;<br /><br /> const unsigned short FONT_PROPORTIONAL_WITH_SERIFS = 2 ;<br /> const unsigned short FONT_MONSPACED_WITHOUT_SERIFS = 3 ;<br /> const unsigned short FONT_CASUAL = 4 ;<br /> const unsigned short FONT_CURSIVE = 5 ;<br /> const ondertekende korte FONT_SMALL_CAPITALS = 6;<br /> kenmerk Alleen-lezen kenmerk unsigned short font;<br /> kenmerk Alleen-lezen kenmerk unsigned short fontOpacity;<br /> kenmerk read-only kenmerk unsigned short backgroundOpacity;<br /> kenmerk read-only kenmerk unsigned short fillOpacity;<br /> kenmerk readonly kenmerk unsigned short DEFAULT_OPACITY; a9/&gt; };<br /></p> </td> 
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
   <td><p>interface MediaPlayerItemLoader:<br /> {<br /> void(MediaResource resource, long resourceId,<br /> ItemLoaderListener listener, <br /> MediaPlayerItemConfig config);<br /> void cancel();<br /> readonly attribute MediaPlayerItem currentItem;<br /> };</p> </td> 
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
   <td><p>interface MediaPlayerItem {<br /> kenmerk Alleen-lezen MediaResource-resource;<br /> kenmerk alleen-lezen lange resourceId;<br /> kenmerk alleen-lezen booleaanse live;<br /> <br /> kenmerk alleen-lezen boolean hasAlternateAudio;<br /> kenmerk kenmerk Alleen-lezen AudioTrackList audioTracks;<br /> kenmerk Alleen-lezen Track;<br /> void selectAudioTrack(AudioTrack); <br /> <br /> Alleen-lezen kenmerk boolean hasClosedCaptions;<br /> alleen-lezen kenmerk ClosedCaptionsTrackList closedCaptionsTracks;<br /> alleen-lezen kenmerk ClosedCaptionsTrack selectedClosedCaptionsTrack;<br /> void selectClosedCaptionsTrack() 13/&gt; ClosedCaptionsTrack (track); <br /> <br /> Alleen-lezen kenmerk boolean hasTimedMetadata;<br /> alleen-lezen kenmerk TimedMetadataList timedMetadata;<br /> alleen-lezen kenmerk boolean dynamic;<br /> <br /> alleen-lezen kenmerk boolean isProtected;<br /> alleen-lezen kenmerk DRMMetadataInfoList drmMetadataInfos;<br /> alleen-lezen kenmerk ProfileList-profielen;<br /> alleen-lezen kenmerk Profile selectedProfile;<br /> <br /> alleen-lezen kenmerk boolean trickPlaySupported;<br /> alleen-kenmerk FloatArray PlaybackRates;<br /> alleen-lezen kenmerk float selectedPlaybackRate;<br /> <br /> <br /> alleen-lezen kenmerk MediaPlayer mediaPlayer;<br /> alleen-lezen kenmerk MediaPlayerItemConfig;<br /> };<br /></p> </td> 
   <td><p>interface MediaPlayerItem {<br /> read-only attribuut MediaResource middel;<br /> readonly attribute long resourceId;<br /> readonly attribute boolean live;<br /> <br /> readonly attribute boolean hasAlternateAudio;<br /> readonly attribute AudioTrackList audioTracks;<br /> attribute AudioTrack selectedAudioTrack <br /> <br /> <br /> Alleen-lezen-kenmerk boolean hasClosedCaptions;<br /> alleen-lezen-kenmerk ClosedCaptionsTrackList ccTracks;<br /> kenmerk ClosedCaptionsTrack selectedCCTrack;<br /> <br />&gt; <br /> Alleen-lezen kenmerk boolean hasTimedMetadata;<br /> alleen-lezen kenmerk TimedMetadataList timedMetadata;<br /> alleen-lezen kenmerk boolean dynamic;<br /> <br /> alleen-lezen kenmerk boolean isProtected;<br /> alleen-kenmerk DRMM MetadataInfoList drmMetadataInfos;<br /> Alleen-lezen kenmerkprofielen ProfileList;<br /> <br /> <br /> Alleen-lezen kenmerk boolean trucPlaySupported;<br /> alleen-lezen kenmerk Int32Array availablePlaybackRates;<br /> <br /> kenmerk Alleen-lezen StringList enTags;<br /> <br /> kenmerk Alleen-lezen MediaPlayer mediaPlayer;<br /> <br /> };<br /></p> </td> 
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
   <td><p>interface Track<br /> {<br /> alleen-lezen kenmerk DomString-naam;<br /> alleen-lezen kenmerk DomString-taal;<br /> alleen-lezen kenmerk boolean standaard;<br /> alleen-lezen kenmerk boolean autoSelect;<br /> }; </p> </td> 
   <td>Nieuw voor 2.0</td> 
  </tr> 
  <tr> 
   <td><p>interface AudioTrack: Track<br /> {<br /> alleen-lezen kenmerk DomString-naam; //FromTrack<br /> kenmerk Alleen-lezen DomString-taal;//FromTrack<br /> kenmerk boolean default; // Van track<br /> alleen-lezen kenmerk booleaanse autoSelect;//FromTrack<br /> <br /> kenmerk alleen-lezen kenmerk unsigned int pid;<br /> };</p> </td> 
   <td><p>interface AudioTrack<br /> {<br /> alleen-lezen kenmerk DomString-naam;<br /> alleen-lezen kenmerk DomString-taal; <br /> read-only attribuut boolean default;<br /> readonly attribute boolean autoSelect;<br /> readonly attribute boolean forcated;<br /> <br /> };</p> </td> 
  </tr> 
  <tr> 
   <td>Geen wijziging voor 2.0</td> 
   <td><p>interface AudioTrackList<br /> {<br /> kenmerk read-only lange lengte zonder teken;<br /> getter AudioTrack (unsigned long index);<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface ClosedCaptionsTrack: Track<br /> {<br /> alleen-lezen kenmerk DomString-naam; //FromTrack<br /> kenmerk Alleen-lezen DomString-taal;//FromTrack<br /> kenmerk boolean default; // FromTrack<br /> read-only attribute boolean autoSelect;//FromTrack<br /> <br /> <br /> const unsigned short SERVICE_608_CAPTIONS = 0;<br /> const unsigned short SERVICE_708_CAPTIONS = 1;<br /> const unsigned short SERVICE_WEB_VTT_CAPTIONS = 2;<br /> read-only attribuut unsigned short serviceType;<br /> readonly attribute boolean required;<br /> };</p> </td> 
   <td><p>interface ClosedCaptionsTrack<br /> {<br /> alleen-lezen kenmerk DomString-naam;<br /> alleen-lezen kenmerk DomString-taal;<br /> alleen-lezen kenmerk booleaanse standaard;<br /> <br /> <br /> alleen-lezen kenmerk booleaan actief;<br /> <br /> <br /> a11/&gt; <br /> };<br /><br /></p> </td> 
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
   <td><p>interfaceprofiel<br /> {<br /> alleen-lezen kenmerk unsigned int width;<br /> alleen-lezen kenmerk unsigned int height;<br /> kenmerk read-only kenmerk unsigned int bitRate;<br /> }; </p> </td> 
  </tr> 
  <tr> 
   <td>Profiellijst: Geen wijziging voor 2.0</td> 
   <td><p>interface ProfileList<br /> {<br /> read-only attributen unsigned long length;<br /> getter Profile(unsigned long index);<br /> };</p> </td> 
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
   <td><p>interface DRMMetadataInfo<br /> { <br /> read-only attributen DRMMetadata metadata;<br /> readonly attributen long prefetchTimestamp;<br /> readonly attributen TimeRange timeRange;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>DRMMetadataInfoList</strong>: Geen wijziging voor 2.0</td> 
   <td><p>interface DRMMetadataInfoList<br /> {<br /> kenmerk read-only lange lengte zonder teken;<br /> getter DRMMetadataInfo(unsigned long index);<br /> };</p> </td> 
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
   <td><p>interfaceversie<br /> {<br /> read-only attributen DomString versie;<br /> readonly attributen DomString beschrijving;<br /> readonly attributen long major;<br /> readonly attributen long minor;<br /> readonly attributen long revision;<br /> readonly attribute long apiVersion;<br /> };</p> </td> 
   <td><p>interface Version<br /> {<br /> readonly attribute DomString version;<br /> readonly attribute DomString description;<br /> readonly attribute DomString major;<br /> readonly attribute DomString minor;<br /> readonly attribute DomString revision;<br /> readonly attribute DomString apiVersion;<br /> };</p> </td> 
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
   <td><p>interface TimeRange<br /> {<br /> readonly attributen unsigned long begin;<br /> readonly attributen unsigned long end;<br /> readonly attributen unsigned long duration;<br /> };</p> </td> 
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
   <td><p>interface QOSProvider<br /> {<br /> void attachMediaPlayer(MediaPlayer speler);<br /> void detachMediaPlayer();<br /> <br /> readonly attribute DeviceInformation deviceInformation;<br /> readonly attribute PlaybackInformation playbackInformation;<br /> };</p> </td> 
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
   <td><p>interface DeviceInformation<br /> {<br /> alleen-lezen kenmerk DomString os;<br /> <br /> <br /> <br /> alleen-lezen kenmerk DomString id;<br /> alleen-lezen kenmerk int densityDPI;<br /> alleen-lezen kenmerk int heightPixels;<br /> alleen kenmerk int width<br /> alleen-lezen kenmerk boolean seekToKeyFrame;<br /> };</p> </td> 
   <td><p>interface DeviceInformation<br /> {<br /> read-only attribute DomString os;<br /> readonly attribute int sdk;<br /> readonly attribute DomString model;<br /> readonly attribute DomString manufacturer;<br /> readonly attribute DomString id;<br /> readonly attribute intDPI;<br /> readonly kenmerk int heightPixels;<br /> kenmerk read-only int widthPixels;<br /> <br /> };</p> </td> 
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
   <td><p>interface LoadInfo<br /> {<br /> alleen-lezen kenmerk DomString url;<br /> alleen-lezen kenmerk int size;<br /> alleen-lezen kenmerk double downloadDuration;<br /> alleen-lezen kenmerk int periodIndex;<br /> alleen-lezen kenmerk double mediaDuration;<br /> alleen-lezen kenmerk short TRACK_TYPE_FRAGMENT;<br /> readonly attribute short TRACK_TYPE_TRACK;<br /> readonly attribute short TRACK_TYPE_MANIFEST;<br /> readonly attribute short type;<br /> readonly attribute DomString trackName;<br /> readonly attribute DomString trackType;<br /> readonly attribute int trackIndex;&lt;a1 3/&gt; };<br /></p> </td> 
  </tr> 
 </tbody> 
</table>

### {#view} weergeven

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API's</th> 
   <th>1.3 API's</th> 
  </tr> 
  <tr> 
   <td>Geen wijziging voor 2.0</td> 
   <td><p>interface View<br /> {<br /> read-only attribuut unsigned short x;<br /> readonly attribute unsigned short y;<br /> readonly attribute unsigned short width;<br /> readonly attribute unsigned short height;<br /> <br /> void setSize(unsigned short width, unsigned short height);<br /> void setPos(unsigned short x, kort zonder teken y);<br /> }</p> </td> 
  </tr> 
 </tbody> 
</table>

### PlaybackInformation {#playbackinformation}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API's</th> 
   <th>1.3 API's</th> 
  </tr> 
  <tr> 
   <td><p>interface PlaybackInformation<br /> {<br /> readonly attribuut double timeToFirstByte;<br /> readonly attribute double timeToLoad;<br /> readonly attribute double timeToStart;<br /> readonly attribute double timeToFail;<br /> readonly attribute int totalSecondsPlayed;<br /> readonly attribute int totalSecondsSpent;<br /> kenmerk read-only double frameRate;<br /> kenmerk read-only int droppedFrameCount;<br /> kenmerk read-only int gezienBandwidth;<br /> kenmerk readonly int bitrate;<br /> kenmerk readonly kenmerk double bufferTime;<br /> kenmerk readonly kenmerk intLength;<br /> readonly attribute int emptyBufferCount;<br /> readonly attribute double bufferingTime;<br /> };</p> </td> 
   <td><p>interface PlaybackInformation<br /> {<br /> readonly attribuut double timeToFirstByte;<br /> readonly attribute double timeToLoad;<br /> readonly attribute double timeToStart;<br /> readonly attribute double timeToFail;<br /> readonly attribute int totalSecondsPlayed;<br /> readonly attribute int totalSecondsSpent;<br /> kenmerk read-only double frameRate;<br /> kenmerk readonly int droppedFrameCount;<br /> <br /> kenmerk readonly int bitrate;<br /> kenmerk readonly double bufferTime;<br /> kenmerk readonly attribute int bufferLength;<br /> readonly kenmerk int emptyBufferCount;<br /> kenmerk read-only double bufferingTime;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

## Nuttige bronnen {#helpful-resources}

* Zie de volledige Help-documentatie op de pagina [Adobe Primetime Learn &amp; Support](https://helpx.adobe.com/support/primetime.html).
