---
title: Gecodeerde inhoud verpakken
description: Gecodeerde inhoud verpakken
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Gecodeerde inhoud verpakken{#package-encrypted-content}

1. De `<Primetime DRM DVD>\Reference Implementation\Command Line Tools\` aan uw lokale bestandssysteem.
1. In uw lokale `Command Line Tools\` map, update de `flashaccesstools.properties` bestand om met uw server te werken.

   U moet ten minste de volgende eigenschappen wijzigen:

   * `encrypt.keys.asymmetric.certfile=[license-server-certificate.cer]`: Het pad naar het certificaat van de licentieserver (het eindigt gewoonlijk met [!DNL .cer], [!DNL .der] of [!DNL .pem]).

   * `encrypt.license.serverurl=[license-server-url]`: De URL van uw licentieserver, bijvoorbeeld:    `https://<License Server Hostname>:8080/flashaccessserver/sampletenant`.

   * `encrypt.license.servercert=[transport-certificate.cer]`: De weg aan uw certificaat van het Vervoer (het eindigt gewoonlijk met [!DNL .cer], [!DNL .der], of [!DNL .pem]).

   * `encrypt.sign.certfile=[packager-credentials.pfx]`: Het pad naar uw Packager-certificaat (dit eindigt bij [!DNL .pfx]).

   * `encrypt.sign.certpass=[password]`: Het wachtwoord voor uw Packager-certificaat.

   >[!NOTE]
   >
   >Zorg ervoor dat u het wachtwoord niet sleept.

1. Maak een beleid.

   In uw lokale `Command Line Tools\` en voert u de volgende opdracht uit:

   ```
   java -jar libs/AdobePolicyManager.jar new examplepolicy.pol -n examplepolicy -x
   ```

   Met deze opdracht maakt u een beleidsbestand met de naam [!DNL examplepolicy.pol] die anonieme verificatie van de licentieserver gebruikt (de `-x` ).
1. Kopieer het MP4-, FLV- of F4V-videobestand dat u wilt coderen naar uw lokale computer `Command Line Tools\` map.
1. Verpak uw inhoud.

   Laten we zeggen dat uw bronvideobestand [!DNL sample.mp4]. In uw lokale `Command Line Tools\` en voert u de volgende opdracht uit:

   ```
   java -jar libs/AdobePackager.jar sample.mp4 sample_encrypted.mp4 -p examplepolicy.pol
   ```

   >[!NOTE]
   >
   >Als u HLS-, HDS- of DASH-inhoud wilt verpakken, moet u een ander pakketprogramma gebruiken, zoals [Adobe Primetime Offline Packager](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf).

1. Kopieer de versleutelde elementen (in dit geval [!DNL sample_encrypted.mp4] en [!DNL sample_encrypted.mp4.metadata]) naar `<Your Content Server - Tomcat Install Dir>\webapps\ROOT`.

Op dit moment hebt u de verpakkingsfase van het proces voltooid.

>[!NOTE]
>
>Zie voor meer informatie over opdrachtregelprogramma&#39;s voor het verpakken van inhoud, het maken van beleid en meer [Adobe Primetime DRM-opdrachtregelprogramma&#39;s](../drm-reference-implementations/command-line-tools/command-line-tools-overview.md).
