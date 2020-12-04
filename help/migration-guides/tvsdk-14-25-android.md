---
title: TVSDK 1.4 tot en met 2.5 voor Android (Java)
seo-title: TVSDK 1.4 tot en met 2.5 voor Android (Java)
description: TVSDK 2.5 biedt meerdere voordelen ten opzichte van versie 1.4 in termen van prestaties, beveiliging, betere integratie en meer.
seo-description: TVSDK 2.5 biedt meerdere voordelen ten opzichte van versie 1.4 in termen van prestaties, beveiliging, betere integratie en meer.
uuid: aaab7aec-cb5b-4840-82e8-7112a8d98a8a
contentOwner: vishgupt
products: SG_PRIMETIME
topic-tags: migration
discoiquuid: 8d9136bf-b3ae-450c-bd8a-0bb246527886
translation-type: tm+mt
source-git-commit: e644e8497e118e2d03e72bef727c4ce1455d68d6
workflow-type: tm+mt
source-wordcount: '2343'
ht-degree: 0%

---


# TVSDK 1.4 tot en met 2.5 voor Android (Java) {#tvsdk-to-for-android-java}

TVSDK 2.5 biedt meerdere voordelen ten opzichte van versie 1.4 in termen van prestaties, beveiliging, betere integratie en meer.

TVSDK lost de grootste uitdagingen op, op het apparaat dat het belangrijkst is. Android gaat door met de wereldwijde dominantie, met meer dan 86% van het marktaandeel. Bij de migratie naar TVSDK op Android worden de afspeelprestaties geoptimaliseerd om de betrokkenheid van gebruikers te verbeteren en de time-to-market te versnellen met ondersteuning voor nieuwe indelingen voor inhoud.

## Voordelen van migratie naar TVSDK v2.5 {#benefits-of-migrating-to-tvsdk-v}

TVSDK 2.5 biedt meerdere voordelen ten opzichte van versie 1.4 in termen van prestaties, beveiliging, betere integratie en meer. Lees verder om snel te weten wat de voordelen zijn van migreren naar deze nieuwe versie.

Volgens een benchmarkingstudie van derden biedt v2.5 een vermindering van 5 keer de opstarttijd en een vermindering van 3,8 keer de gedropte frames ten opzichte van het gemiddelde in de branche.

| Prestatiekenmerken | Beschrijving |
|--- |--- |
| Instant-on voor VOD en Live | Laad initiële ts-segmenten vooraf voor onmiddellijke weergave voor VOD- en live-lineaire streams tijdens kanaalomschakeling, voor een tv-achtige ervaring. |
| Lazy en laden | Hiermee wordt het afspelen gestart zodra de inhoud vóór de rol beschikbaar is en halverwege de rol geplaatste advertenties in een parallelle thread worden opgelost. |
| Blijvende netwerkverbindingen | Verhoog de efficiëntie en verlaag de latentie van netwerkcode voor snellere afspeelprestaties. |
| Verbeterde ABR-logica | De nieuwe logica ABR is gebaseerd op bufferlengte, tarief van verandering van bufferlengte, en gemeten bandbreedte. Dit zorgt ervoor dat ABR het juiste beetjetarief kiest wanneer de bandbreedte fluctueert en ook het aantal tijden optimaliseert de bitsnelheidschakelaar eigenlijk door het tarief te controleren waarbij de bufferlengte verandert. |
| Gedeeltelijke segmentdownload | Hiermee wordt het afspelen gestart zodra voldoende frames van een segment beschikbaar zijn om video betrouwbaar op de client te renderen. |
| Parallelle downloads | TVSDK downloadt parallel audio- en videosegmenten voor gedempte inhoud om de afspeelprestaties te optimaliseren. |

De afspeelfuncties verbeteren de betrokkenheid van de consument doordat ze de ervaring van lineaire uitzending op digitaal afspelen bieden. Bovendien kunt u native DRM zoals Windows gebruiken voor HD-weergave.

| Afspeelfuncties | Beschrijving |
|--- |--- |
| MP4 afspelen | MP4-korte clips hoeven niet opnieuw te worden getranscodeerd om te worden afgespeeld in TVSDK. |
| DASH VOD-inhoud afspelen | De standaard DASH VOD-afspeelvoorbeelden worden ondersteund. |
| Vloeiend Trickplay met ABR | Ondersteuning voor snel voorwaarts en terugspoelen in HLS met gebruik van hoofdframes met lage snelheden en I-frames met snellere snelheden. ABR-ondersteuning voor alle ondersteunde frames. |

De functies zijn belangrijk om te voldoen aan de studierichting, zoals het afspelen van HD via native DRM.

| Functies | Beschrijving |
|--- |--- |
| Uitvoerbeveiliging op basis van resolutie | het afspelen kan worden beperkt tot alleen bepaalde resoluties die zijn toegestaan door DRM-vereisten. Alleen beschikbaar via Primetime DRM. |
| Widevine-ondersteuning | Ondersteund met DASH VOD-streams om native DRM-gebruiksproblemen in te schakelen. |

Directe factureringsverbeteringen maken het niet meer nodig om maandelijks handmatige rapporten voor facturering te maken. VHL 2.0 staat voor een snellere tijd aan markt met pre-bouwstijlintegratie en betere nauwkeurigheid in het volgen toe.

| Functies | Beschrijving |
|--- |--- |
| Moatintegratie | Ondersteuning voor meting van de weergavekenbaarheid van advertenties vanuit de maan. |
| VHL 2.0 | De meest recente geoptimaliseerde integratie van videohartslagen in de bibliotheek voor automatische verzameling van gebruiksgegevens voor Adobe Analytics. |
| Ondersteuning voor failover | Aanvullende strategieën die zijn geïmplementeerd om het afspelen zonder onderbreking voort te zetten, ondanks fouten met hostservers, afspeellijstbestanden en segmenten. |
| Integratie van directe facturering | Verzendt factureringsmetriek naar Adobe Analytics backend die door Adobe Primetime voor stromen wordt verklaard die door klant worden gebruikt. |

>[!NOTE]
>
>Alle functies van TVSDK v1.4 worden ondersteund in v2.5, behalve de ondersteuning voor Multi-CDN.

## Overzicht van het migratieproces {#overview-of-the-migration-process}

Voor een vloeiende migratie van TVSDK 1.4 naar 2.5 moet u overschakelen naar versie 2.5-bibliotheken, opnieuw compileren en vervolgens met dit document problemen opsporen die zich voordoen.

TVSDK v1.4-bibliotheken werken niet met en bestaan niet samen met v2.5-bibliotheken. U moet v2.5-bibliotheken gebruiken met TVSDK 2.5 en uw toepassingen en integratie migreren voor een upgrade naar TVSDK 2.5. In dit document wordt beschreven hoe en wat er moet worden gewijzigd in uw toepassingscode en hoe fouten moeten worden aangepakt tijdens het opnieuw compileren.

Het bestand psdk.jar gebruikt bibliotheken van derden voor de ondersteuning van verschillende functies. Als u wilt voorkomen dat de bibliotheken worden verwijderd, neemt u het volgende op in het `proguard.cfg`-bestand:

```java
# Adobe TVSDK keep classes
-keep class com.adobe.** { *; }
-keep class com.google.android.exoplayer.**
{ *; }
```

In het `build.gradle`-bestand moet u de compilerinstructie opnemen om de JAR-bestanden op TVSDK-basis op te nemen. Als uw app Adobe Video Analytics bevat, moet u de compilatierichtlijn opnemen voor de extra potten die vereist zijn voor de integratie van Adobe Video Analytics in de app

```java
# Compile Adobe TVSDK jars compile files('libs/psdk-va.jar')
compile files('libs/VideoHeartbeat.jar')
```

