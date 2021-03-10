---
description: Wanneer het afspelen een advertentie-einde bereikt, een advertentie-einde doorgeeft of eindigt in een advertentie-einde, definieert TVSDK een standaardgedrag voor het plaatsen van de huidige afspeelkop.
title: Afspelen met advertenties aanpassen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '990'
ht-degree: 0%

---


# Afspelen aanpassen met advertenties{#customize-playback-with-ads}

Wanneer het afspelen een advertentie-einde bereikt, een advertentie-einde doorgeeft of eindigt in een advertentie-einde, definieert TVSDK een standaardgedrag voor het plaatsen van de huidige afspeelkop.

>[!TIP]
>
>U kunt het standaardgedrag met voeten treden door de `PTAdPolicySelector` klasse te gebruiken.

Het standaardgedrag varieert, afhankelijk van het feit of de gebruiker de advertentie doorgeeft tijdens het afspelen of door te zoeken in een video.

U kunt het gedrag voor het afspelen en afspelen op de volgende manieren aanpassen:

* Sla de positie op waar de gebruiker het bekijken van de video heeft gestopt en hervat het afspelen op dezelfde positie in een toekomstige sessie.
* Als een advertentie-einde aan de gebruiker wordt voorgesteld, toon geen extra advertenties voor een aantal notulen, zelfs als de gebruiker aan een nieuwe positie zoekt.
* Als de inhoud na een paar minuten niet kan worden afgespeeld, start u de stream opnieuw of start u de stream over naar een andere bron voor dezelfde inhoud.

   Als u tijdens de afspeelsessie van de failover de gebruiker de mogelijkheid wilt bieden om advertenties over te slaan en de vorige mislukte positie te herstellen, kunt u pre-roll- en/of mid-roll-advertenties uitschakelen. TVSDK biedt methoden om pre- en mid-roll-advertenties over te slaan.

## API-elementen voor het afspelen van advertenties {#section_296ADE00CFEA40CBA1B46142720D13A5}

TVSDK biedt klassen en methoden waarmee u het afspeelgedrag kunt aanpassen van inhoud die reclame bevat.
De volgende API-elementen zijn handig voor het aanpassen van het afspelen:

<table id="table_B07E373B9D2B425AB36466B1D42411AD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> API-element </th> 
   <th colname="col2" class="entry"> Inhoud die reclame ondersteunt </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTAdMetadata  </span> </td> 
   <td colname="col2"> Bepaal of een advertentieeinde moet worden gemarkeerd als gevolgd door een viewer en zo ja, wanneer om het te markeren. Stel het gevolgde beleid in en krijg dit via de eigenschap <span class="codeph"> adBreakAsWatched </span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTAdPolicySelector  </span> </td> 
   <td colname="col2"> Protocol dat aanpassing van TVSDK en gedrag toestaat. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTDefaultAdPolicySelector  </span> </td> 
   <td colname="col2"> Klasse die het standaardgedrag van TVSDK uitvoert. Uw toepassing kan deze klasse overschrijven om het standaardgedrag aan te passen zonder de volledige interface te implementeren. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTMediaPlayer  </span> </td> 
   <td colname="col2"> 
    <ul id="ul_37700A741403448A8760FDDA68B099AA"> 
     <li id="li_B465170D449E49489C5924572BEEB4A5"> <span class="codeph"> localTime  </span>. <p>Dit is de lokale tijd van het afspelen, exclusief de geplaatste en afgebroken foto's. </p> </li> 
     <li id="li_D9D68CF428904BB2B84E1BCE828A90DC"> <span class="codeph"> seekToLocalTime  </span> . <p>Hier wordt gezocht ten opzichte van een lokale tijd in de stream. </p> </li> 
     <li id="li_9DBCA75537DC4824AA66B53A3FA28812"> <span class="codeph"> getTimeline.convertToLocalTime  </span>. <p>De virtuele positie op de tijdlijn wordt geconverteerd naar de lokale positie. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTAdBreak  </span> </td> 
   <td colname="col2"> <span class="codeph"> isWatched,  </span> eigenschap. Geeft aan of de viewer de advertentie heeft gecontroleerd. </td> 
  </tr> 
 </tbody> 
</table>

## Aangepaste weergave instellen {#section_8209BAACC7814C9399988DC7DE9CF4CA}

Registreer de beleidsinstantie voor advertenties bij TVSDK voordat u gedrag voor advertenties kunt aanpassen of overschrijven.

Voer een van de volgende handelingen uit om het gedrag van advertenties aan te passen:

* Conform het `PTAdPolicySelector`-protocol en implementeer alle vereiste methoden voor beleidsselectie.

   Deze optie wordt aanbevolen als u **all** de standaard en het gedrag moet negeren.

* Overschrijf de klasse `PTDefaultAdPolicySelector` en verstrek implementaties voor slechts die gedragingen die aanpassing vereisen.

   Deze optie wordt geadviseerd als u slechts **sommige** van het standaardgedrag moet met voeten treden.

Voer voor beide opties de volgende taken uit:

