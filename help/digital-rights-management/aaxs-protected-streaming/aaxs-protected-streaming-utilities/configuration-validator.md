---
title: Configuratie-validatie
description: Configuratie-validatie
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# Configuratie-validatie {#configuration-validator}

De Adobe adviseert lopende het nut van Validator van de Configuratie alvorens de server te beginnen om het even welke tijd veranderingen in het configuratiedossier worden aangebracht. Dit nut kan de meeste configuratiefouten vroeg ontdekken, alvorens zij mislukkingen tijdens verzoekverwerking veroorzaken.

Gebruik de opdracht om de validator uit te voeren:

```
Validator.bat options  
```

of de opdracht:

```
java -jar libs/flashaccess-validator.jar options 
```

Voor elk van de configuratiedossiers van de vergunningsserver, kan Validator op dossier-gebaseerde bevestiging uitvoeren, die ervoor zorgt het dossier van XML behoorlijk gevormd is en aan het schema van het configuratiedossier voldoet. Voer de opdracht uit om bestandsgebaseerde validatie uit te voeren op het algemene configuratiebestand:

```
Validator --file path/flashaccess-global.xml --global
```

Om op dossier-gebaseerde bevestiging op het dossier van de huurdersconfiguratie uit te voeren, stel het bevel in werking:

```
Validator --file path/flashaccess-tenant.xml --tenant
```

Validator kan plaatsing-gebaseerde bevestiging ook uitvoeren; naast het controleren van conformiteit met het schema, controleert dit niveau van bevestiging ook dat de gespecificeerde waarden geldig zijn (bijvoorbeeld, zorgt het ervoor dat de referenced dossiers bestaan). Op implementatie gebaseerde validatie kan op twee niveaus worden uitgevoerd:

* Aannemer — bevestigt configuratiedossier en geloofsbrieven voor een specifieke huurder. Om de configuratie voor &quot;huurder1&quot;te bevestigen, stel het bevel in werking:

```
Validator --root-path-to-LicenseServer.ConfigRoot -d flashaccessserver/tenant1 -t 
```

* Algemeen — Valideert het algemene configuratiebestand en de validatie van de huurder voor alle huurders. Om globale plaatsing-gebaseerde bevestiging uit te voeren, stel het bevel in werking:

```
Validator --root-path-to-LicenseServer.ConfigRoot -g 
```
