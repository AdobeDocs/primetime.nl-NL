---
seo-title: Configuratie-validatie
title: Configuratie-validatie
uuid: 60ebd35c-290a-4f08-9bd0-178903857149
translation-type: tm+mt
source-git-commit: 47b2ed65ff0ea4f54a210cf7627ed535782296b9
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---


# Configuratievalidering {#configuration-validator}

Adobe raadt u aan het hulpprogramma Configuration Validator uit te voeren voordat u de server start wanneer wijzigingen in het configuratiebestand worden aangebracht. Dit nut kan de meeste configuratiefouten vroeg ontdekken, alvorens zij mislukkingen tijdens verzoekverwerking veroorzaken.

Gebruik de opdracht om de validator uit te voeren:

```
Validator.bat options  
```

of de opdracht:

```
java -jar libs/flashaccess-validator.jar options 
```

Voor elk van de configuratiedossiers van de vergunningsserver, kan Validator op dossier-gebaseerde bevestiging uitvoeren, die ervoor zorgt het dossier van XML behoorlijk gevormd is en met het schema van het configuratiedossier in overeenstemming is. Voer de opdracht uit om bestandsgebaseerde validatie uit te voeren op het algemene configuratiebestand:

```
Validator --file path/flashaccess-global.xml --global
```

Om op dossier-gebaseerde bevestiging op het dossier van de huurdersconfiguratie uit te voeren, stel het bevel in werking:

```
Validator --file path/flashaccess-tenant.xml --tenant
```

Validator kan ook op plaatsing-gebaseerde bevestiging uitvoeren; naast het controleren van de conformiteit met het schema, controleert dit niveau van bevestiging ook dat de gespecificeerde waarden geldig zijn (bijvoorbeeld, verzekert het dat de referenced dossiers bestaan). Op implementatie gebaseerde validatie kan op twee niveaus worden uitgevoerd:

* Aannemer — bevestigt configuratiedossier en geloofsbrieven voor een specifieke huurder. Om de configuratie voor &quot;huurder1&quot;te bevestigen, stel het bevel in werking:

```
Validator --root-path-to-LicenseServer.ConfigRoot -d flashaccessserver/tenant1 -t 
```

* Algemeen — Valideert het algemene configuratiebestand en de validatie van de huurder voor alle huurders. Voer de opdracht uit om globale validatie op basis van implementatie uit te voeren:

```
Validator --root-path-to-LicenseServer.ConfigRoot -g 
```