Meerdere kleine wijzigingen worden niet in dit document behandeld. Raadpleeg [TVSDK 2.5 voor Android Java API](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.5/index.html) voor de kleine wijzigingen in de API. De overeenkomstige C++ API verwijzing heeft gedetailleerde beschrijvingen. Zie [TVSDK 2.5 voor Android C++ API](https://help.adobe.com/en_US/primetime/api/psdk/cpp_2.5/index.html) voor analoge C++ API-documentatie.

Meerdere voorbeelden van het API-gebruik worden behandeld in de referentie-implementatie die met de TVSDK wordt gedistribueerd.

## API-wijzigingen in TVSDK v2.5 {#api-changes-in-tvsdk-v}

De nieuwe, verouderde en gewijzigde API&#39;s worden hieronder beschreven.

| TVSDK v1.4 | TVSDK v2.5 | Beschrijving |
|--- |--- |--- |
| import com.adobe.ave.drm.DRMAcquireLicenseSettings | import com.adobe.mediacore.drm.DRMAcquireLicenseSettings; | Alle klassenamen in de TVSDK 2.5-API beginnen met het voorvoegsel com.adobe.mediacore. Dit is slechts een voorbeeld. |
| MediaPlayerException, IllegalStateException, of IllegalArgumentException | MediaPlayerException | In 2.5 genereren de API&#39;s alleen MediaPlayerException. |
| MediaPlayer.PlayerState (MediaPlayer.Event.PLAYBACK) | MediaPlayerStatus (MediaPlayerEvent.STATUS_CHANGED) | In v2.5 werd de naam van MediaPlayer.PlayerState gewijzigd in een aparte opsomming MediaPlayerStatus. |
| DefaultMediaPlayer.create (getActivity().getApplicationContext()) | MediaPlayer mediaPlayer = new MediaPlayer(getActivity(). getApplicationContext(); | De statische methoden die worden gebruikt om objecten te maken, worden vervangen door openbare constructors. |
| MediaPlayer.seekToLocalTime() | MediaPlayer.seekToLocal() | De methode MediaPlayer.seekToLocalTime() heet nu MediaPlayer.seekToLocal(). |
| closedCaptionsTrack.isActive() |  | Niet beschikbaar |
| MetadataNode | Metagegevens | In v2.5 vervangt de klasse Metadata het gebruik van de klasse MetadataNode van versie 1.4. |
| DefaultMetadataKeys | MetadataKeys | De DefaultMetadataKeys van v1.4 bevinden zich in v2.5 enum MetadataKeys. |
| AdvertisingFactory | ContentFactory | De AdvertisingFactory van v1.4 wordt hernoemd naar ContentFactory in v2.5 |
| PlacementOpportunityDetector | OpportunityGenerator | Detectoren worden vervangen door generatoren. |
| mediaPlayer.getView().notifyClick(); | mediaPlayer.notifyClick(); | De methode notifyClick() van MediaPlayerView is verplaatst naar de MediaPlayer-klasse. |
| public ABRControlParameters(ABRPopolicy abrPolicy, int nInitialBitRate, int nMinBitRate, int nMaxBitRate) | public ABRControlParameters(int nInitialBitRate, int nMinBitRate, int nMaxBitRate, ABRPopolicy abrPolicy, int nMinTrickPlayBitRate, int nMaxTrickPlayBitRate, int nMaxTrickPlayBandwidthUsage, double dMax layoutRate) |  |
| playbackInformation.getTimeToFirstFrame() |  | Niet beschikbaar |
|  | playbackInformation.get PerceptionBandwidth() | TVSDK v2.5 QOSProvider heeft een nieuwe eigenschap om de waargenomen bandbreedte tijdens een streamingsessie te bepalen. |

### Verwijderde klassen {#removed-classes}

De volgende klassen worden verwijderd en hebben geen equivalenten.

* `TimeRangeCollection`
* `PSDKConfig`
* `BaseLogger`
* `DefaultLogger`
* `Log`
* `Logger`
* `LogFactory`
* `NullLogger`

De laatste zes van deze klassen zijn beschikbaar als nutsklassen in de verwijzingsimplementatie.

## Wijzigingen in naamruimte {#namespace-changes}

De TVSDK 2.5-API consolideert naamruimten.

Alle klassenamen in de TVSDK 2.5-API beginnen met het voorvoegsel com.adobe.mediacore. Sommige klassenamen in de TVSDK 1.4-API beginnen met com.adobe.ave. De corresponderende 2.5-klassen veranderen com.adobe.ave in com.adobe.mediacore. Let bijvoorbeeld op de wijzigingen in de volgende coderegels voor 1.4 en 2.5:

```java
// TVSDK 1.4
import com.adobe.ave.drm.DRMAcquireLicenseSettings; import com.adobe.ave.drm.DRMLicense;
import com.adobe.ave.drm.DRMManager; import com.adobe.ave.drm.DRMMetadata
```

```java
// TVSDK 2.5
import com.adobe.mediacore.drm.DRMAcquireLicenseSettings; import com.adobe.mediacore.drm.DRMLicense;
import com.adobe.mediacore.drm.DRMManager; import com.adobe.mediacore.drm.DRMMetadata;
```

## Wijzigingen in gebeurtenisafhandeling {#changes-in-event-handling}

Wanneer u gebeurtenissen in deze versie wilt registreren, geeft u de handler door aan `addEventListener`. De lijst van gebeurtenissen is ingrijpend herzien van versie 1.4 naar versie 2.5.\
Hier ziet u bijvoorbeeld hoe u een gebeurtenishandler registreert voor `MediaPlayerEvent.STATUS_CHANGED:`

```java
mPlayer.addEventListener(MediaPlayerEvent.STATUS_CHANGED,
new StatusChangeEventListener() {
@Override
public void onStatusChanged(MediaPlayerStatusChangeEvent event) {
//Handle status change event
}
});
```

Zo is de gebeurtenis geregistreerd in 1.4:

```java
mPlayer.addEventListener(MediaPlayer.Event.PLAYBACK, new MediaPlayer.PlaybackEventListener() {
@Override
public void onStateChanged(MediaPlayer.PlayerState state,
MediaPlayerNotification notification) {
//Handle status change event
}
// Additional handlers
...
});
```

Het opsommingsteken MediaPlayerEvent bevat alle gebeurteniscodes. De volgende gebeurteniscodes uit 1.4 bestaan niet meer in 2.5:

* `ADBREAK_PLACEMENT_COMPLETED`
* `ADBREAK_PLACEMENT_FAILED`
* `ADBREAK_REMOVAL_COMPLETED`
* `AD_BREAK_MANIFEST_LOAD_COMPLETE`
* `AD_MANIFEST_LOAD_COMPLETE`
* `AD_MANIFEST_LOAD_FAILED`
* `AUDIO_TRACK_FAILED`
* `BACKGROUND_MANIFEST_FAILED`
* `BUFFERING_FULL, CUSTOM_AD_EVENT`
* `CONTENT_MARKER`
* `CONTENT_PLACEMENT_COMPLETE`
* `CONTENT_CHANGED`
* `ITEM_REPLACED`
* `ITEM_READY`
* `VIEW_CLICKED`
* `PREPARED`
* `UPDATED`
* `OPPORTUNITY_COMPLETED`
* `OPPORTUNITY_CREATED`
* `OPPORTUNITY_FAILED`
* `PAUSE_AT_PERIOD_END`
* `PLAYBACK_STARTED`
* `PLAYBACK_PAUSED`
* `PLAYBACK_COMPLETED`
* `PLAY_COMPLETE`
* `POST_ROLL_COMPLETE`
* `RESOURCE_LOADED`
* `TIMED_METADATA_SKIPPED`
* `VIDEO_ERROR`
* `VIDEO_STATE_CHANGED`

De volgende gebeurteniscodes zijn nieuw in 2.5:

* `AD_RESOLUTION_COMPLETE`
* `BUFFER_PREPARED`
* `CAPTIONS_UPDATED`
* `MANIFEST_UPDATED`
* `PLAYBACK_RANGE_UPDATED`
* `RESERVATION_REACHED`
* `TIME_CHANGED`
* `TIMED_EVENT`
* `TIMED_METADATA_ADDED_IN_BACKGROUND`

### Naam van gebeurtenissen wijzigen {#renamed-events}

| Nieuwe naam | Oude naam |
|--- |--- |
| ZOEKEN_BEGIN | ZOEKEN_STARTEN |
| SEEK_END | ZOEKEN_VOLTOOID |
| SEEK_POSITION_ADJUSTED | SEEK_ADJUST_COMPLETED |
| BUFFERING_BEGIN | BUFFERING_STARTED |
| BUFFERING_END | BUFFERING_COMPLETED |
| AUDIO_TRACK_UPDATED | AUDIO_TRACK_CHANGED |
| STATUS_CHANGED | STATE_CHANGED |
| TIMED_METADATA_AVAILABLE | TIMED_METADATA_ADDED |
| SIZE_AVAILABLE | SIZE_CHANGED |
| LOAD_INFO | LOAD_INFORMATION_AVAILABLE |

## Wijzigingen in MediaPlayer {#mediaplayer-changes}

Een nieuwe manier om `MediaPlayer` en veranderingen in sommige methodes te construeren.

**Wijzigingen in de MediaPlayer-klasse**

Hier volgen de wijzigingen in de klasse `MediaPlayer`:

* De `MediaPlayerStatus` enum vervangt `MediaPlayer.PlayerState`. Bijvoorbeeld:

```java
//TVSDK v1.4
mPlayer. addEventListener(MediaPlayer.Event.PLAYBACK, new MediaPlayer.PlaybackEventListener() {

@Override
public void onStateChanged(MediaPlayer.PlayerState state,MediaPlayerNotification notification) {
//Handle status change event
}
// Additional handlers
...
});

//TVSDK v2.5
mPlayer.addEventListener(MediaPlayerEvent.STATUS_CHANGED, new StatusChangeEventListener() {
@Override
public void onStatusChanged(MediaPlayerStatusChangeEvent event) {
//Handle status change event
}
//Additional handlers.
...
});
```

* De methode `MediaPlayer.seekToLocalTime()` wordt nu `MediaPlayer.seekToLocal` genoemd. Bijvoorbeeld:

```java
//TVSDK v1.4
public void seekToLocal(long localPosition) { mediaPlayer.seekToLocalTime(localPosition);
}

//TVSDK v2.5
public void seekToLocal(long localPosition) { mediaPlayer.seekToLocal(localPosition);
}
```

* De methode `MediaPlayerView.notifyClick()` is nu `MediaPlayer.notifyClick()`. Bijvoorbeeld:

```java
//TVSDK v1.4
public void adClick() { mediaPlayer.getView().notifyClick();
}

//TVSDK v2.5
public void adClick() { mediaPlayer.notifyClick();
}
```

* De oude methode `MediaPlayer.MediaPlayer.getNotificationHistory()` is nu verdwenen en niet vervangen.
* De eerste `MediaPlayer.replaceCurrentItem()` wordt in twee methoden gesplitst: `replaceCurrentResource()`, die een instantie van `MediaResource`, en `replaceCurrentItem()` neemt, die een geval van `MediaPlayerItem` neemt. Bijvoorbeeld:

```java
//TVSDK v1.4
MediaResource playerResource = MediaResource.createFromUrl(url, getAdvertisingMetadata());

mediaPlayer.replaceCurrentItem(playerResource);

//TVSDK v2.5 - replacing a resource
MediaResource playerResource = new MediaResource(url,
MediaResource.Type.HLS, getAdvertisingMetadata());
...
try {
mMediaPlayer.replaceCurrentResource(playerResource, _mediaPlayerItemConfig);
} catch (MediaPlayerException mediaPlayerException) {
// handle exception.
}
// TVSDK 2.5 - replacing an Item
MediaPlayerItemLoader itemLoader = new MediaPlayerItemLoader(context, new MediaPlayerItemLoader.LoaderListener() {

@Override
public void onError(PSDKErrorCode psdkErrorCode, String s) {
...
}
@Override
public void onLoadComplete(MediaPlayerItem mediaPlayerItem) {
...
}
@Override
public void onBufferingBegin() {
...
}
@Override
public void onBufferPrepared() {
...
}
});
MediaResource playerResource = new MediaResource(url,
MediaResource.Type.HLS, getAdvertisingMetadata());

itemLoader.load(playerResource); itemLoader.prepareBuffer();
mediaPlayer.replaceCurrentItem(itemLoader.getItem());
```

U kunt dit gebruiken om tussen pre-geïnitialiseerde instanties MediaPlayer, zoals in het geval van stroomonderbrekingen te schakelen.

**Constructors vervangen de methode static create()**

U kunt constructors gebruiken in TVSDK v2.5 in plaats van de methoden `create()` van TVSDK v1.4 te gebruiken. Alle klassen met namen die met Standaard beginnen, zoals `DefaultMediaPlayer`, `DefaultNetworkConfig`, `DefaultContentFactory`, zijn niet beschikbaar in v2.5.

In sommige gevallen gebruikt de TVSDK v1.4-API het volgende patroon voor het maken van klassen:

1. Definieer een interface (bijvoorbeeld `MediaPlayer`).
1. Geef een standaardklasse op (bijvoorbeeld `DefaultMediaPlayer`).
1. Verstrek een `create()` methode op de standaardklasse om een klasse te leveren die de interface uitvoert.

In TVSDK v2.5 zijn dergelijke interfaces concrete klassen en u maakt instanties van deze klassen met de respectievelijke constructors. Dit verschil wordt geïllustreerd door de volgende codefragmenten:

```java
//TVSDK v1.4
// Create a media player
// MediaPlayer is an interface
private MediaPlayer createMediaPlayer() { MediaPlayer mediaPlayer =
DefaultMediaPlayer.create(getActivity().getApplicationContext()); return mediaPlayer;

//TVSDK v2.5
// Create a media player
// MediaPlayer is a class that you instantiate private MediaPlayer createMediaPlayer() {
MediaPlayer mediaPlayer =
new MediaPlayer(getActivity().getApplicationContext()); return mediaPlayer;
}
```

Andere klassen die dit patroon niet volgen maar `create()` methodes in 1.4 gebruiken omvatten:

* MediaResource\
   Dit werd voorheen `MediaResource.createFromUrl()` gebruikt. Gebruik nu de constructor, die een URL, een brontype en metagegevens gebruikt. Bijvoorbeeld:

```java
//TVSDK v1.4
MediaResource playerResource = MediaResource.createFromUrl(url, getAdvertisingMetadata());
mediaPlayer.replaceCurrentItem(playerResource);

//TVSDK v2.5
MediaResource playerResource =
new MediaResource(url, MediaResource.Type.HLS, getAdvertisingMetadata());

try { mediaPlayer.replaceCurrentResource(playerResource,_mediaPlayerItemConfig);
} catch (MediaPlayerException mediaPlayerException) {
// handle exception.
}
```

* Advertentie
* AdAsset
* AdBreak

Sommige klassen (bijvoorbeeld `ContentFactory`) zijn abstracte klassen zonder openbaar beschikbare standaardimplementatie (bijvoorbeeld `DefaultContentFactory`). In deze gevallen kunt u een standaardimplementatie via een gemakfunctie verstrekken, bijvoorbeeld: `mediaPlayerItemConfig.getDefaultContentFactory()`

**Wijzigingen in ondertiteling**

De volgende wijzigingen zijn van toepassing op klassen die gerelateerd zijn aan ondertiteling:

* Bij het ophalen van Closed Caption-tracks retourneert `MediaPlayerItem.getClosedCaptionTracks()` alleen actieve tracks.
* `ClosedCaptionTrack` heeft geen  `isActive()` methode meer.

```java
//TVSDK v1.4
public List<String> getClosedCaptionTracks(String label) {
List<String> closedCaptionsTracksAsStrings = new ArrayList<String>(); MediaPlayerItem currentItem = mediaPlayer.getCurrentItem(); List<ClosedCaptionsTrack> closedCaptionsTracks =
currentItem.getClosedCaptionsTracks(); Iterator<ClosedCaptionsTrack> iterator =
closedCaptionsTracks.iterator();
if (currentItem != null) {
while (iterator.hasNext()) {
ClosedCaptionsTrack closedCaptionsTrack = iterator.next(); String isActive = closedCaptionsTrack.isActive() ? " (" + label
+ ")" : "";
closedCaptionsTracksAsStrings.add(closedCaptionsTrack.getName()
+ " : " + closedCaptionsTrack.getLanguage() + isActive);
}
}
return closedCaptionsTracksAsStrings;
}

//TVSDK v2.5
public List<String> getClosedCaptionTracks(String label) {

MediaPlayerItem currentItem = mediaPlayer.getCurrentItem(); List<ClosedCaptionsTrack> closedCaptionsTracks =
currentItem.getClosedCaptionsTracks();
Iterator<ClosedCaptionsTrack> iterator = closedCaptionsTracks.iterator();

List<String> closedCaptionsTracksAsStrings = new ArrayList<String>(); if (currentItem != null) {
while (iterator.hasNext()) {
ClosedCaptionsTrack closedCaptionsTrack = iterator.next(); closedCaptionsTracksAsStrings.
add(closedCaptionsTrack.getName() + " : ");
}
}
return closedCaptionsTracksAsStrings;
}
// Add snippet and desc for CaptionsUpdatedEventListener mediaPlayer.addEventListener(MediaPlayerEvent.CAPTIONS_UPDATED,
captionsUpdatedEventListener);

private final CaptionsUpdatedEventListener captionsUpdatedEventListener = new CaptionsUpdatedEventListener() {

@Override
public void onCaptionsUpdated(MediaPlayerItemEvent mediaPlayerItemEvent) { getActivity().findViewById(R.id.sbPlayerControlCC).setVisibility(
View.VISIBLE/*Visible*/);
}
};
```

## Wijzigingen in advertenties {#advertising-changes}

Er zijn verschillende ad-gerelateerde wijzigingen in versie 2.5.

**Wijzigingen in het reclamegedrag**

Het standaardgedrag van het afspelen van de advertentie wanneer een gebruiker een zoekactie uitvoert na een advertentiepod, verandert enigszins in v2.5. Als het ad-einde niet wordt gevolgd, wordt de advertentie afgespeeld na een zoekactie. Wanneer de app het standaard advertentiebeleid gebruikt, wordt het ad-einde verwijderd nadat het afspelen is voltooid. Als u TVSDK v2.5 gebruikt en een gebruiker achter een advertentiepod op de tijdlijn zoekt en het ad-einde niet wordt gecontroleerd, wordt geen advertentie afgespeeld.

In TVSDK v1.4 wordt echter standaard een advertentie afgespeeld in het geval van een achterwaartse zoekactie. Als u bijvoorbeeld achterwaarts zoekt tussen het derde en het vierde ad-einde, wordt standaard het derde en het derde ad-einde afgespeeld voor TVSDK v1.4.

**Wijziging van regels toevoegen**

De regels voor Advertentie worden opgegeven met behulp van een JSON-bestand. De indeling van het JSON-bestand blijft in beide versies van de TVSDK hetzelfde. In TVSDK v2.5 moet het JSON-bestand met regels voor toevoegen echter worden gehost op een locatie die toegankelijk is via een HTTP-URL. De toepassing kan een instantie van AuditudeSettings gebruiken.

```java
//TVSDK v2.5
AuditudeSettings result = new AuditudeSettings(); result.setCRSRulesJsonURL(<http url of AdobeTVSDKConfig.json>);
```

In TVSDK versie 1.4 wordt dit bestand onder de map assets in de toepassing geplaatst en wordt het bestand door TVSDK geladen.

**Fabrieksnaam wijzigen**

`AdvertisingFactory` heet nu  `ContentFactory`. Met `ContentFactory` kunt u aangepaste advertentieworkflows maken door een aantal van de methoden te overschrijven. Gebruik return null om het standaardgedrag te behouden, zoals in het volgende voorbeeld:

```java
//TVSDK v2.5
new ContentFactory() {
@Override
public AdPolicySelector retrieveAdPolicySelector(MediaPlayerItem item) { return new CustomAdPolicySelector();
}
@Override
public List<OpportunityGenerator> retrieveGenerators(MediaPlayerItem item) { return null;
}
@Override
public List<ContentResolver> retrieveResolvers(MediaPlayerItem item) { return null;
}
@Override
public List<CustomAdHandler> retrieveCustomAdPlaybackHandlers(MediaPlayerItem item) { return null;
}
};
```

**Geen lengte ad-einden**

TVSDK 2.5 voegt nullengte en onderbrekingen in als plaatsaanduidingen wanneer de advertentieserver geen advertenties retourneert.

De lengte nul en de onderbrekingen kunnen worden bepaald door het aantal advertenties op te sporen dat nul is in het advertentieeinde met behulp van de gebeurtenis onAdBreakStarted en de toepassing moet deze advertentieonderbrekingen dienovereenkomstig afhandelen.

**Wijzigingen in metagegevens**

De klasse Metadata biedt een betere vervanging voor de voormalige klasse MetadataNode.

* De klasse Metadata kan tekenreeksen, bytearrays en andere objecten Metagegevens opslaan:

```java
TVSDK v1.4
public AuditudeSettings createAdvertisementSettings() { Metadata advertisingParams = new MetadataNode();
advertisingParams.setValue("platform", Build.VERSION.RELEASE); advertisingParams.setValue("model", Build.MODEL);
AuditudeSettings adSettings = new AuditudeSettings();
// Set ad domain, zone id and media_id
...

// Set the target paramaters adSettings.setTargetingParameters(advertisingParams);

return adSettings;
}
//TVSDK v2.5
public AuditudeSettings createAdvertisementSettings() { Metadata advertisingParams = new Metadata();
advertisingParams.setValue("platform", Build.VERSION.RELEASE); advertisingParams.setValue("model", Build.MODEL);
AuditudeSettings adSettings = new AuditudeSettings();
// Set ad domain, zone id and media_id
...

// Set the target paramaters adSettings.setTargetingInfo(advertisingParams);

return adSettings;
}
```

* De `MetadataKeys` enum vervangt `DefaultMetadataKeys`. Niet alle toetsen in `DefaultMetadataKeys` zijn aanwezig in de nieuwe versie.

```java
//TVSDK v1.4
if (this.mediaPlayer != null && this.mediaPlayer.getCurrentItem() != null) { MetadataNode resourceMetadata =
(MetadataNode) this.mediaPlayer.getCurrentItem().getResource().getMetadata();
VideoAnalyticsMetadata vaMetadata = (VideoAnalyticsMetadata)
resourceMetadata.getNode(DefaultMetadataKeys.
VIDEO_ANALYTICS_METADATA_KEY.getValue());
}

//TVSDK v2.5
if (resourceMetadata.containsKey(VideoAnalyticsMetadata.
VIDEO_ANALYTICS_METADATA_KEY)) {
JSONObject vaMetadataObj =
new JSONObject(resourceMetadata.
getValue(VideoAnalyticsMetadata. VIDEO_ANALYTICS_METADATA_KEY));
vaMetadata = parseVideoAnalyticsMetadata(vaMetadataObj);
}

} catch (JSONException e) { e.printStackTrace();
}
```

* Metagegevens voor advertenties worden nu vertegenwoordigd door de klasse `AdvertisingMetadata`, een subklasse van Metagegevens, en worden nu opgeslagen in `MediaPlayerItemConfig` in plaats van `MediaResource`.

```java
//TVSDK v1.4
MetadataNode mediaMetadata = new MetadataNode();

if (stream.live) { mediaMetadata.setNode(DefaultMetadataKeys.AUDITUDE_METADATA_KEY.getValue(),
getAdSettingsForLive());
} else {
mediaMetadata.setNode(DefaultMetadataKeys.AUDITUDE_METADATA_KEY.getValue(), getAdSettingsForVod());
}
MediaResource playerResource = MediaResource.createFromUrl(url, mediaMetadata);

//TVSDK v2.5
MediaPlayerItemConfig mediaItemConfig = new MediaPlayerItemConfig(context);

if (stream.live) {
AuditudeSettings adSettings = getAdSettingsForLive(); adSettings.setLivePreroll(true); mediaItemConfig.setAdvertisingMetadata(adSettings);
} else {
// Set the advertising parameters for VOD. mediaItemConfig.setAdvertisingMetadata(getAuditudeSettingsForVod());
}

// Create advertising metadata node Metadata mediaMetadata = new Metadata();

// Asset Url
MediaResource playerResource =
new MediaResource(url, MediaResource.Type.HLS, mediaMetadata);
try {
mediaPlayer.replaceCurrentResource(playerResource, mItemConfig);
} catch (MediaPlayerException mediaPlayerException) {
//handle exception.
}
```

Metagegevens over netwerkconfiguratie, die voorheen lid waren van de klasse `MediaResource`, worden nu vertegenwoordigd door de klasse `NetworkConfiguration` en worden nu opgeslagen in `MediaPlayerItemConfig` in plaats van `MediaResource`.

```java
//TVSDK v1.4
MediaResource playerResource = MediaResource.createFromUrl(url, mediaMetadata);
...

//TVSDK v2.5
MediaPlayerItemConfig mediaItemConfig = new MediaPlayerItemConfig(context);

NetworkConfiguration mediaNetworkConfiguration = mediaItemConfig.getNetworkConfiguration();
```

**Wijzigingen in getimede metagegevens parseren**

De parsering van `TimedMetadata` is in 2.5 gewijzigd ten opzichte van de datatypen voor het parseren van ID3-tag.

```java
//TVSDK v1.4
public void onTimedMetadata(TimedMetadata timedMetadata) { TimedMetadata.Type type = timedMetadata.getType();
if (type.equals(TimedMetadata.Type.ID3)){ PMPDemoApp.logger.i(LOG_TAG + "#onTimedMetadata",
"New ID3 tag detected at time = " + timedMetadata.getTime());
Metadata metadata = timedMetadata.getMetadata(); Set<String> keys = metadata.keySet();
for (String key : keys) {
String value = metadata.getValue(key); PMPDemoApp.logger.i(LOG_TAG + "#onTimedMetadata",
"Key = " + key + " Value = " + value);
}
} else if (_mediaPlayer.getPlaybackRange() != null &&
_mediaPlayer.getPlaybackRange().getDuration() > 0) { displayRanges();
PMPDemoApp.logger.i(LOG_TAG +
"#onTimedMetadata",
"New timed metadata. Name " + timedMetadata.getName() +
", time " + timedMetadata.getTime() + ", id " + timedMetadata.getId() + ", metadata " +
timedMetadata.getMetadata() + ".");
/*if (!_timedMetadataList.contains(timedMetadata)) {
_timedMetadataList.add(timedMetadata);
}*/
/* scte35 */
if (timedMetadata.getName().equalsIgnoreCase("#EXT-OATCLS-SCTE35")) { parseSCTE35Tag(timedMetadata);
}
}
}

//TVSDK v2.5
public void onTimedMetadata(TimedMetadataEvent timedMetadataEvent) { PMPDemoApp.logger.i(LOG_TAG + " inside"," ontimedmetadata"); TimedMetadata timedMetadata = timedMetadataEvent.getTimedMetadata();

TimedMetadata.Type type = timedMetadata.getType(); if (type.equals(TimedMetadata.Type.ID3)) {
PMPDemoApp.logger.i(LOG_TAG +
"#onTimedMetadata",
"New ID3 tag detected at time = " + timedMetadata.getTime());
Metadata metadata = timedMetadata.getMetadata();
if (metadata != null) { PMPDemoApp.logger.i(LOG_TAG +
"::expandID3Metadata", "isEmpty " + metadata.isEmpty());
Set<String> keys = metadata.keySet(); PMPDemoApp.logger.i(LOG_TAG + "::expandID3Metadata",
"No of keys=" + keys.size());
String s;
for (String key : keys) {
byte[] value = metadata.getByteArray(key); s = new String(value);
if (key.equalsIgnoreCase("APIC"))
s = "SUPPRESSING BINARY DATA FOR ATTACHED PICTURE.";
PMPDemoApp.logger.i(LOG_TAG + "::expandID3Metadata",
"Key=" + key + ", Length=" + value.length + ", Value=" + s.trim());
}
}
} else if (_mediaPlayer.getPlaybackRange() != null &&
_mediaPlayer.getPlaybackRange().getDuration() > 0) { displayRanges();
PMPDemoApp.logger.i(LOG_TAG +
"#onTimedMetadata",
"New timed metadata. Name " + timedMetadata.getName() +
", time " + timedMetadata.getTime() + ", id " + timedMetadata.getId() + ", metadata " +
timedMetadata.getMetadata() + ".");
/*if (!_timedMetadataList.contains(timedMetadata)) {
_timedMetadataList.add(timedMetadata);
}*/
/* scte35 */
if (timedMetadata.getName().equalsIgnoreCase("#EXT-OATCLS-SCTE35")) { PMPDemoApp.logger.i(LOG_TAG +
" inside ontimedmetadata"," ext"); parseSCTE35Tag(timedMetadata);
}
}
}
```

**Overige wijzigingen**

De volgende aanvullende wijzigingen zijn beschikbaar in versie 2.5:

* De methode `notifyClick()` is verplaatst van `MediaPlayerView` naar `MediaPlayer`.

* `AdPolicySelector` is een interface, geen klasse. Alle methoden implementeren.
* `AdPolicyInfo` bevat nu een lijst van  `AdBreakTimelineItem`, niet  `AdBreakPlacement`.

* De API-naam van de abstracte klasse `ContentResolver` wordt gewijzigd.
* `PlacementOpportunityDetector` is niet meer beschikbaar. In plaats daarvan breidt u de abstracte klasse `OpportunityGenerator` uit. De voorbeeldimplementatie is hiervan een voorbeeld.

* De parameters van de constructor `AdBreakPlacement` zijn hetzelfde, maar in een andere volgorde. Voor een steekproefimplementatie, zie de implementatie van de Speler van de Verwijzing die met het product wordt gebundeld.

## Wijzigingen in DRM {#changes-in-drm}

De meeste wijzigingen in deze versie bevinden zich in de DRM-laag. In de volgende tabel staan aanvullende wijzigingen tussen versies 1.4 en 2.5:

| DRMManager, methode | Terugbellen met succes in 1.4 | Fout bij terugbellen in 1.4 | Listener in 2.5 |
|--- |--- |--- |--- |
| verwervingLicense | DRMLicenseAcquiredCallback | DRMOperationErrorCallback | DRMAcquireLicenseListener |
| verwervingPreviewLicense | DRMLicenseAcquiredCallback | DRMOperationErrorCallback | DRMAcquireLicenseListener |
| authenticate | DRMAuthenticationCompleteCallback | DRMOperationErrorCallback | DRMAuthenticateListener |
| createMetadataFromBytes | NA | DRMOperationErrorCallback | DRMErrorListener |
| initialiseren | DRMOperationCompleteCallback | DRMOperationErrorCallback | DRMOperationCompleteListener |
| joinLicenseDomain | DRMOperationCompleteCallback | DRMOperationErrorCallback | DRMOperationCompleteListener |
| leaveLicenseDomain | DRMOperationCompleteCallback | DRMOperationErrorCallback | DRMOperationCompleteListener |
| resetDRM | DRMOperationCompleteCallback | DRMOperationErrorCallback | DRMOperationCompleteListener |
| returnLicense | DRMLicenseReturnCompleteCallback | DRMOperationErrorCallback | DRMReturnLicenseListener |
| setAuthenticationToken | DRMOperationCompleteCallback | DRMOperationErrorCallback | DRMOperationCompleteListener |
| storeLicenseBytes | DRMOperationCompleteCallback | DRMOperationErrorCallback | DRMOperationCompleteListener |

```java
//TVSDK 1.4
private final MediaPlayer.DRMEventListener _drmEventListener = new MediaPlayer.DRMEventListener() {

@Override
public void onDRMMetadata(final DRMMetadataInfo drmMetadataInfo) { PMPDemoApp.logger.i(LOG_TAG + "::MediaPlayer.DRMEventListener#onDRMMetadata",
"DRM metadata available: " + drmMetadataInfo + ".");
if (getSuppressAutoPlayPreference() && drmMetadataInfo != null) {
// if suppress play setting, then the user is a tester who
// wishes to manually intervene between the metadata available
// event and the play event, so launch the metadata interface
// and give it the loaded metadata bytes, but only once
_drmMetadata = drmMetadataInfo.getDRMMetadata();
}
if (drmMetadataInfo == null ||
!DRMHelper.isAuthNeeded(drmMetadataInfo.getDRMMetadata())) { PMPDemoApp.logger.i(LOG_TAG + "#onDRMMetadata", "DRM auth is not needed."); return;
}
// Perform DRM auth.
// Possible logic might take into consideration a threshold
// between the current player time and the DRM metadata start
// time. For the time being, we resolve it as soon as we receive
// the DRM metadata.

DRMManager drmManager = _mediaPlayer.getDRMManager(); if (drmManager == null) {
PMPDemoApp.logger.e(LOG_TAG + "#onDRMMetadata", "DRMManager is null."); return;
}
SharedPreferences sharedPreferences =
PreferenceManager.getDefaultSharedPreferences(getActivity()); String authUser =
sharedPreferences.getString(PMPDemoApp.SETTINGS_DRM_USERNAME,
getResources().getString(R.string.drmUsername));
String authPass = sharedPreferences.getString(PMPDemoApp.SETTINGS_DRM_PASSWORD,
getResources().getString(R.string.drmPassword));
DRMHelper.performDrmAuthentication(drmManager,
drmMetadataInfo.getDRMMetadata(), authUser,
authPass,
new DRMAuthenticationListener() {
@Override
public void onAuthenticationStart() { PMPDemoApp.logger.i(LOG_TAG + "#onAuthenticationStart",
"DRM authentication started for DRM metadata at [" + drmMetadataInfo.getPrefetchTimestamp() + "].");
}
@Override
public void onAuthenticationError(long majorCode,
long minorCode, Exception e) {
if (getActivity() == null) { return;
}
PMPDemoApp.logger.e(LOG_TAG +
"#onAuthenticationError",
"DRM authentication failed. " + majorCode + " 0x" + Long.toHexString(minorCode));
_handler.post(new Runnable() {
@Override
public void run() { showToast(getString(R.string.drmAuthenticationError)); getActivity().finish();
}
});
}
@Override
public void onAuthenticationComplete(byte[] authenticationToken) { PMPDemoApp.logger.i(LOG_TAG +
"#onAuthenticationComplete",
"Auth successful for DRM metadata at [" + drmMetadataInfo.getPrefetchTimestamp() + "].");
}
});
}
};

//TVSDK 2.5
private final DRMMetadataInfoEventListener drmMetadataInfoEventListener = new DRMMetadataInfoEventListener() {
@Override
public void onDRMMetadataInfo(DRMMetadataInfoEvent drmMetadataInfoEvent) { final DRMMetadataInfo drmMetadataInfo =
drmMetadataInfoEvent.getDRMMetadataInfo();
PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.DRMEventListener#onDRMMetadata",
"DRM metadata available: " + drmMetadataInfo + ".");
if (getSuppressAutoPlayPreference() && drmMetadataInfo != null) {
// if suppress play setting, then the user is a tester who
// wishes to manually intervene between the metadata
// available event and the play event, so launch the
// metadata interface and give it the loaded metadata
// bytes, but only once
drmMetadata = drmMetadataInfo.getDRMMetadata();
}
if (drmMetadataInfo ==
null || !DRMHelper.isAuthNeeded(drmMetadataInfo.getDRMMetadata())) { PMPDemoApp.logger.i(LOG_TAG +
"#onDRMMetadata",
"DRM auth is not needed.");
return;
}
// Perform DRM auth.
// Possible logic might take into consideration a threshold between
// the current player time and the DRM metadata start time. For the
// time being, we resolve it as soon as we receive the DRM metadata.

DRMManager drmManager = _mediaPlayer.getDRMManager(); if (drmManager == null) {
PMPDemoApp.logger.e(LOG_TAG +
"#onDRMMetadata", "DRMManager is null.");
return;
}

SharedPreferences sharedPreferences = PreferenceManager.getDefaultSharedPreferences(getActivity());
String authUser = sharedPreferences.getString(PMPDemoApp.SETTINGS_DRM_USERNAME,
getResources().getString(R.string.drmUsername));
String authPass = sharedPreferences.getString(PMPDemoApp.SETTINGS_DRM_PASSWORD,
getResources().getString(R.string.drmPassword));
DRMHelper.performDrmAuthentication(drmManager,
drmMetadataInfo.getDRMMetadata(), authUser,
authPass,
new DRMAuthenticationListener() {
@Override
public void onAuthenticationStart() { PMPDemoApp.logger.i(LOG_TAG +
"#onAuthenticationStart",
"DRM authentication started for DRM metadata at [" + drmMetadataInfo.getPrefetchTimestamp() + "].");
}
@Override
public void onAuthenticationError(int major,
int minor,
String erroString, String serverErrorURL) {
if (getActivity() == null) { return;
}
PMPDemoApp.logger.e(LOG_TAG +
"#onAuthenticationError",
"DRM authentication failed. " + major +
" 0x" +
Long.toHexString(minor));
_handler.post(new Runnable() {
@Override
public void run() { showToast(getString(R.string.drmAuthenticationError)); getActivity().finish();
}
});
}
@Override
public void onAuthenticationComplete(byte[] authenticationToken) { PMPDemoApp.logger.i(LOG_TAG +
"#onAuthenticationComplete",
"Auth successful for DRM metadata at [" + drmMetadataInfo.getPrefetchTimestamp() + "].");
}
});
}
};
```

De statische `DRMManager`-instantie die beschikbaar was in 1.4 nadat mediaplayer is gemaakt, is nu beschikbaar nadat de gebeurtenislistener `onDRMMetadataInfo` is geactiveerd.

## Wijzigingen met betrekking tot adaptieve bitsnelheid (ABR) {#adaptive-bitrate-abr-related-changes}

**Wijzigingen in constanten**

Veel constanten zijn van type veranderd van `String` in `int`. Bijvoorbeeld: `MediaResourceType`, `ABRControlParameters` en `MediaPlayerStatusChangeEvent`.

```java
//TVSDK v1.4
ABRControlParameters
private void setAbrControlParams() { SharedPreferences sharedPreferences =
PreferenceManager.getDefaultSharedPreferences(getActivity());
if (sharedPreferences.getBoolean(PMPDemoApp.SETTINGS_ABR_CTRL_ENABLED,
PMPDemoApp.DEFAULT_ABR_ENABLED)) {
int initialBitRate = getIntPreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_INITIAL_BITRATE, 0);
int minBitRate = getIntPreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_MIN_BITRATE, 0);
int maxBitRate = getIntPreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_MAX_BITRATE, PMPDemoApp.DEFAULT_MAX_BIT_RATE);
int mbrPolicyAsInt =
getIntPreference(sharedPreferences, PMPDemoApp.SETTINGS_ABR_POLICY, 0); ABRControlParameters.ABRPolicy abrPolicy = policyFromInt(mbrPolicyAsInt); abrPolicy = abrPolicy != null ?
abrPolicy : ABRControlParameters.ABRPolicy.ABR_MODERATE;
_mediaPlayer.setABRControlParameters(new ABRControlParameters(initialBitRate,
minBitRate, maxBitRate, abrPolicy));
}
}

//TVSDK v2.5
ABRControlParameters
private void setAbrControlParams() { ABRControlParametersBuilder abrBuilder =
new ABRControlParametersBuilder();

if (sharedPreferences.getBoolean(PMPDemoApp.SETTINGS_ABR_CTRL_ENABLED, PMPDemoApp.DEFAULT_ABR_ENABLED)) {

abrBuilder.setInitialBitRate(getIntPreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_INITIAL_BITRATE,
ABRControlParameters.DEFAULT_ABR_INITIAL_BITRATE)); abrBuilder.setMinBitRate(getIntPreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_MIN_BITRATE,
ABRControlParameters.DEFAULT_ABR_MIN_BITRATE)); abrBuilder.setMaxBitRate(getIntPreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_MAX_BITRATE,
ABRControlParameters.DEFAULT_ABR_MAX_BITRATE)); abrBuilder.setMaxPlayoutRate(getDoublePreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_MAX_PLAYOUT_RATE,
ABRControlParameters.DEFAULT_MAX_PLAYOUT_RATE)); abrBuilder.setMinTrickPlayBitRate(getIntPreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_MIN_TRICKPLAY_BITRATE,
ABRControlParameters.DEFAULT_ABR_MIN_BITRATE)); abrBuilder.setMaxTrickPlayBitRate(getIntPreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_MAX_TRICKPLAY_BITRATE,
ABRControlParameters.DEFAULT_ABR_MAX_BITRATE)); abrBuilder.setMaxTrickPlayBandwidthUsage(getIntPreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_MAX_TRICKPLAY_BANDWIDTH,
ABRControlParameters.DEFAULT_ABR_MAX_BITRATE));

switch (getIntPreference(sharedPreferences, PMPDemoApp.SETTINGS_ABR_POLICY, -1)) {
case 0: abrBuilder.setPolicy(ABRControlParameters.ABRPolicy.ABR_CONSERVATIVE); break;
case 1: abrBuilder.setPolicy(ABRControlParameters.ABRPolicy.ABR_MODERATE); break;
case 2: abrBuilder.setPolicy(ABRControlParameters.ABRPolicy.ABR_AGGRESSIVE); break;
default: abrBuilder.setPolicy(ABRControlParameters.DEFAULT_ABR_POLICY);
}
}
_mediaPlayer.setABRControlParameters(abrBuilder.toABRControlParameters());
}
```

**Wijzigingen in de constructor ABRControlParameters**

Sommige parameters zijn toegevoegd, sommige hebben een andere naam gekregen en sommige zijn verplaatst. Hieronder ziet u de constructorhandtekening in v1.4 en de nieuwe handtekening in 2.5:

```java
//TVSDK v1.4
public ABRControlParameters(ABRPolicy abrPolicy,
int nInitialBitRate, int nMinBitRate,
int nMaxBitRate)

//TVSDK v2.5
public ABRControlParameters(int nInitialBitRate,
int nMinBitRate, int nMaxBitRate,
ABRPolicy abrPolicy,
int nMinTrickPlayBitRate, int nMaxTrickPlayBitRate,
int nMaxTrickPlayBandwidthUsage, double dMaxPlayoutRate)
```

## Foutgebeurtenissen en verwerking {#error-events-and-handling}

**Wijzigingen in foutafhandeling**

De klasse `MediaError` is vervangen door de klasse `Notification`. Het enige verschil tussen de klassen `MediaError` en `Notification` is dat laatstgenoemde geen beschrijvingsattribuut bevat. De TVSDK 1.4-foutcodes met de waarden 101xxx, 102xxx, 104xxx, 106xxx, 107xxx, 109xxx bestaan niet in TVSDK 2.5. Voor de playbackcodes in TVSDK 2.5, zie [Native Fout - videoplaybackwaarden](assets/psdk_android_2.5.pdf).

Hieronder volgen voorbeelden van foutafhandeling in TVSDK 1.4 en 2.5:

```java
//TVSDK v1.4
@Override
public void onStateChanged(MediaPlayer.PlayerState state, MediaPlayerNotification notification) {
PMPDemoApp.logger.i(LOG_TAG + "::MediaPlayer.PlayerStateEventListener#onStateChanged()", "Player state changed to [" + state
+ "].");

switch (state) {
// Non recoverable state - either reset player and reinitialize
// or release the player and create a new one.
case ERROR: PMPDemoApp.logger.e(LOG_TAG +
"::MediaPlayer.PlayerStateEventListener#onStateChanged()", "Error: " + notification + "."); getActivity().finish();
break;
default:
// do nothing
}
}

//TVSDK v2.5
private final StatusChangeEventListener statusChangeEventListener = new StatusChangeEventListener() {
@Override
public void onStatusChanged(MediaPlayerStatusChangeEvent mediaPlayerStatusChangeEvent)
{
MediaPlayerStatus state = mediaPlayerStatusChangeEvent.getStatus(); PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.PlayerStateEventListener#onStateChanged()", "Player state changed to [" + state
+ "].");
switch (state) {
// Non recoverable state - either reset player and reinitialize
// or release the player and create a new one.
case ERROR:
PMPDemoApp.logger.e(LOG_TAG + "::MediaPlayer.PlayerStateEventListener#onStateChanged()", "Error: ");
printErrorMetadata(mediaPlayerStatusChangeEvent.getMetadata()); showToast("MediaPlayer status ERROR: Look at the logs for details"); getActivity().finish();
break;
default:
// do nothing
}
}
};
```

Alle herstelbare fouten worden behandeld als waarschuwingen en worden behandeld met de `NotificationEventListener` in TVSDK 2.5. De waarschuwingen worden als meldingen weergegeven met de listener `onOperationFailed` in de QOS-handler in TVSDK 1.4, waarbij de melding een aparte gebeurtenis is, net als in TVSDK 2.5. De in de punten 1.4 en 2.5 behandelde waarschuwing ziet er als volgt uit:

```java
//TVSDK v1.4
private final MediaPlayer.QOSEventListener _qosEventListener = new MediaPlayer.QOSEventListener()
{
@Override
public void onBufferStart() {
PMPDemoApp.logger.i(LOG_TAG + "::MediaPlayer.QOSEventListener#onBufferStart()", "Buffering started.");
}
@Override
public void onBufferComplete() {
PMPDemoApp.logger.i(LOG_TAG + "::MediaPlayer.QOSEventListener#onBufferComplete()", "Buffering complete.");
}
@Override
public void onSeekStart() {
PMPDemoApp.logger.i(LOG_TAG + "::MediaPlayer.QOSEventListener#onSeekStart()", "Seek starting.");
}
@Override
public void onSeekComplete(long adjustedTime) {
PMPDemoApp.logger.i(LOG_TAG + "::MediaPlayer.QOSEventListener#onSeekComplete()", "Seek complete at position: " + adjustedTime + ".");
}
@Override
public void onLoadInfo(LoadInfo loadInfo) {
PMPDemoApp.logger.i(LOG_TAG + "::MediaPlayer.QOSEventListener#onLoadInfo()", "Url: " + loadInfo.getUrl() + ", size: "
+ loadInfo.getSize() + " bytes, media duration: " + loadInfo.getMediaDuration() + "ms, download duration: " + loadInfo.getDownloadDuration() + "ms");
}
@Override
public void onOperationFailed(MediaPlayerNotification.Warning warning) {

StringBuffer sb = new StringBuffer("Player operation failed: "); sb.append(warning.getCode()).append(" - ").append(warning.getDescription()); if (warning.getMetadata() != null) {
sb.append("Warning metadata: ").append(warning.getMetadata().toString());
}

MediaPlayerNotification innerNotification = warning.getInnerNotification(); registerFailedAudioTrackIndex(innerNotification); handleFailedSeekEvent(innerNotification);

while (innerNotification != null) { sb.append("Inner notification: ");
sb.append(innerNotification.getCode()).append(" - ").append(innerNotification.getDescription());
Metadata metadata = innerNotification.getMetadata(); if (metadata != null) {
for (String key : metadata.keySet()) { sb.append(" - ").append

//TVSDK v2.5
private final NotificationEventListener notificationEventListener = new NotificationEventListener() {
/**
* An example of dumping the information within a Notification. Here, we don't handle the event in
* any way except to print a log message.
* @param event The NotificationEvent
*/
@Override
public void onNotification(NotificationEvent event) { Notification notification = event.getNotification(); Notification.Type type = notification.getType(); StringBuilder sb = new StringBuilder(); sb.append("[").append(type).append("]");
sb.append(" Player operation failed (").append(notification.getCode()).append(")"); Metadata metadata = notification.getMetadata();
if (metadata != null)
{
for (String key : metadata.keySet())
{
sb.append(", ").append(key).append(" = ").append(metadata.getValue(key));
}
}
Notification inner = notification.getInnerNotification(); if (inner != null) {
sb.append(" :: Inner Notification [").append(inner.getType()).append("](").append(inner.getCode()).append(")");
Metadata innerMetadata = inner.getMetadata(); if (innerMetadata != null) {
for (String iKey : innerMetadata.keySet()) { sb.append(", ").append(iKey).append(" =
").append(innerMetadata.getValue(iKey));
}
}
}
switch(type)
{
case ERROR:
PMPDemoApp.logger.e(LOG_TAG, sb.toString()); break;
case WARNING:
PMPDemoApp.logger.w(LOG_TAG, sb.toString()); break;
default:
PMPDemoApp.logger.i(LOG_TAG, sb.toString()); break;
}
showToast(sb.toString()); PMPDemoApp.logger.d(LOG_TAG, sb.toString());
}
};
```

**Nieuwe uitzonderingen**

Terwijl TVSDK v1.4 een combinatie nulls, foutenwinst, en een verscheidenheid van uitzonderingen ( `MediaPlayerException`, `IllegalStateException`, en `IllegalArgumentException`) gebruikte, TVSDK v2.5 `generatesMediaPlayerException` voor alle fouten.

>[!NOTE]
>
>Om details op een MediaPlayerException te krijgen, kunt u `getErrorCode()` gebruiken.

Hieronder ziet u een voorbeeld van de wijziging:

```java
//TVSDK v1.4
public void setBufferControlParams() { try {
mediaPlayer.setBufferControlParameters(getBufferParamsFromSettings());
} catch (IllegalArgumentException e) { PrimetimeReference.logger.w(LOG_TAG +
"#setBufferControlParams",
"Unable to apply buffering params: " + e.getMessage() + ".");
}
}

//TVSDK v2.5
public void setBufferControlParams() { try {
mediaPlayer.setBufferControlParameters(getBufferParamsFromSettings());
} catch (MediaPlayerException e) { PrimetimeReference.logger.w(LOG_TAG + "#setBufferControlParams", "Unable to apply buffering params: " + e.getMessage() + ".");
}
}
```

## Wijzigingen in QOS-parameters {#changes-to-qos-parameters}

Er zijn kleine veranderingen in QOSProvider objecten eigenschappen:

* De `TimeToFirstFrame` is niet beschikbaar in TVSDK 2.5.
* TVSDK 2.5 QOSProvider heeft een nieuw bezit om de waargenomen bandbreedte tijdens een het stromen zitting te bepalen.

```java
//TVSDK v1.4
public void updateQosInformation(PlaybackInformation playbackInformation) { if (playbackInformation == null) {
return;
}
setQosItem("Frame rate", (int) playbackInformation.getFrameRate() +
" (" + (int) playbackInformation.getDroppedFrameCount() + " dropped)"); setQosItem("Bitrate", (int) playbackInformation.getBitrate()); setQosItem("Buffering time", (long) playbackInformation.getBufferingTime()); setQosItem("Buffer length", (long) playbackInformation.getBufferLength()); setQosItem("Buffer time", (long) playbackInformation.getBufferTime()); setQosItem("Empty buffer count", (int) playbackInformation.getEmptyBufferCount()); setQosItem("Time to load", (int) playbackInformation.getTimeToLoad()); setQosItem("Time to start", (int) playbackInformation.getTimeToStart()); setQosItem("Time to first frame", (int) playbackInformation.getTimeToFirstFrame()); setQosItem("Time to prepare", (int) playbackInformation.getTimeToPrepare()); setQosItem("Last seek time", (int) playbackInformation.getLastSeekTime());
}

//TVSDK v2.5
public void updateQosInformation(PlaybackInformation playbackInformation) { if (playbackInformation == null) {
return;
}
setQosItem("Frame rate", (int) playbackInformation.getFrameRate() +
" (" + (int) playbackInformation.getDroppedFrameCount() + " dropped)"); setQosItem("Bitrate", (int) playbackInformation.getBitRate()); setQosItem("Buffering time", (long) playbackInformation.getBufferingTime()); setQosItem("Buffer length", (long) playbackInformation.getBufferLength()); setQosItem("Buffer time", (long) playbackInformation.getBufferTime()); setQosItem("Empty buffer count", (int) playbackInformation.getEmptyBufferCount()); setQosItem("Time to load", (int) playbackInformation.getTimeToLoad()); setQosItem("Time to start", (int) playbackInformation.getTimeToStart());
setQosItem("Time to prepare", (int) playbackInformation.getTimeToPrepare());
setQosItem("Perceived Bandwidth", (int) playbackInformation.getPerceivedBandwidth());
```

* De `QOSEventListener::onOperationFailed()` bestaat niet meer in TVSDK 2.5. De waarschuwingen die voorheen in deze gebeurtenislistener werden weergegeven, worden nu weergegeven in de gebeurtenislistener `NotificationEventListener::onNotification()`.

* `QOSProvider event listeners onBufferStart()`, `onBufferComplete()`, `onSeekStart()`, `onSeekComplete()`, en `onLoadInfo()` zijn individuele gebeurtenisluisteraars die met een mediaPlayer instantie worden gebonden.

```java
//TVSDK v1.4
private final MediaPlayer.QOSEventListener _qosEventListener = new MediaPlayer.QOSEventListener() {

@Override
public void onBufferStart() { PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.QOSEventListener#onBufferStart()", "Buffering started.");
showBufferingSpinner();
}
@Override
public void onBufferComplete() { PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.QOSEventListener#onBufferComplete()", "Buffering complete.");
hideBufferingSpinner();
}
@Override
public void onSeekStart() { PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.QOSEventListener#onSeekStart()", "Seek starting.");
inTrickPlayMode = false;
}
@Override
public void onSeekComplete(long adjustedTime) { PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.QOSEventListener#onSeekComplete()", "Seek complete at position: " +
adjustedTime + ".");
_controlBar.setPosition(adjustedTime);
if (adjustedTime == _mediaPlayer.getPlaybackRange().getEnd() &&
_mediaPlayer.getStatus() == MediaPlayer.PlayerState.COMPLETE) {
// Show the replay button. showReplayButton();
}
if (_mediaPlayer.getStatus() == MediaPlayer.PlayerState.PAUSED) {
// Show the pause icon.
_controlBar.pause();
}
}
@Override
public void onLoadInfo(LoadInfo loadInfo) { PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.QOSEventListener#onLoadInfo()", "Url: " +
loadInfo.getUrl() + ", size: " + loadInfo.getSize() +
" bytes, media duration: " +
loadInfo.getMediaDuration() + "ms, download duration: " +
loadInfo.getDownloadDuration() + "ms");
 
public void onOperationFailed(MediaPlayerNotification.Warning warning) {

StringBuffer sb = new StringBuffer("Player operation failed: "); sb.append(warning.getCode()).append(" - ").append(warning.getDescription()); if (warning.getMetadata() != null) {
sb.append("Warning metadata: ").append(warning.getMetadata().toString());
}

MediaPlayerNotification innerNotification = warning.getInnerNotification(); registerFailedAudioTrackIndex(innerNotification); handleFailedSeekEvent(innerNotification);

while (innerNotification != null) { sb.append("Inner notification: ");
sb.append(innerNotification.getCode()).append(" - "). append(innerNotification.getDescription());
Metadata metadata = innerNotification.getMetadata(); if (metadata != null) {
for (String key : metadata.keySet()) { sb.append(" - ").append(key).append(": ").
append(metadata.getValue(key));
}
}
innerNotification = innerNotification.getInnerNotification();
}
String errMsg = sb.toString(); PMPDemoApp.logger.w(LOG_TAG +
"::MediaPlayer.QOSEventListener#onOperationFailed()", errMsg);
showToast(errMsg);
}
};

//TVSDK v2.5
mediaPlayer.addEventListener(MediaPlayerEvent.LOAD_INFORMATION_AVAILABLE,
loadInfoEventListener); mediaPlayer.addEventListener(MediaPlayerEvent.BUFFERING_BEGIN,
bufferingBeginEventListener); mediaPlayer.addEventListener(MediaPlayerEvent.BUFFERING_END,
bufferingEndEventListener); mediaPlayer.addEventListener(MediaPlayerEvent.SEEK_BEGIN,
seekBeginEventListener); mediaPlayer.addEventListener(MediaPlayerEvent.SEEK_END,
seekEndEventListener);
// Buffering events.
BufferingBeginEventListener bufferingBeginEventListener = new BufferingBeginEventListener() {
@Override
public void onBufferingBegin(BufferEvent bufferEvent) { PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.QOSEventListener#onBufferStart()", "Buffering started.");
showBufferingSpinner();
}
};

BufferingEndEventListener bufferingEndEventListener = new BufferingEndEventListener() {
@Override
public void onBufferingEnd(BufferEvent bufferEvent) { PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.QOSEventListener#onBufferComplete()",
"Buffering complete."); hideBufferingSpinner();
}
};

BufferPreparedEventListener bufferPreparedEventListener = new BufferPreparedEventListener() {
@Override
public void onBufferPrepared() {
}
};
// seek events.
SeekBeginEventListener seekBeginEventListener = new SeekBeginEventListener() {

@Override
public void onSeekBegin(SeekEvent seekEvent) { PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.QOSEventListener#onSeekStart()", "Seek starting.");
inTrickPlayMode = false;
}
};
SeekEndEventListener seekEndEventListener = new SeekEndEventListener() {
@Override
public void onSeekEnd(SeekEvent seekEvent) {
double adjustedTime = seekEvent.getActualPosition();
PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.QOSEventListener#onSeekComplete()", "Seek complete at position: " + adjustedTime + ".");
_controlBar.setPosition((long) adjustedTime);
if (adjustedTime == _mediaPlayer.getPlaybackRange().getEnd() &&
_mediaPlayer.getStatus() == MediaPlayerStatus.COMPLETE) {
// Show the replay button. showReplayButton();
}
if (_mediaPlayer.getStatus() == MediaPlayerStatus.PAUSED) {
// Show the pause icon.
_controlBar.pause();
}
}
};
/**
* LoadInformationEventListener that intercepts PSDK load info events
*/
private final LoadInformationEventListener loadInfoEventListener = new LoadInformationEventListener() {

@Override
public void onLoadInformation(LoadInformationEvent event) { LoadInformation loadInfo = event.getLoadInfomation(); PMPDemoApp.logger.i(
LOG_TAG + "::LoadInformationEventListener#onLoadInfomation()", "Url: " + loadInfo.getUrl() + ", size: "
+ loadInfo.getSize()
+ " bytes, download duration: "
+ loadInfo.getDownloadDuration() + "ms");
}
};
```

## Nuttige bronnen {#helpful-resources}

* Zie de volledige Help-documentatie op de pagina [Adobe Primetime Learn &amp; Support](https://helpx.adobe.com/support/primetime.html).