---
title: Inhoud verpakken
description: Inhoud verpakken
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---

# Inhoud verpakken{#packaging-content}

Wanneer het verpakken van inhoud voor verre zeer belangrijke levering, gebruik een beleid dat specificeert dat de verre zeer belangrijke levering wordt vereist. De URL van de toetsserver moet worden opgenomen in het M3U8 (manifestbestand) voor de HLS-inhoud. De URL van de primaire DRM-sleutelserver heeft de volgende indeling:

```
https://key-server-host:port/faxsks/tenant-name/key
```

Bijvoorbeeld voor hostnaam van sleutelserver [!DNL mykeyserver.com] luisteren op haven 443, en een genoemde huurder `tenant1`De URL van de toetsserver die in de M3U8 moet worden opgegeven, is:

```
https://mykeyserver.com:443/faxsks/tenant1/key
```

Dezelfde URL kan worden gebruikt voor zowel iOS- als Xbox 360-clients. Of als de server met afzonderlijke huurders voor elk cliënttype wordt gevormd, kunnen verschillende URLs worden gebruikt.

Dezelfde inhoud kan worden afgespeeld op clients waarvoor geen sleutelserver vereist is, mits de URL van de licentieserver verwijst naar een correct geconfigureerde uitvoeringslicentieserver.
