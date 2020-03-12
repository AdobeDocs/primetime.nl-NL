---
description: We gebruiken zowel de Bento4-pakketsoftware als de Adobe offline-pakketsoftware om gecodeerde DASH-inhoud te ontwerpen. Bento4 neemt als invoer niet-gecodeerde MP4-inhoud.
seo-description: We gebruiken zowel de Bento4-pakketsoftware als de Adobe offline-pakketsoftware om gecodeerde DASH-inhoud te ontwerpen. Bento4 neemt als invoer niet-gecodeerde MP4-inhoud.
seo-title: Verpak uw inhoud met Bento4
title: Verpak uw inhoud met Bento4
uuid: 88323a4e-d0b5-4a41-acec-7126d3e0c90b
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c

---


# Inhoud verpakken voor Windows en PlayReady {#package-for-widevine}

We gebruiken zowel de Bento4-pakketsoftware als de Adobe offline-pakketsoftware om gecodeerde DASH-inhoud te ontwerpen. Bento4 neemt als invoer niet-gecodeerde MP4-inhoud.

## Verpak uw inhoud met Bento4{#package-your-content-with-bento}

De Bento4-verpakker verwacht dat de invoer-MP4 vooraf gefragmenteerd is. De distributie van het Bento4-pakket bevat hiervoor een gereedschap.

**Bento4 aanroepen**

Bento4-pakketaanroepen zien er als volgt uit:

    ./mp4dash
    -f
    —use-segment-list
    —use-segment-timeline
    —subtitles
    —encryption-key=7cc7f0470019ac10d06bca13a580a9ff:5fa05f94e8cd 09fc0747c7c5ac215b3b
    —widevine
    —widevine-header=provider:intertrust#content_id:2a &quot;CC_300_640x360.mp4&quot;
    -o &quot;CC_300_640x36 0_DASH&quot;
>
    ./mp4dash
    -f
    —use-segment-list
    —use-segment-timeline
    —subtitles
    —encryption-key=7cc7f0470019ac10d06bca13a580a9ff:5fa05f94e8cd 09fc0747c7c5ac215b3b
    —playready
    —playready-header=\&quot;LA_URL:http://pr.test.expressplay.com/playready/RightsManager.asmx\&quot;

In het onderstaande voorbeeld worden PlayReady- en Windows-schema&#39;s gecombineerd. In dit specifieke geval voegt de verpakker zowel Widevine-inhoudsbeveiliging als PlayReady-gegevens voor inhoudsbeveiliging toe aan de DASH-uitvoerinhoud.

    /mp4dash
    -f
    —use-segment-list
    —use-segment-timeline
    —subtitles
    —encryption-key=7cc7f0470019ac10d06bca13a580a9ff:5fa05f94e8cd 09fc0747c7c5ac215b3b
    —playready
    —playready-header=\&quot;LA_URL:http://pr.test.expressplay.com/playready/RightsManager.asmx\&quot;
    —widevine
    —widevine-header=provider:intertrust#content_id:2a &quot;CC_300_640x360.mp4&quot;
    
    
    -o &quot;CC_300_640x360_DASH&quot;where

De waarde voor de `--encryption-key` markering is in de vorm `<base16 encoded key id>:<base16 encoded encryption key>`.

De `--widevine-header=provider:intertrust#content_id:2a` vlag vertelt de verpakker om de pssh doos in manifest op te nemen, die TVSDK momenteel voor playback vereist.
De waarde voor `-playready-header` is voor de verwerving van een PlayReady-licentie.

## Inhoud verpakken met Adobe Offline Packager {#package-your-content-with-adobe-offline-packager}

Adobe Offline Packager neemt niet-gecodeerde MP4-inhoud in.

**Adobe Offline Packager aanroepen**

Een typisch offlinepakketactivering van Adobe zou als de vraag hieronder kijken:

    java -jar OfflinePackager.jar -conf_path Content_PR_WV.xml -in_path &quot;Jaigo.mp4&quot;
    -out_path &quot;Jaigo_DASH&quot;
    -key_file_path &quot;Jaigo_DASH/_info/key.B64.random&quot;
    -widevine_key_id c595f214d84dc7ecc f31a8ebf1b7ddda5
    -widevine_provider intertrust
    -playready_LA_
    URLhttp://pr.test.expressplay.com/playready/RightsManager.asmx
    -playready_keyid c595f214d84dc7ecf31a8ebf1b7ddda5
    -content_id c595f2 14d84dc7ecf31a8ebf1b7ddda5

In dit specifieke geval voegt de offlineverpakker zowel Widevine-inhoudsbeveiliging als PlayReady-inhoudsbeveiligingsinitialisatiegegevens toe aan de DASH-uitvoerinhoud. De waarde van `-key_file_path` is voor een base64-gecodeerde sleutel. De waarde van `-playready_LA_URL` is voor de verwerving van een PlayReady-licentie.

Het argument conf_path verwijst naar het configuratiebestand dat het volgende zou bevatten:

    &lt;config>
    &lt;frag_dur>4&lt;/frag_dur>
    &lt;target_dur>6&lt;/target_dur>
    &lt;encrypt_audio>false&lt;/encrypt_audio>
    &lt;/config>

Omdat bepaalde Android-apparaten, met name Amazon Fire TV, geen ondersteuning bieden voor audiodecodering, is audiocodering optioneel.