---
description: Adobe Offline Packager gebruikt als invoer van niet-gecodeerde MP4-inhoud.
title: Inhoud verpakken met Adobe Offline Packager
exl-id: 4433d76a-57c0-41e6-b358-5408b0fe87e7
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---

# Inhoud verpakken met Adobe Offline Packager{#package-your-content-with-adobe-offline-packager}

Adobe Offline Packager gebruikt als invoer van niet-gecodeerde MP4-inhoud.

**Adobe Offline Packager aanroepen**

Een typisch offlinepakketactivering van Adobe zou als de vraag hieronder kijken:

    java -jar OfflinePackager.jar -conf_path Content_PR_WV.xml -in_path &quot;Jaigo.mp4&quot;
    -out_path &quot;Jaigo_DASH&quot;
    -key_file_path &quot;Jaigo_DASH/_info/key.B64.random&quot;
    -widevine_key_id c595f214d84dc7ecf31a8ebf1b7ddda5
    -widevine_provider intertrust
    -playready_LA_URL
    http://pr.test.expressplay.com/playready/RightsManager.asmx
    -playready_keyid c595f214d84dc7ecf31a8ebf1b7ddda5
    -content_id c595f214d84dc7ecf31a8ebf1b7ddda5

In dit specifieke geval voegt de offlineverpakker zowel Widevine-inhoudsbeveiliging als PlayReady-inhoudsbeveiligingsinitialisatiegegevens toe aan de DASH-uitvoerinhoud. De waarde van `-key_file_path` is voor een base64-gecodeerde sleutel. De waarde van `-playready_LA_URL` is voor PlayReady-licentieverwerving.

Het argument conf_path verwijst naar het configuratiebestand dat het volgende zou bevatten:

    &lt;config>
    &lt;frag_dur>4&lt;/frag_dur>
    &lt;target_dur>6&lt;/target_dur>
    &lt;encrypt_audio>false&lt;/encrypt_audio>
    &lt;/config>

Omdat bepaalde Android-apparaten, met name Amazon Fire TV, geen ondersteuning bieden voor audiodecodering, is audiocodering optioneel.
