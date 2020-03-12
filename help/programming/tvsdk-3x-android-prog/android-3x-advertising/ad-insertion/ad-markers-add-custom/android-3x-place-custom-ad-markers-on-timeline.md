---
description: In dit voorbeeld wordt aangegeven hoe u aangepaste en markeertekens op de afspeeltijdlijn kunt opnemen.
seo-description: In dit voorbeeld wordt aangegeven hoe u aangepaste en markeertekens op de afspeeltijdlijn kunt opnemen.
seo-title: Aangepaste markeertekens op de tijdlijn plaatsen
title: Aangepaste markeertekens op de tijdlijn plaatsen
uuid: 47e31a97-e5da-46f3-bdcc-327c159c4355
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Aangepaste markeertekens op de tijdlijn plaatsen {#place-custom-ad-markers-on-the-timeline}

In dit voorbeeld wordt aangegeven hoe u aangepaste en markeertekens op de afspeeltijdlijn kunt opnemen.

1. Vertaal de out-of-band ad-positioneringsinformatie in een lijst/serie van `RepaceTimeRange` klasse.
1. Maak een instantie van een `CustomRangeMetadata` klasse en gebruik de `setTimeRangeList` methode ervan met de lijst/array als argument om de lijst met tijdbereiken in te stellen.
1. Gebruik de `setType` methode om het type in te stellen op `MARK_RANGE`.
1. Gebruik de `MediaPlayerItemConfig.setCustomRangeMetadata` methode met de `CustomRangeMetadata` instantie als argument om de metagegevens voor het aangepaste bereik in te stellen.
1. Gebruik de `MediaPlayer.replaceCurrentResource` methode met de `MediaPlayerItemConfig` instantie als argument om de nieuwe bron in te stellen als de huidige bron.
1. Wacht op een `STATE_CHANGED` gebeurtenis, die meldt dat de speler zich in de `PREPARED` toestand bevindt.
1. Start het afspelen van video door `MediaPlayer.play`te bellen.

Hier volgt het resultaat van het voltooien van de taken in dit voorbeeld:

* Als een `ReplaceTimeRange` ander element op de afspeeltijdlijn overlapt, bijvoorbeeld, `ReplaceTimeRange` is de beginpositie van een object eerder dan een reeds geplaatste eindpositie, wordt door TVSDK het begin van de beledigende gebeurtenis stilletjes aangepast `ReplaceTimeRange` om het conflict te voorkomen.

   Hierdoor is de aanpassing `ReplaceTimeRange` korter dan oorspronkelijk opgegeven. Als de aanpassing tot een duur van nul leidt, laat TVSDK de overtreding stil vallen `ReplaceTimeRange`.

* TVSDK zoekt naar aangrenzende tijdbereiken voor aangepaste toevoegingen en voegt deze in afzonderlijke ad-einden samen.

Tijdbereiken die zich niet naast een ander tijdbereik bevinden, worden omgezet in ad-hocafbrekingen die één advertentie bevatten.

* Als de toepassing probeert om een media middel te laden de waarvan configuratie bevat `CustomRangeMetadata` die slechts in de tellers van de contextdouane kan worden gebruikt en, werpt TVSDK een uitzondering als het onderliggende element niet van type VOD is.

* Wanneer u werkt met aangepaste advertentiemarkeringen, deactiveert TVSDK andere ad-resolving mechanismen (bijvoorbeeld Adobe Primetime en besluitvorming).

   U kunt elke TVSDK-ad-resolver-module of het aangepaste ad-markeermechanisme gebruiken. Wanneer u aangepaste advertentiemarkeringen gebruikt, wordt de advertentie-inhoud beschouwd als zijnde opgelost en op de tijdlijn geplaatst.

In het volgende codefragment worden drie tijdbereiken op de tijdlijn geplaatst als aangepaste advertentiemarkeringen.
>```java>
>// Assume that the 3 time ranges are obtained through external means 
// Use them to populate the ReplaceTimeRange instance 
List<ReplaceTimeRange> timeRanges = new ArrayList<ReplaceTimeRange>(); 
timeRanges.add(new ReplaceTimeRange(0,10000, 0)); 
timeRanges.add(new ReplaceTimeRange(15000,20000, 0)); 
timeRanges.add(new ReplaceTimeRange(25000,30000, 0)); 

CustomRangeMetadata customRangeMetadata = new CustomRangeMetadata(); 
customRangeMetadata.setTimeRangeList(timeRanges); 
customRangeMetadata.setType(CustomRangeMetadata.CustomRangeType.MARK_RANGE); 

//Create a MediaResource instance 
MediaResource mediaResource = MediaResource.createFromUrl( 
       "www.example.com/video/test_video.m3u8", timeRanges.toMedatada(null)); 

// Create a MediaPlayerItemConfig instance 
MediaPlayerItemConfig config =  
 new MediaPlayerItemConfig(getActivity().getApplicationContext()); 

// Set customRangeMetadata 
config.setCustomRangeMetadata(customRangeMetadata); 

// Prepare the content for playback by calling replaceCurrentResource 
// NOTE: mediaPlayer is an instance of a properly configured MediaPlayer  
mediaPlayer.replaceCurrentResource(mediaResource, config); 

// wait for TVSDK to reach the PREPARED state 
mediaPlayer.addEventListener(MediaPlayerEvent.STATE_CHANGED,  
 new StatusChangeEventListener() { 
   @Override 
   public void onStatusChanged(MediaPlayerStatusChangeEvent event) { 

   if( event.getStatus() == MediaPlayerStatus.PREPARED ) { 
       // TVSDK is in the PREPARED state, so start the playback  
       mediaPlayer.play(); 
   } 
   ... 
}
```>

