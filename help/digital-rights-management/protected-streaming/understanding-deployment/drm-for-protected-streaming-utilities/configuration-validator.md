---
description: Adobe adviseert dat als u veranderingen in het configuratiedossier aanbrengt, u het nut van Validator van de Configuratie zou moeten in werking stellen alvorens u de server begint. Dit nut kan de meeste configuratiefouten vroeg ontdekken, alvorens zij mislukkingen tijdens verzoekverwerking veroorzaken.
title: Configuratievalidator
exl-id: 41d0a926-4e12-442c-886e-5f12cf10eed8
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---

# Configuratievalidator{#configuration-validator}

Adobe adviseert dat als u veranderingen in het configuratiedossier aanbrengt, u het nut van Validator van de Configuratie zou moeten in werking stellen alvorens u de server begint. Dit nut kan de meeste configuratiefouten vroeg ontdekken, alvorens zij mislukkingen tijdens verzoekverwerking veroorzaken.

Typ het volgende als u de validator wilt uitvoeren:

```
Validator.bat  
<i class="+ topic ph hi-d="" i "="">
  options  
</i class="+ topic>
```

of

```
java -jar libs/flashaccess-validator.jar  
<i class="+ topic ph hi-d="" i "="">
  options 
</i class="+ topic>
```

Voor elk van de configuratiedossiers van de vergunningsserver, kan Validator op dossier-gebaseerde bevestiging uitvoeren, die ervoor zorgt dat het dossier van XML correct is gevormd en met het schema van het configuratiedossier in overeenstemming is.

Als u op een bestand gebaseerde validatie wilt uitvoeren op het algemene configuratiebestand, typt u:

```
Validator --<file path>/flashaccess-global.xml --global
```

Om op dossier-gebaseerde bevestiging op het dossier van de huurdersconfiguratie uit te voeren, typ:

```
Validator --<file path>/flashaccess-tenant.xml --tenant
```

Validator kan plaatsing-gebaseerde bevestiging ook uitvoeren. Naast het controleren van conformiteit met het schema, verifieert dit niveau van bevestiging ook dat de waarden die u specificeerde geldig zijn. Zo zorgt de code ervoor dat bestanden waarnaar wordt verwezen, bestaan.

Op implementatie gebaseerde validatie kan op de volgende niveaus worden uitgevoerd:

* `Tenant` — Valideert het configuratiedossier en geloofsbrieven voor een specifieke huurder. Als u de configuratie voor wilt bevestigen `<tenant1>`, type:

   ```
       Validator --<root-path-to-LicenseServer.ConfigRoot> -d flashaccessserver/tenant1 -t
   ```

* `Global` — Valideert het algemene configuratiebestand en de validatie van de huurder voor alle huurders. Als u globale plaatsing-gebaseerde bevestiging wilt uitvoeren, type:

   ```
       Validator --<root-path-to-LicenseServer.ConfigRoot> -g
   ```
