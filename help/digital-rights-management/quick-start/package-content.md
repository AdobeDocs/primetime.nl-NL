---
seo-title: Gecodeerde inhoud verpakken
title: Gecodeerde inhoud verpakken
uuid: 1e271167-107d-41df-8a7c-3075cb3acc0c
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---


# Gecodeerde inhoud verpakken{#package-encrypted-content}

1. Kopieer de map `<Primetime DRM DVD>\Reference Implementation\Command Line Tools\` naar uw lokale bestandssysteem.
1. Werk in uw lokale `Command Line Tools\`-map het `flashaccesstools.properties`-bestand bij om met uw server te werken.

   U moet ten minste de volgende eigenschappen wijzigen:

   * `encrypt.keys.asymmetric.certfile=[license-server-certificate.cer]`: Het pad naar het certificaat van uw licentieserver (het eindigt gewoonlijk met  [!DNL .cer],  [!DNL .der] of  [!DNL .pem]).

   * `encrypt.license.serverurl=[license-server-url]`: De URL van uw licentieserver, bijvoorbeeld:     `https://<License Server Hostname>:8080/flashaccessserver/sampletenant`.

   * `encrypt.license.servercert=[transport-certificate.cer]`: De weg aan uw certificaat van het Vervoer (het eindigt gewoonlijk met  [!DNL .cer],  [!DNL .der], of  [!DNL .pem]).

   * `encrypt.sign.certfile=[packager-credentials.pfx]`: Het pad naar het Packager-certificaat (dit eindigt bij  [!DNL .pfx]).

   * `encrypt.sign.certpass=[password]`: Het wachtwoord voor uw certificaat van Packager.
   >[!NOTE]
   >
   >Zorg ervoor dat u het wachtwoord niet sleept.

1. Maak een beleid.

   Voer de volgende opdracht uit in uw lokale map `Command Line Tools\`:

   ```
   java -jar libs/AdobePolicyManager.jar new examplepolicy.pol -n examplepolicy -x
   ```

   Met deze opdracht maakt u een beleidsbestand met de naam [!DNL examplepolicy.pol] dat anonieme verificatie van de licentieserver gebruikt (de optie `-x`).
1. Kopieer het MP4-, FLV- of F4V-videobestand dat u wilt coderen naar uw lokale `Command Line Tools\`-map.
1. Verpak uw inhoud.

   Stel dat uw bronvideobestand [!DNL sample.mp4] is. Voer de volgende opdracht uit in uw lokale map `Command Line Tools\`:

   ```
   java -jar libs/AdobePackager.jar sample.mp4 sample_encrypted.mp4 -p examplepolicy.pol
   ```

   >[!NOTE]
   >
   >Als u HLS-, HDS- of DASH-inhoud wilt verpakken, moet u een ander pakketprogramma gebruiken, zoals [Adobe Primetime Offline Packager](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf).

1. Kopieer de gecodeerde bestandsobjecten (in dit geval [!DNL sample_encrypted.mp4] en [!DNL sample_encrypted.mp4.metadata]) naar `<Your Content Server - Tomcat Install Dir>\webapps\ROOT`.

U hebt nu de verpakkingsfase van het proces voltooid.

>[!NOTE]
>
>Zie [Adobe Primetime DRM Command-line tools](../drm-reference-implementations/command-line-tools/command-line-tools-overview.md) voor gedetailleerde informatie over opdrachtregelprogramma&#39;s voor het verpakken van inhoud, het maken van beleid en meer.
