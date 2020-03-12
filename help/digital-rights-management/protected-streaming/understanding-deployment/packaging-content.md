---
description: Wanneer u inhoud verpakt, moet u de URL van de licentieserver opgeven.
seo-description: Wanneer u inhoud verpakt, moet u de URL van de licentieserver opgeven.
seo-title: Inhoud verpakken
title: Inhoud verpakken
uuid: 2e47a9a2-bbc6-4995-8ce5-6ca6b116349b
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Inhoud verpakken{#packaging-content}

Wanneer u inhoud verpakt, moet u de URL van de licentieserver opgeven.

De URL van de Adobe Primetime DRM-server gebruikt de volgende indeling:

```
http(s)://<license-server-host:port>/flashaccessserver/<tenant-name>
```

Bijvoorbeeld, voor de hostname van de vergunningsserver `mylicenseserver.com` die op haven 8080 luistert, en een huurder riep *`tenant1`*, zou u de volgende syntaxis voor de vergunningsserver URL gebruiken die u op de tijd specificeert dat u inhoud verpakt:

```
https://mylicenseserver.com:8080/flashaccessserver/tenant1
```

Als elke huurder een verschillende Server van de Vergunning en van het Vervoer Credentials gebruikt, zorg ervoor dat u het correcte huurderscertificaat in de verpakker specificeert.

Als u ervoor wilt zorgen dat de server vergunningen slechts aan inhoud van bekende verpakkers uitgeeft, moet u het certificaat van de verpakker in de pakketwhitelist van het dossier van de huurdersconfiguratie omvatten.
