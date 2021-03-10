---
title: Inhoud verpakken
description: Inhoud verpakken
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---


# Inhoud verpakken{#packaging-content}

Wanneer het verpakken van inhoud voor verre zeer belangrijke levering, gebruik een beleid dat specificeert dat de verre zeer belangrijke levering wordt vereist. De URL van de toetsserver moet worden opgenomen in het M3U8 (manifestbestand) voor de HLS-inhoud. De URL van de primaire DRM-sleutelserver heeft de volgende indeling:

```
https://key-server-host:port/faxsks/tenant-name/key
```

Voor de hostnaam [!DNL mykeyserver.com] van Key Server die bijvoorbeeld luistert op poort 443 en een huurder met de naam `tenant1`, is de URL van de toetsserver die moet worden opgegeven in de M3U8:

```
https://mykeyserver.com:443/faxsks/tenant1/key
```

Dezelfde URL kan worden gebruikt voor zowel iOS- als Xbox 360-clients. Of als de server met afzonderlijke huurders voor elk cliënttype wordt gevormd, kunnen verschillende URLs worden gebruikt.

Dezelfde inhoud kan worden afgespeeld op clients waarvoor geen sleutelserver vereist is, mits de URL van de licentieserver verwijst naar een correct geconfigureerde uitvoeringslicentieserver.
