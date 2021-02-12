---
description: De manifestserver retourneert master afspeellijsten in de M3U8-indeling, conform de voorgestelde HTTP Live Streaming-standaard. Het bestaat uit een reeks variantvervoerstromen (TSs), elk die vertoningen van de zelfde inhoud voor verschillende beetjetarieven en formaten bevatten. Bij Adobe Primetime en invoegen wordt de EXT-X-MARKER-tag toegevoegd die door videospelers op de client moet worden geïnterpreteerd.
seo-description: De manifestserver retourneert master afspeellijsten in de M3U8-indeling, conform de voorgestelde HTTP Live Streaming-standaard. Het bestaat uit een reeks variantvervoerstromen (TSs), elk die vertoningen van de zelfde inhoud voor verschillende beetjetarieven en formaten bevatten. Bij Adobe Primetime en invoegen wordt de EXT-X-MARKER-tag toegevoegd die door videospelers op de client moet worden geïnterpreteerd.
seo-title: EXT-X-MARKERINGSrichtlijn
title: EXT-X-MARKERINGSrichtlijn
uuid: e349bf89-b196-47b4-a362-9913fa28b2c6
translation-type: tm+mt
source-git-commit: e437f4143fb939f46d106c64efc391137c33fe17
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 0%

---


# EXT-X-MARKERINGSrichtlijn {#ext-x-marker-directive}

De manifestserver retourneert master afspeellijsten in de M3U8-indeling, conform de voorgestelde HTTP Live Streaming-standaard. Het bestaat uit een reeks variantvervoerstromen (TSs), elk die vertoningen van de zelfde inhoud voor verschillende beetjetarieven en formaten bevatten. Bij Adobe Primetime en invoegen wordt de EXT-X-MARKER-tag toegevoegd die door videospelers op de client moet worden geïnterpreteerd.

