---
seo-title: Inhoud verpakken
title: Inhoud verpakken
uuid: 5d1d4b9d-f241-4291-9577-e9de5a8b92be
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---


# Inhoud verpakken{#packaging-content}

Bij het verpakken van inhoud moet de URL van de licentieserver worden opgegeven. De URL van de Adobe Access-server heeft de volgende indeling:

```
http(s):// license-server-host:port/flashaccessserver/tenant-name
```

Bijvoorbeeld, voor de hostname van de licentieserver &quot;mylicenseserver.com&quot;luisterend op haven 8080 en een huurder genoemd &quot;huurder1&quot;, is de licentieserver URL om bij verpakkingstijd te specificeren:

```
https://mylicenseserver.com:8080/flashaccessserver/tenant1
```

Als elke huurder een verschillende Server van de Vergunning en van het Vervoer Credentials gebruikt, ben zeker om het correcte huurderscertificaat in de verpakker te specificeren.

Als u ervoor wilt zorgen dat de server alleen licenties uitgeeft voor inhoud die is verpakt door bekende verpakkers, neemt u het certificaat van de verpakker op in de lijst met pakketmachtigingen van het configuratiebestand voor de huurder.
