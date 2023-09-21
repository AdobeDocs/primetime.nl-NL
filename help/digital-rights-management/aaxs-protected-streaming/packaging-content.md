---
title: Inhoud verpakken
description: Inhoud verpakken
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---

# Inhoud verpakken{#packaging-content}

Bij het verpakken van inhoud moet de URL van de licentieserver worden opgegeven. De Adobe Access Server URL heeft de volgende notatie:

```
http(s):// license-server-host:port/flashaccessserver/tenant-name
```

Bijvoorbeeld, voor de hostname van de licentieserver &quot;mylicenseserver.com&quot;luisterend op haven 8080 en een huurder genoemd &quot;huurder1&quot;, is de licentieserver URL om bij verpakkingstijd te specificeren:

```
https://mylicenseserver.com:8080/flashaccessserver/tenant1
```

Als elke huurder een verschillende Server van de Vergunning en van het Vervoer Credentials gebruikt, ben zeker om het correcte huurderscertificaat in de verpakker te specificeren.

Als u ervoor wilt zorgen dat de server alleen licenties uitgeeft voor inhoud die in een pakket is geplaatst door bekende verpakkers, neemt u het certificaat van de verpakker op in de lijst van gewenste personen van de pakketsoftware van het configuratiebestand voor de huurder.
