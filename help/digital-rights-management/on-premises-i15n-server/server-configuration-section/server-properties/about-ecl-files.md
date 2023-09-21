---
title: ECI-bestanden
description: ECI-bestanden
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# ECI-bestanden{#about-eci-files}

Naast de CRL&#39;s moet u ook periodiek ingesloten ECI-bestanden (Common Interface) bijwerken. Telkens wanneer Adobe ondersteuning toevoegt voor een nieuw Primetime DRM-clientplatform (bijvoorbeeld iOS, Android, Windows Flash Player enz.), wordt een nieuwe ECI-record gemaakt. Om de individualisering van deze cliënt te steunen, moet een overeenkomstige ECI verslag op de Server van de Individualisatie aanwezig zijn.

Aangezien de release van nieuwe Primetime DRM-clients niet veel voorkomt, zal de Adobe zo nodig bijgewerkte ECI-gegevens vrijgeven. De Adobe verzamelt regelmatig ECI-bestanden en host deze op de onderstaande locatie voor distributie:

```
http://cdmdownload.adobe.com/indiv/onprem/eci/Latest.txt
```

De [!DNL Latest.txt] Het bestand bevat de URL naar het meest recente CRL-distributiebestand.

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
1. De naam van het bestand wijzigen in [!DNL ECI.zip].
1. Pak de [!DNL ECI] directory.
1. Vervang de oude ECI-directory door de nieuwe.
1. Start de Individualization-server opnieuw.
