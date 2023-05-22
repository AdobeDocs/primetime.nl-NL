---
description: Deze workflow voor multi-DRM begeleidt u door het instellen, verpakken, licentiëren en afspelen van DASH-inhoud die met Windows en PlayReady is gecodeerd.
title: MultiDRM-workflow voor Windows en PlayReady
exl-id: 97adfa69-52ef-470b-903a-eff1f075b7be
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# MultiDRM-workflow voor Windows en PlayReady {#multi-drm-workflow-for-widevine-and-playready}

Deze workflow voor multi-DRM begeleidt u door het instellen, verpakken, licentiëren en afspelen van DASH-inhoud die met Windows en PlayReady is gecodeerd.

Met primetime-TVSDK kunt u met Windows gecodeerde of met PlayReady gecodeerde DASH-inhoud alleen op HTML5 en Android afspelen in TVSDK-versie 2.X. De encryptie van de inhoud DASH wordt bepaald door de Gemeenschappelijke specificatie van de Encryptie, de volledige details waarvan buiten het werkingsgebied van dit document zijn. Deze sectie bevat relevante details over de DASH-indeling en de versleutelingsspecificatie en informatie over enkele gereedschappen die u kunt gebruiken om de ondersteunde inhoud te genereren.

>[!NOTE]
>
>Er zijn geen plannen gemaakt om de weergave van Widevine-encrypted DASH-inhoud te ondersteunen met Android TVSDK 1.X.

## DASH-inhoud en algemene codering in één oogopslag {#section_33A881158F724835B4B89AAE97302B17}

De inhoud van het streepje bestaat uit hoofdmanifest, geschreven in xml, dat aan video en audiodossiers aan playback richt. In het voorbeeld onder het DASH-manifest verwijst naar een video-URL, video/1080_30.mp4 en een audio-URL, audio/1080_30.mp4, ten opzichte van de URL van het manifest.

```
<MPD xmlns="urn:mpeg:DASH:schema:MPD:2011" xmlns:cenc="urn:mpeg:cenc:2013" xmlns:scte35="urn:scte:scte35:2013" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"mediaPresentationDuration="PT30S" minBufferTime="PT8S" profiles="urn:mpeg:dash:profile:isoff-on-demand:2011" type="static" xsi:schemaLocation="urn:mpeg:DASH:schema:MPD:2011 DASH-MPD.xsd">
    <Period id="1" start="PT0S">
        <AdaptationSet bitstreamSwitching="true" contentType="video" id="1" segmentAlignment="true" startWithSAP="2">
            <Representation bandwidth="4215100" codecs="avc1.4d4029" height="1080" id="1" mimeType="video/mp4" width="1920">
                <BaseURL>video/1080_30.mp4</BaseURL>
                <CueInfo schemeIdUri="urn:adobe:mpeg:dash:cueinfo:2012"/>
            </Representation>
        </AdaptationSet>
 
        <AdaptationSet bitstreamSwitching="true" contentType="audio" id="2" segmentAlignment="1" startWithSAP="1">
            <Representation bandwidth="320600" codecs="mp4a.40.02" id="1" mimeType="audio/mp4">
                <BaseURL>audio/1080_30.mp4</BaseURL>
                <CueInfo schemeIdUri="urn:adobe:mpeg:dash:cueinfo:2012"/>
            </Representation>
        </AdaptationSet>
    </Period>
</MPD>
```

Hieronder ziet u een voorbeeld-manifest waarop Gemeenschappelijke codering is toegepast. De Windows-elementen voor inhoudsbeveiliging XML (de `<ContentProtection>` blokken) in het manifest bevatten een base64 gecodeerde psh (de Specifieke Kopbal van het Systeem van de Bescherming) doos. Het vak PSH bevat de gegevens die nodig zijn voor het initialiseren van de ontsleuteling van inhoud. Deze gegevens worden ook ingesloten in de video-/audio-inhoud waarnaar het manifest verwijst. DASH-inhoud kan meerdere elementen ter bescherming van inhoud bevatten, bijvoorbeeld 1 voor PlayReady en 1 voor Windows.

