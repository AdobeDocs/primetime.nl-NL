---
seo-title: Inhoud verpakken
title: Inhoud verpakken
uuid: 366c8470-b7ef-4a39-83c2-151ba9be9a32
translation-type: tm+mt
source-git-commit: 1547eb3dd220fafc08df923f40504736c16a866c

---


# Inhoud verpakken{#packaging-content}

Wanneer het verpakken van inhoud voor verre zeer belangrijke levering, gebruik een beleid dat specificeert dat de verre zeer belangrijke levering wordt vereist. De URL van de toetsserver moet worden opgenomen in het M3U8 (manifestbestand) voor de HLS-inhoud. De URL van de primaire DRM-sleutelserver heeft de volgende indeling:

```
https://key-server-host:port/faxsks/tenant-name/key
```

Bijvoorbeeld, voor de zeer belangrijke gastheernaam van de Server die op haven 443 [!DNL mykeyserver.com] luistert, en een huurder genoemd `tenant1`, is de belangrijkste server URL in M3U8 te specificeren:

```
https://mykeyserver.com:443/faxsks/tenant1/key
```

Dezelfde URL kan worden gebruikt voor zowel iOS- als Xbox 360-clients. Of als de server met afzonderlijke huurders voor elk cliënttype wordt gevormd, kunnen verschillende URLs worden gebruikt.

Dezelfde inhoud kan worden afgespeeld op clients waarvoor geen sleutelserver vereist is, mits de URL van de licentieserver verwijst naar een correct geconfigureerde uitvoeringslicentieserver.
