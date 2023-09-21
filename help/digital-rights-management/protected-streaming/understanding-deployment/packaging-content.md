---
description: Wanneer u inhoud verpakt, moet u de URL van de licentieserver opgeven.
title: Inhoud verpakken
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---

# Inhoud verpakken{#packaging-content}

Wanneer u inhoud verpakt, moet u de URL van de licentieserver opgeven.

De URL van de Adobe Primetime DRM-server gebruikt de volgende indeling:

```
http(s)://<license-server-host:port>/flashaccessserver/<tenant-name>
```

Bijvoorbeeld voor hostnaam van licentieserver `mylicenseserver.com` die op haven 8080, en een huurder richt *`tenant1`* U gebruikt dan de volgende syntaxis voor de URL van de licentieserver die u opgeeft op het moment dat u inhoud verpakt:

```
https://mylicenseserver.com:8080/flashaccessserver/tenant1
```

Als elke huurder een verschillende Server van de Vergunning en van het Vervoer Credentials gebruikt, zorg ervoor dat u het correcte huurderscertificaat in de verpakker specificeert.

Als u ervoor wilt zorgen dat de server vergunningen slechts aan inhoud van bekende verpakkers uitgeeft, moet u het certificaat van de verpakker in de pakketsoftware lijst van gewenste personen van het dossier van de huurdersconfiguratie omvatten.
