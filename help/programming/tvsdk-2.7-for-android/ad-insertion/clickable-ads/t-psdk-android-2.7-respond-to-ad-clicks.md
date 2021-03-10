---
description: Wanneer een gebruiker op een advertentie of een verwante knop klikt, moet de toepassing reageren. TVSDK biedt u informatie over de doel-URL voor de klik.
title: Reageren op klikken op advertenties
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---


# Reageren op klikken op advertenties {#respond-to-clicks-on-ads}

TVSDK biedt u informatie zodat u op doorklikadvertenties kunt werken. Terwijl u de interface van de speler maakt, moet u bepalen hoe u moet reageren wanneer een gebruiker op een klikbare advertentie klikt.

Voor TVSDK voor Android kan alleen op lineaire advertenties worden geklikt.
Wanneer een gebruiker op een advertentie of een verwante knop klikt, moet de toepassing reageren. TVSDK biedt u informatie over de doel-URL voor de klik.

1. Registreer `AdClickedEventListener.onAdClicked` om een gebeurtenislistener voor TVSDK in te stellen en de doorklikinformatie te verstrekken.

   Wanneer een gebruiker op een advertentie of een verwante knop klikt, verzendt TVSDK dit bericht, inclusief informatie over de bestemming voor de klik.
1. Gebruikersinteracties controleren op klikbare advertenties.
1. Wanneer de gebruiker de advertentie of knop aanraakt of erop klikt, om TVSDK op de hoogte te brengen, roept u `notifyClick` op `MediaPlayerView`.
1. Luister naar de `onAdClick(AdClickEvent event)`-gebeurtenis van TVSDK.
1. Als u de doorklikURL en verwante informatie wilt ophalen, gebruikt u de methoden getter voor de instantie `AdClickEvent`.
1. De video pauzeren.

   Zie Het pauzeren en hervatten van het afspelen voor meer informatie over het pauzeren van de video.
1. Gebruik de doorklikinformatie om de advertentie-door URL en de verwante informatie te tonen.

       U kunt de informatie bijvoorbeeld op een van de volgende manieren weergeven:
   
   * In uw toepassing, door klik-door URL in browser te openen.

      Op bureaubladplatforms worden de video en het afspeelgebied gebruikt om doorklikURL&#39;s aan te roepen wanneer de gebruiker klikt.
   * Gebruikers omleiden naar hun externe mobiele webbrowser.

      Op mobiele apparaten worden de video en het afspeelgebied gebruikt voor andere functies, zoals het verbergen en weergeven van besturingselementen, het pauzeren van het afspelen, het uitbreiden naar het volledige scherm, enzovoort. Op deze apparaten wordt een aparte weergave, zoals een sponsor, gebruikt om de doorklikURL te starten.

1. Sluit het browservenster waarin de doorklikinformatie wordt weergegeven en hervat het afspelen van de video.

<!--<a id="example_2D93228E510D438C8AB5559897817A47"></a>-->

Bijvoorbeeld:

```java
private AdStartedEventListener adStartedEventListener =  
  new AdStartedEventListener() { 
    @Override 
    public void onAdStarted(AdPlaybackEvent adPlaybackEvent) { 
        Ad ad = adPlaybackEvent.getAd(); 
        if (ad == null) { 
            return; 
        } 
 
        _pubOverlay.startAd(adPlaybackEvent.getAdBreak(), ad); 
 
        if (areClickableAdsEnabled() && ad.isClickable()) { 
            _isClickableAdPlaying = true; 
            _playerClickableAdFragment.show(); 
        } 
    } 
}; 
 
private AdCompletedEventListener adCompletedEventListener =  
  new AdCompletedEventListener() { 
    @Override 
    public void onAdCompleted(AdPlaybackEvent adPlaybackEvent) { 
        Ad ad = adPlaybackEvent.getAd(); 
        _pubOverlay.stopAd(adPlaybackEvent.getAdBreak(), ad); 
 
        _isClickableAdPlaying = false; 
        if (ad.isClickable()) { 
            _playerClickableAdFragment.hide(); 
        } 
    } 
}; 
 
private AdClickedEventListener adClickedEventListener =  
  new AdClickedEventListener() { 
    @Override 
    public void onAdClicked(AdClickEvent adClickEvent) { 
        AdClick adClick = adClickEvent.getAdClick(); 
        Ad ad = adClickEvent.getAd(); 
 
        String url = adClick.getUrl(); 
        if (url == null || url.trim().equals("")) { 
        } else { 
            Uri uri = Uri.parse(url); 
            Intent intent = new Intent(ACTION_VIEW, uri); 
            try { 
                startActivity(intent); 
            } catch (Exception e) { 
            } 
        } 
    } 
}; 
```

