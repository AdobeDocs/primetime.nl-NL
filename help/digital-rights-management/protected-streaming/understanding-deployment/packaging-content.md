---
description: Wanneer u inhoud verpakt, moet u de URL van de licentieserver opgeven.
title: Inhoud verpakken
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
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

Bijvoorbeeld, voor de hostnaam van de licentieserver `mylicenseserver.com` die op haven 8080 luistert, en een huurder genoemd *`tenant1`*, zou u de volgende syntaxis voor de vergunningsserver URL gebruiken die u op het tijdstip specificeert dat u inhoud verpakt:

```
https://mylicenseserver.com:8080/flashaccessserver/tenant1
```

Als elke huurder een verschillende Server van de Vergunning en van het Vervoer Credentials gebruikt, zorg ervoor dat u het correcte huurderscertificaat in de verpakker specificeert.

Als u ervoor wilt zorgen dat de server vergunningen slechts aan inhoud van bekende verpakkers uitgeeft, moet u het certificaat van de verpakker in de pakketsoftware lijst van gewenste personen van het dossier van de huurdersconfiguratie omvatten.