Zie [Adobe Primetime Live streaming profiel](https://wwwimages2.adobe.com/content/dam/acom/en/devnet/primetime/PrimetimeHLS_April2014.pdf) voor meer informatie over de EXT-X-MARKER-tag.

>[!NOTE]
>
>Deze functionaliteit is alleen beschikbaar als de URL van de bootstrap-manifestserver niet de parameter `pttrackingmode` bevat.

>[!NOTE]
>
>De tag EXT-X-MARKER wordt toegevoegd aan advertentiesegmenten en niet aan inhoudssegmenten.

In de conceptstandaard op [Live HTTP-streaming](https://tools.ietf.org/html/draft-pantos-http-live-streaming-23) worden de inhoud en indeling van afspeellijsten met varianten beschreven. De tag EXT-X-MARKER geeft de client de opdracht een callback aan te roepen. Het bevat de volgende componenten:

* **** IDUnique-id (tekenreeks) voor deze callback-gebeurtenis binnen de context van de programmastream.

* **** TYPEType (tekenreeks) van de callback-gebeurtenis: PodBegin, PodEnd, PrerollPodBegin, PrerollPodEnd of AdBegin

* **** DURATIONLength of time (in seconden) vanaf het begin van het segment met de tag waarvoor de instructie geldig blijft.

* **** OFFSETOptional. De verschuiving (in seconden) ten opzichte van het begin van het afspelen van het segment, wanneer de callback moet worden aangeroepen.

   * `PodBegin` en  `PrerollPodBegin` bevatten baken-informatie in het kenmerk DATA en worden geactiveerd bij het begin van het segment. De tag `OFFSET` is hier dus niet beschikbaar.

   * `AdBegin` bevat bakeninformatie in het attribuut DATA en de impositietags worden geactiveerd aan het begin van dat segment. De tag `OFFSET` is hier dus ook niet beschikbaar.

   * `PodEnd` en  `PrerollPodEnd` bevatten baken-informatie in het kenmerk DATA, maar worden geactiveerd aan het einde van het huidige segment, omdat wordt verwacht dat deze tags worden geactiveerd aan het einde van het laatste segment van de laatste advertentie in de pod. In dit geval is `OFFSET` ingesteld op `<duration of segment>` om op te geven dat het baken moet worden geactiveerd aan het einde van het huidige segment.

* **Een tekenreeks met** DATABase64-codering die is ingesloten in dubbele aanhalingstekens die de gegevens bevatten die aan de toepassing moeten worden doorgegeven wanneer de callback wordt aangeroepen. Het bevat informatie over het bijhouden van advertenties die voldoet aan de VMAP1.0- en VAST3.0-specificaties.

* **Aantal** advertenties dat in de advertentiesonderbreking zal worden vastgezet.

   Alleen van toepassing als de component TYPE is ingesteld op PodBegin of PrerollPodBegin.

* **** BREAKDURTotale duur (in seconden) van het gevulde en afgebroken formulier.

   Alleen van toepassing als de component TYPE is ingesteld op PodBegin of PrerollPodBegin.

Wanneer het construeren van callback, interpreteer de componenten EXT-X-MARKER als volgt:

* Wanneer de tag `OFFSET` bevat, wordt de callback geactiveerd bij de opgegeven verschuiving ten opzichte van het begin van het afspelen van de inhoud in dat segment. Anders, brand de callback zodra de inhoud in dat segment begint speel.
* Gebruik `DURATION` om de voortgang van de advertentie-inhoud te volgen en om URL&#39;s aan te vragen voor het bijhouden van gebeurtenissen.
* Geef `ID`, `TYPE`, en `DATA` aan callback door.

Gebruik `PrerollPodBegin`, en `PrerollPodEnd` waarden voor `TYPE` om te beslissen welk TS segment eerst in levende/lineaire stromen moet spelen.

>[!NOTE]
>
>De waarden `PrerollPodBegin` en `PrerollPodEnd` zijn alleen beschikbaar wanneer een pre-roll-advertentie in een live stream wordt ingevoegd.

De manifestserver omvat markeringen EXT-X-MARKER in de volgende segmenten:

* Het eerste segment in het advertentieeinde om het begin van een advertentiepod bij te houden.
* Het eerste segment van de advertentie om het begin/einde/de voortgang van een afzonderlijke advertentie in een advertentiepod bij te houden.
* Het laatste segment in het advertentieeinde om het einde van een advertentiepod bij te houden.

De manifestserver verzendt een `VMAP1.0-conformant` document van XML om het begin en het eind van elk advertentieeinde te volgen. Het is een gefilterde versie van de daadwerkelijke die reactie VMAP1.0 door de advertentieserver wordt teruggekeerd, en bevat hoofdzakelijk de volgende gebeurtenissen zoals hier getoond:

```xml
<?xml version="1.0"?> 
<AdTrackingFragments> 
<AdTrackingFragment> 
<vmap:VMAP xmlns:vmap="https://www.iab.net/vmap-1.0" version="1.0"> 
    <vmap:AdBreak breakType="linear" breakId="mypre" timeOffset="start"> 
        <vmap:TrackingEvents> 
            <vmap:Tracking event="breakStart"> 
                https://MyServer.com/breakstart.gif 
            </vmap:Tracking> 
            <vmap:Tracking event="breakEnd"> 
                https://MyServer.com/breakend.gif 
            </vmap:Tracking> 
            <vmap:Tracking event="error"> 
                https://MyServer.com/error.gif 
            </vmap:Tracking> 
        </vmap:TrackingEvents> 
    </vmap:AdBreak> 
</vmap:VMAP> 
</AdTrackingFragment> 
</AdTrackingFragments>
```

Voor elke advertentie die de manifestserver in de programmainhoud opneemt, verzendt het een VAST3.0-conformant document van XML om die advertentie te volgen. Elk XML-document bevat een `<InLine>`-element dat het lineaire en creatieve ingevoegde element beschrijft, of een `<Wrapper>`-element in het geval van omvattende advertenties (dat wil zeggen gekoppelde of omgeleide advertenties), en eventuele bijbehorende advertenties en uitbreidingen. Als de VAST-reactie een reekskenmerk bevat, bijvoorbeeld wanneer de advertentie deel uitmaakt van een advertentiepod, bevat het document dat kenmerk. Hier volgt een voorbeeld van een XML-document dat compatibel is met VAST3.0 voor het bijhouden van een afzonderlijke advertentie:

```xml
<?xml version="1.0"?> 
<AdTrackingFragments> 
<AdTrackingFragment> 
<VAST xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"  
      version="3.0"  
      xsi:noNamespaceSchemaLocation="https://service.videoplaza.com/schema/iab/vast-3.0.xsd"> 
<Ad id="903395"> 
    <InLine> 
      <AdSystem version="1.0">Auditude</AdSystem> 
      <AdTitle/> 
      <Error>https://ad.qa.auditude.com/adserver/?ErrAd1=[ERRORCODE]</Error> 
      <Impression id="urn:aeid:903395">https://ad.qa.auditude.com/adserver/e?type=adimp&amp; 
                 cid=127860991&amp; 
                 z=50183&amp; 
                 a=903395&amp; 
                 s=ef8c51dc&amp; 
                 t=1355309735&amp; 
                 w=100000&amp; 
                 uid=_CxLm0b1SeKD8KXco__5TQ&amp; 
                 l=1355280906&amp; 
                 u=956c3cd141086a1da44dcae8ea4ed14a&amp; 
                 br=1&amp; 
                 sq=1&amp; 
                 pod=id:1,ctype:l,ptype:p,dur:400,lot:8,cpos:1,edur:400,elot:8&amp; 
                 ax=0,0,1720,0/?ContentPosition=[CONTENTPLAYHEAD] 
                               ?Cashcash=[CACHEBUSTING] 
                               ?Asset=[ASSETURI] 
      </Impression> 
      <Creatives> 
        <Creative> 
          <Linear> 
            <Duration>00:00:15</Duration> 
            <TrackingEvents> 
              ... 
              <Tracking event="firstQuartile"> 
                https://ad.qa.auditude.com/adserver/e?type=AD_PROGRESS&amp; 
                  a=903395&amp; 
                  a1=105&amp; 
                  ref=urn:asset:903395:105&amp; 
                  unit=percent&amp; 
                  progress=25&amp; 
                  cid=127860991&amp; 
                  z=50183&amp; 
                  a=903395&amp; 
                  s=ef8c51dc&amp; 
                  t=1355309735&amp; 
                  w=100000&amp; 
                  uid=_CxLm0b1SeKD8KXco__5TQ&amp; 
                  l=1355280906&amp; 
                  u=956c3cd141086a1da44dcae8ea4ed14a&amp; 
                  br=1&amp; 
                  sq=1&amp; 
                  pod=id:1,ctype:l,ptype:p,dur:400,lot:8,cpos:1,edur:400,elot:8&amp; 
                  ax=0,0,1720,0/?ContentPosition=[CONTENTPLAYHEAD] 
                                ?Cashcash=[CACHEBUSTING] 
                                ?Asset=[ASSETURI] 
              </Tracking>                
              <Tracking event="midpoint"> 
                https://ad.qa.auditude.com/adserver/e?type=AD_PROGRESS&amp; 
                  a=903395&amp; 
                  a1=105&amp; 
                  ref=urn:asset:903395:105&amp; 
                  unit=percent&amp; 
                  progress=50&amp; 
                  cid=127860991&amp; 
                  z=50183&amp; 
                  a=903395&amp; 
                  s=ef8c51dc&amp; 
                  t=1355309735&amp; 
                  w=100000&amp; 
                  uid=_CxLm0b1SeKD8KXco__5TQ&amp; 
                  l=1355280906&amp; 
                  u=956c3cd141086a1da44dcae8ea4ed14a&amp; 
                  br=1&amp; 
                  sq=1&amp; 
                  pod=id:1,ctype:l,ptype:p,dur:400,lot:8,cpos:1,edur:400,elot:8&amp; 
                  ax=0,0,1720,0/?ContentPosition=[CONTENTPLAYHEAD] 
                                ?Cashcash=[CACHEBUSTING] 
                                ?Asset=[ASSETURI] 
              </Tracking> 
              <Tracking event="firstQuartile"> 
                https://www.Tweeeen.com/?ContentPosition=[CONTENTPLAYHEAD] 
                                       ?Cashcash=[CACHEBUSTING] 
                                       ?Asset=[ASSETURI] 
              </Tracking> 
              <Tracking event="midpoint"> 
                https://www.Fiftyyyy.com/?ContentPosition=[CONTENTPLAYHEAD] 
                                        ?Cashcash=[CACHEBUSTING] 
                                        ?Asset=[ASSETURI] 
              </Tracking> 
              ... 
            </TrackingEvents> 
            <VideoClicks> 
              <ClickTracking> 
                https://www.MP4-Vid-ClickTrack.com/?ContentPosition=[CONTENTPLAYHEAD] 
                                                  ?Cashcash=[CACHEBUSTING] 
                                                  ?Asset=[ASSETURI] 
              </ClickTracking> 
              <ClickThrough> 
                https://www.cnn.com/?ContentPosition=[CONTENTPLAYHEAD] 
                                   ?Cashcash=[CACHEBUSTING] 
                                   ?Asset=[ASSETURI] 
              </ClickThrough> 
              ... 
            </VideoClicks> 
            <AdParameters>campaign_id=7012</AdParameters> 
            <MediaFiles> 
              ...            
            </MediaFiles> 
          </Linear> 
        </Creative> 
        <Creative> 
          <CompanionAds> 
            <Companion id="103" width="300" height="250"> 
              <StaticResource creativeType="image/jpeg"> 
                https://ad.qa.auditude.com/adserver/c/z=50183; 
                  l=1355280906; 
                  u=956c3cd141086a1da44dcae8ea4ed14a; 
                  uid=_CxLm0b1SeKD8KXco__5TQ; 
                  cid=127860991; 
                  s=ef8c51dc; 
                  t=1355309735; 
                  br=1; 
                  sq=1; 
                  pod=id%3a1%2cctype%3al%2cptype%3ap%2cdur 
                    %3a400%2clot%3a8%2ccpos%3a1%2cedur%3a400%2celot%3a8; 
                  ax=0%2c0%2c1720%2c0; 
                  w=100000; 
                  a=903395; 
                  a1=103/c300x250.jpeg 
              </StaticResource> 
              <CompanionClickThrough> 
                https://ad.qa.auditude.com/adserver/l/a=903395%3Ba1=103 
                  %3Ba2=1%3Bz=50183%3Bl=1355280906%3Bu=956c3cd141086a1da44dcae8ea4ed14a 
                  %3Bcid=127860991%3Bs=ef8c51dc%3Buid=_CxLm0b1SeKD8KXco__5TQ 
                  %3Bt=1355309735%3Bbr=1%3Bsq=1%3Bpod=id%3a1%2cctype%3al%2cptype 
                  %3ap%2cdur%3a400%2clot%3a8%2ccpos%3a1%2cedur%3a400%2celot%3a8 
                  %3Bax=0%2c0%2c1720%2c0 
              </CompanionClickThrough> 
              <AdParameters>campaign_id=7012</AdParameters> 
            </Companion> 
          </CompanionAds> 
        </Creative> 
        ... 
      </Creatives> 
      <Extensions> 
        <Extension type="Behavior"> 
          ... 
        </Extension> 
      </Extensions> 
    </InLine> 
  </Ad> 
  </VAST> 
</AdTrackingFragment> 
</AdTrackingFragments> 
```
