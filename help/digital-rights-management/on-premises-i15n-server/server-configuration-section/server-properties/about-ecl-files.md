---
seo-title: ECI-bestanden
title: ECI-bestanden
uuid: 124d8ab1-933b-4a1b-992a-919f3d799460
translation-type: tm+mt
source-git-commit: d8e4c39c297d69b154baf0b4d67cf09b5cf0a9d4

---


# ECI-bestanden{#about-eci-files}

Naast de CRL&#39;s moet u ook periodiek ingesloten ECI-bestanden (Common Interface) bijwerken. Wanneer Adobe ondersteuning toevoegt voor een nieuw Primetime DRM-clientplatform (bijvoorbeeld iOS, Android, Windows Flash Player, enz.) wordt een nieuwe ECI-record gemaakt. Om de individualisering van deze cliënt te steunen, moet een overeenkomstige ECI verslag op de Server van de Individualisatie aanwezig zijn.

Aangezien de release van nieuwe Primetime DRM-clients niet veel voorkomt, zal Adobe waar nodig bijgewerkte ECI-gegevens publiceren. Adobe verzamelt regelmatig ECI-bestanden en host deze op de onderstaande locatie voor distributie:

```
http://cdmdownload.adobe.com/indiv/onprem/eci/Latest.txt
```

Het [!DNL Latest.txt] bestand bevat de URL naar het meest recente CRL-distributiebestand.

Adobe maakt het ZIP-bestand van de ECI op de onderstaande manier:

Mapstructuur:

```
ECI\*
```

De inhoud van de map wordt recursief weergegeven:

```
zip -R ECI ECI.zip
```

Er wordt een OpenSSL SHA-256-overzicht berekend van het ZIP-bestand:

```
openssl dgst -sha256 -hex ECI.zip
```

De naam van het ZIP-bestand wordt gewijzigd in de archiefdatum en de SHA-256-samenvatting:

```
Rename ECI.zip to <DATE_SHA-256>.zip
```

Bijvoorbeeld:

```
20150310_aea45bf06241f04fba2b310ff9a8066c6aba73c8d22387b60509481e9cefc43e.zip
```

Controleer regelmatig de bovenstaande locatie op bijgewerkte ECI-bestanden.

Voer het volgende proces voor installatie na download uit:

1. Noteer de SHA-256-samenvatting en herberekend deze met OpenSSL of een vergelijkbaar gereedschap.
1. Vergelijk dit met de naam die u in de bestandsnaam hebt opgegeven.
1. Wijzig de naam van het bestand in [!DNL ECI.zip].
1. Pak de [!DNL ECI] directory uit.
1. Vervang de oude ECI-directory door de nieuwe.
1. Start de Individualization-server opnieuw.