1. Registreer de beleidsinstantie die door TVSDK via de cliëntfabriek moet worden gebruikt.

   >[!NOTE]
   >
   >Aangepast advertentiebeleid dat aan het begin van het afspelen is geregistreerd, wordt gewist wanneer de `PTMediaPlayer`-instantie wordt gedealdeerd. Elke keer dat een nieuwe afspeelsessie wordt gemaakt, moet uw toepassing een beleidsselector registreren.

   Bijvoorbeeld:

   ```
   // Create an instance of the custom policy selector 
   PTS5MinuteSkipBreakPolicySelector *adPolicySelector  
        = [[[PTS5MinuteSkipBreakPolicySelector alloc] initWithMediaPlayer:self.player] autorelease]; 
   
   // register this instance 
   [[PTDefaultMediaPlayerClientFactory defaultFactory] registerAdPolicySelector:adPolicySelector];
   ```

1. Implementeer uw aanpassingen.

## Overslaan en afbrekingen gedurende een tijdsperiode {#section_99809BE4D9BB4DEEBBF596C746CA428A}

Standaard dwingt TVSDK een advertentie-einde af wanneer de gebruiker een advertentie-einde zoekt. U kunt het gedrag aanpassen om een advertentie-einde over te slaan als de tijd die is verstreken vanaf een vorige eindemarkering binnen een bepaald aantal minuten is.

>[!IMPORTANT]
>
>Wanneer er een interne zoekactie is om een advertentie over te slaan, kan het zijn dat er een kleine pauze is in het afspelen.

In het volgende voorbeeld van een aangepaste advertentiebeleidskiezer worden advertenties in de komende vijf minuten (tijd van de wandklok) overgeslagen nadat een gebruiker een advertentiesonderbreking heeft bekeken.

1. Registreer de beleidsinstantie die door TVSDK via de cliëntfabriek moet worden gebruikt.

   ```
   // Create an instance of the custom policy selector 
   PTS5MinuteSkipBreakPolicySelector *adPolicySelector  
        = [[[PTS5MinuteSkipBreakPolicySelector alloc] initWithMediaPlayer:self.player] autorelease]; 
   
   // register this instance 
   [[PTDefaultMediaPlayerClientFactory defaultFactory] registerAdPolicySelector:adPolicySelector];
   ```

1. Implementeer uw aanpassingen.

**PTS5MinuteSkipBreakPolicySelector.h**

```
#import "PTMediaPlayerNotifications.h" 
#import "PTMediaPlayer.h" 
#import "PTDefaultAdPolicySelector.h" 
 
//  extend the default policy  
selector@interface PTS5MinuteSkipBreakPolicySelector : PTDefaultAdPolicySelector 
  
- (id)initWithMediaPlayer:(PTMediaPlayer *)player; 
  
@end
```

**PTS5MinuteSkipBreakPolicySelector.m**

```
#import "PTS5MinuteSkipBreakPolicySelector.h" 
  
double MIN_BREAK_INTERVAL  = 60 * 5; // 5 minutes 
  
@implementation PTS5MinuteSkipBreakPolicySelector 
{ 
    PTMediaPlayer *_player; 
    NSTimeInterval _lastAdBreakPlayedTime; 
} 
  
- (id)initWithMediaPlayer:(PTMediaPlayer *)player 
{ 
    if (self = [super init]) 
    { 
        _lastAdBreakPlayedTime = 0; 
        _player = [player retain]; 
        [self addobservers]; 
    } 
    
    return self; 
} 
  
- (NSArray *)selectAdBreaksToPlay:(PTAdPolicyInfo *)info 
{ 
    NSLog(@"%@ - selectAdBreaksToPlay (%f): %f", self,  
        CMTimeGetSeconds(info.currentTime), _lastAdBreakPlayedTime); 
    
    BOOL shouldPlay = [self shouldPlayAdBreaks]; 
    if (shouldPlay) 
    { 
        return [super selectAdBreaksToPlay:info]; 
    } 
    
    return nil; 
} 
  
- (PTAdBreakPolicyType)selectPolicyForAdBreak:(PTAdPolicyInfo *)info 
{ 
    NSLog(@"%@ - selectPolicyForAdBreak (%f): %f  %f", self,  
            CMTimeGetSeconds(info.currentTime), _lastAdBreakPlayedTime,  
            [[NSDate date] timeIntervalSince1970]); 
    
    BOOL shouldPlay = [self shouldPlayAdBreaks]; 
    if (shouldPlay) 
    { 
        return [super selectPolicyForAdBreak:info]; 
    } 
    
    return PTAdBreakPolicyTypeSkip; 
} 
  
- (BOOL)shouldPlayAdBreaks 
{ 
    NSTimeInterval currentTime = [[NSDate date] timeIntervalSince1970]; 
    if (_lastAdBreakPlayedTime <= 0) 
    { 
        return YES; 
    } 
    
    if (_lastAdBreakPlayedTime > 0 && (currentTime - _lastAdBreakPlayedTime) > MIN_BREAK_INTERVAL) 
    { 
        return YES; 
    } 
    
    // don't play any ad break if 5 minutes hasn't elapsed 
    return NO; 
} 
  
- (void) onMediaPlayerAdBreakStarted:(NSNotification *) notification 
{ 
    NSLog(@"%@ - AdBreak Start", self); 
} 
  
- (void) onMediaPlayerAdBreakCompleted:(NSNotification *) notification 
{ 
    _lastAdBreakPlayedTime = [[NSDate date] timeIntervalSince1970]; 
    NSLog(@"%@ - AdBreak Complete at: %f", self, _lastAdBreakPlayedTime); 
} 
  
- (void)addobservers 
{ 
    [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerAdBreakStarted:)  
                name:PTMediaPlayerAdBreakStartedNotification object:_player]; 
    [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerAdBreakCompleted:)  
                name:PTMediaPlayerAdBreakCompletedNotification object:_player]; 
} 
  
- (void)removeObservers 
{ 
    [[NSNotificationCenter defaultCenter] removeObserver:self]; 
} 
  
- (void)dealloc 
{ 
    [self removeObservers]; 
    [_player release]; 
    [super dealloc]; 
} 
  
@end
```

