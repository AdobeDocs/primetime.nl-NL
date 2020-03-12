---
description: Adobe Offline Packager neemt niet-gecodeerde MP4-inhoud in.
seo-description: Adobe Offline Packager neemt niet-gecodeerde MP4-inhoud in.
seo-title: Inhoud verpakken met Adobe Offline Packager
title: Inhoud verpakken met Adobe Offline Packager
uuid: d0676147-c20f-49ea-93a6-9c8dbbbba992
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c

---


# Inhoud verpakken met Adobe Offline Packager{#package-your-content-with-adobe-offline-packager}

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