```
<?xml version="1.0" ?>
<MPD mediaPresentationDuration="PT3M35.533S" minBufferTime="PT15.00S" profiles="urn:mpeg:dash:profile:isoff-live:2011" type="static" xmlns="urn:mpeg:dash:schema:mpd:2011" xmlns:cenc="urn:mpeg:cenc:2013">
  <!-- Created with Bento4 mp4-dash.py, VERSION=1.6.0-607 -->
  <Period>
    <!-- Audio -->
    <AdaptationSet mimeType="audio/mp4" segmentAlignment="true" startWithSAP="1">
      <!-- Common Encryption -->
      <ContentProtection cenc:default_KID="9e828b37-842d-9f71-0233-c007fb1d4f5b" schemeIdUri="urn:mpeg:dash:mp4protection:2011" value="cenc"/>
      <!-- Widevine -->
      <ContentProtection schemeIdUri="urn:uuid:edef8ba9-79d6-4ace-a3c8-27dcd51d21ed">
        <cenc:pssh>
        AAAAQ3Bzc2gAAAAA7e+LqXnWSs6jyCfc1R0h7QAAACMIARIQnoKLN4Qtn3ECM8AH+x1PWxoKaW50ZXJ0cnVzdCIBKg==
        </cenc:pssh>
      </ContentProtection>
      <Representation audioSamplingRate="44100" bandwidth="200429" codecs="mp4a.40.2" id="audio/und">
        <AudioChannelConfiguration schemeIdUri="urn:mpeg:dash:23003:3:audio_channel_configuration:2011" value="2"/>
        <SegmentList duration="15000" timescale="1000">
          <Initialization sourceURL="audio/und/init.mp4"/>
          <SegmentURL media="audio/und/seg-1.m4f"/>
          <SegmentURL media="audio/und/seg-2.m4f"/>
          <SegmentURL media="audio/und/seg-3.m4f"/>
          <SegmentURL media="audio/und/seg-4.m4f"/>
          <SegmentURL media="audio/und/seg-5.m4f"/>
          <SegmentURL media="audio/und/seg-6.m4f"/>
          <SegmentURL media="audio/und/seg-7.m4f"/>
          <SegmentURL media="audio/und/seg-8.m4f"/>
          <SegmentURL media="audio/und/seg-9.m4f"/>
          <SegmentURL media="audio/und/seg-10.m4f"/>
          <SegmentURL media="audio/und/seg-11.m4f"/>
          <SegmentURL media="audio/und/seg-12.m4f"/>
          <SegmentURL media="audio/und/seg-13.m4f"/>
          <SegmentURL media="audio/und/seg-14.m4f"/>
          <SegmentURL media="audio/und/seg-15.m4f"/>
          <SegmentURL media="audio/und/seg-16.m4f"/>
        </SegmentList>
      </Representation>
    </AdaptationSet>
 
    <!-- Video -->
    <AdaptationSet maxHeight="720" maxWidth="1280" mimeType="video/mp4" minHeight="720" minWidth="1280" segmentAlignment="true" startWithSAP="1">
      <!-- Common Encryption -->
      <ContentProtection cenc:default_KID="9e828b37-842d-9f71-0233-c007fb1d4f5b" schemeIdUri="urn:mpeg:dash:mp4protection:2011" value="cenc"/>
      <!-- Widevine -->
      <ContentProtection schemeIdUri="urn:uuid:edef8ba9-79d6-4ace-a3c8-27dcd51d21ed">
        <cenc:pssh>
        AAAAQ3Bzc2gAAAAA7e+LqXnWSs6jyCfc1R0h7QAAACMIARIQnoKLN4Qtn3ECM8AH+x1PWxoKaW50ZXJ0cnVzdCIBKg==
        </cenc:pssh>
      </ContentProtection>
 
      <Representation bandwidth="2640920" codecs="avc1.64001F" frameRate="30" height="720" id="video/1" scanType="progressive" width="1280">
        <SegmentList duration="15000" timescale="1000">
          <Initialization sourceURL="video/1/init.mp4"/>
          <SegmentURL media="video/1/seg-1.m4f"/>
          <SegmentURL media="video/1/seg-2.m4f"/>
          <SegmentURL media="video/1/seg-3.m4f"/>
          <SegmentURL media="video/1/seg-4.m4f"/>
          <SegmentURL media="video/1/seg-5.m4f"/>
          <SegmentURL media="video/1/seg-6.m4f"/>
          <SegmentURL media="video/1/seg-7.m4f"/>
          <SegmentURL media="video/1/seg-8.m4f"/>
          <SegmentURL media="video/1/seg-9.m4f"/>
          <SegmentURL media="video/1/seg-10.m4f"/>
          <SegmentURL media="video/1/seg-11.m4f"/>
          <SegmentURL media="video/1/seg-12.m4f"/>
          <SegmentURL media="video/1/seg-13.m4f"/>
          <SegmentURL media="video/1/seg-14.m4f"/>
          <SegmentURL media="video/1/seg-15.m4f"/>
        </SegmentList>
      </Representation>
    </AdaptationSet>
  </Period>
</MPD>
```

Let op: in het eerste voorbeeld hierboven wordt alleen naar één bestand voor elke stream verwezen, terwijl in het tweede voorbeeld naar een reeks kleine inhoudsfragmenten wordt verwezen. In plaats van expliciet naar fragmenten te verwijzen, kunt u ook een fragmentsjabloon definiëren, bijvoorbeeld:

```
<Representation bandwidth="348000" codecs="avc1.42c01e" height="360" id="1" width="640">
    <BaseURL>video/</BaseURL>
    <SegmentTemplate initialization="JaigoInit.mp4" media="Jaigo$Number$.m4s" startNumber="0" timescale="1000">
        <SegmentTimeline>
            <S d="4538" t="0"/>
            <S d="4304" t="4538"/>
            <S d="4004" t="8842"/>
            <S d="2102" t="12846"/>
        </SegmentTimeline>
    </SegmentTemplate>
</Representation>
```

In dit geval verwacht de inhoudsparser (TVSDK) video-inhoud te zoeken op Jaigo0.m4s, Jaigo1.m4s, Jaigo2.m4s, enzovoort. Dit wordt hoofdzakelijk gebruikt voor levende het stromen en heeft het voordeel dat het niet de cliënt vereist om manifest telkens opnieuw van tijd tot tijd te downloaden.