## De videopositie opslaan en later {#section_FAE252E38CED48D4BDD38BAA4A6A20A4} hervatten

U kunt de huidige afspeelpositie in een video opslaan en het afspelen op dezelfde positie in een volgende sessie hervatten.

Dynamisch ingevoegde advertenties verschillen per gebruikerssessie, zodat het opslaan van de positie **met** gespliceerde advertenties naar een andere positie in een toekomstige sessie verwijst. TVSDK biedt methoden om de afspeelpositie op te halen zonder gespliceerde advertenties te negeren.

1. Wanneer de gebruiker een video afsluit, wordt de positie in de video opgehaald en opgeslagen.

   >[!TIP]
   >
   >Duur van advertentie is niet inbegrepen.

   De pauzes van de toevoeging kunnen in elke zitting als toe te schrijven aan advertentiepatronen, frequentiegrenzen, etc. variëren. De huidige tijd van de video in één sessie kan in een volgende sessie anders zijn. Wanneer u een positie in de video opslaat, haalt de toepassing de lokale tijd op. Gebruik de eigenschap `localTime` om deze positie te lezen, die u kunt opslaan op het apparaat of in een database op de server.

   Als de gebruiker bijvoorbeeld op de twintigste minuut van de video staat en deze positie vijf minuten aan advertenties bevat, is `currentTime` 1200 seconden, terwijl `localTime` op deze positie 900 seconden is.

   >[!IMPORTANT]
   >
   >De lokale tijd en de huidige tijd zijn het zelfde voor levende/lineaire stromen. In dit geval heeft `convertToLocalTime` geen effect. Voor VOD blijft de lokale tijd ongewijzigd tijdens het afspelen van advertenties.

   ```
   - (void) onMediaPlayerTimeChange:(NSNotification *)notification { 
       CMTimeRange seekableRange = self.player.seekableRange; 
   
       if (CMTIMERANGE_IS_VALID(seekableRange)) { 
           double seekableRangeStart = CMTimeGetSeconds(seekableRange.start); 
           double seekableRangeDuration = CMTimeGetSeconds(seekableRange.duration); 
           double currentTime = CMTimeGetSeconds(self.player.currentTime); // includes ads 
           double localTime = CMTimeGetSeconds(self.player.localTime); // no ads 
       } 
   }
   ```

1. De video op dezelfde positie hervatten: Als u het afspelen van de video wilt hervatten vanaf de positie die tijdens een vorige sessie is opgeslagen, gebruikt u `seekToLocalTime`

   >[!TIP]
   >
   >Deze methode wordt alleen aangeroepen met lokale tijdwaarden. Als de methode wordt aangeroepen met de huidige-tijdresultaten, treedt een onjuist gedrag op.

   Gebruik `seekToTime` om naar de huidige tijd te zoeken.

1. Wanneer uw toepassing de gebeurtenis `PTMediaPlayerStatusReady` van de statusverandering ontvangt, zoek aan de bewaarde lokale tijd.

   ```
   [self.player seekToLocalTime:CMTimeMake(900, 1) completionHandler:^(BOOL finished) { 
       [self.player play]; 
   }];
   ```

1. Geef de pagina-einden op zoals opgegeven in de interface voor advertentiebeleid.
1. Voer een douaneselecteur van het advertentiebeleid uit door de standaard uit te breiden en beleidsselecteur.
1. Geef de ad-einden op die aan de gebruiker moeten worden weergegeven door `selectAdBreaksToPlay` te implementeren

   >[!NOTE]
   >
   >Deze methode omvat een pre-rol en onderbreking en de middenrol en pauzes vóór de lokale tijdpositie. Uw toepassing kan besluiten een pre-rol en onderbreking te spelen en aan de gespecificeerde lokale tijd te hervatten, een middenrol en onderbreking te spelen en aan de gespecificeerde lokale tijd te hervatten, of geen ad onderbrekingen te spelen.

