---
description: We gebruiken zowel de Bento4-pakketsoftware als de Adobe offline-pakketsoftware om gecodeerde DASH-inhoud te ontwerpen. Bento4 neemt als invoer niet-gecodeerde MP4-inhoud.
title: Verpak uw inhoud met Bento4
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---


# Inhoud verpakken voor Windows en PlayReady {#package-for-widevine}

We gebruiken zowel de Bento4-pakketsoftware als de Adobe offline-pakketsoftware om gecodeerde DASH-inhoud te ontwerpen. Bento4 neemt als invoer niet-gecodeerde MP4-inhoud.

## Verpak uw inhoud met Bento4{#package-your-content-with-bento}

De Bento4-verpakker verwacht dat de invoer-MP4 vooraf gefragmenteerd is. De distributie van het Bento4-pakket bevat hiervoor een gereedschap.

**Bento4 aanroepen**

Bento4-pakketaanroepen zien er als volgt uit:

```
./mp4dash
-f
--use-segment-list
--use-segment-timeline
--subtitles
--encryption-key=7cc7f0470019ac10d06bca13a580a9ff:5fa05f94e8cd09fc0747c7c5ac215b3b
--widevine
--widevine-header=provider:intertrust#content_id:2a "CC_300_640x360.mp4"
-o "CC_300_640x360_DASH"
```

```
./mp4dash
-f
--use-segment-list
--use-segment-timeline
--subtitles
--encryption-key=7cc7f0470019ac10d06bca13a580a9ff:5fa05f94e8cd09fc0747c7c5ac215b3b
--playready
--playready-header=\"LA_URL:http://pr.test.expressplay.com/playready/RightsManager.asmx\"
```

In het onderstaande voorbeeld worden PlayReady- en Windows-schema&#39;s gecombineerd. In dit specifieke geval voegt de verpakker zowel Widevine-inhoudsbeveiliging als PlayReady-gegevens voor inhoudsbeveiliging toe aan de DASH-uitvoerinhoud.

```
/mp4dash
-f
--use-segment-list
--use-segment-timeline
--subtitles
--encryption-key=7cc7f0470019ac10d06bca13a580a9ff:5fa05f94e8cd09fc0747c7c5ac215b3b
--playready
--playready-header=\"LA_URL:http://pr.test.expressplay.com/playready/RightsManager.asmx\"
--widevine
--widevine-header=provider:intertrust#content_id:2a "CC_300_640x360.mp4"
-o "CC_300_640x360_DASH"
```

waar

De waarde voor de markering `--encryption-key` is in de vorm `<base16 encoded key id>:<base16 encoded encryption key>`.

De `--widevine-header=provider:intertrust#content_id:2a` vlag vertelt de pakketmanager om de doos pssh in manifest op te nemen, die TVSDK momenteel voor playback vereist.

De waarde voor `-playready-header` is voor de verwerving van een PlayReady-licentie.

## Verpak uw inhoud met Adobe Offline Packager {#package-your-content-with-adobe-offline-packager}

Adobe Offline Packager gebruikt als invoer van niet-gecodeerde MP4-inhoud.

**Adobe Offline Packager aanroepen**

Een typisch offlinepakketactivering van Adobe zou als de vraag hieronder kijken:

```
java -jar OfflinePackager.jar -conf_path Content_PR_WV.xml -in_path "Jaigo.mp4"
-out_path "Jaigo_DASH"
-key_file_path "Jaigo_DASH/_info/key.B64.random"
-widevine_key_id c595f214d84dc7ecf31a8ebf1b7ddda5
-widevine_provider intertrust
-playready_LA_URL
http://pr.test.expressplay.com/playready/RightsManager.asmx
-playready_keyid c595f214d84dc7ecf31a8ebf1b7ddda5
-content_id c595f214d84dc7ecf31a8ebf1b7ddda5
```

In dit specifieke geval voegt de offlineverpakker zowel Widevine-inhoudsbeveiliging als PlayReady-inhoudsbeveiligingsinitialisatiegegevens toe aan de DASH-uitvoerinhoud. De waarde van `-key_file_path` is voor een base64-gecodeerde sleutel. De waarde van `-playready_LA_URL` is voor de verwerving van een PlayReady-licentie.

Het argument conf_path verwijst naar het configuratiebestand dat het volgende zou bevatten:

```
<config>
<frag_dur>4</frag_dur>
<target_dur>6</target_dur>
<encrypt_audio>false</encrypt_audio>
</config>
```

Omdat bepaalde Android-apparaten, met name Amazon Fire TV, geen ondersteuning bieden voor audiodecodering, is audiocodering optioneel.
