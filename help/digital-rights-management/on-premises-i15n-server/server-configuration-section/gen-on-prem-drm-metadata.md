---
title: De DRM-metagegevens op locatie genereren
description: De DRM-metagegevens op locatie genereren
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---

# De DRM-metagegevens op locatie genereren{#generate-the-on-premises-drm-metadata}

A [!DNL CreateMetadata.jar] wordt opgenomen in het [!DNL create_metadata] map. Het punt van dit nut is om te creëren op Bebouwen DRM Meta-gegevens die de cliënt in het uitvoeren van het individualisatieproces tegen gespecificeerde op de Server van de Individualisering van Bebouwen in werking zullen stellen.

1. Werk de Primetime DRM Reference Implementation - de Hulpmiddelen van de Lijn van het Bevel met de volgende dossiers bij:

   * [!DNL CreateMetadata.jar]
   * [!DNL commons-cli-1.2.jar]
   * [!DNL createMetadata.properties]

     De twee JAR-bestanden kunnen zich bevinden in de [!DNL Command Line Tools/libs] map. De [!DNL createMetadata.properties] bestand kan naast het [!DNL flashaccesstools.properties] bestand.

<!--<a id="example_2116349CA33642CD9293EAD94A532ED8"></a>-->

Ingesloten is een [!DNL examplecreate.sh] script dat een voorbeeld van het maken van metagegevens bevat. Configureer de URL van de licentieserver en de URL van de Individualization-server in zowel het script als de eigenschappenbestanden voordat u probeert metagegevens te genereren.

De inputs voor het hulpprogramma zijn als volgt:

* `createMetadata.properties` - Het eigenschappenbestand met een standaardbeleid, certificaatlocaties en wachtwoorden, enz.
* `indivCert` - PKCS12-bestand met certificaat voor individueel vervoer
* `indivURL` - URL van de On Premises Individualization Server

Het uitvoerbestand is een DRM-metagegevensbestand op locatie dat door de DRM-client wordt gebruikt. Bijvoorbeeld:

```
java -jar libs/CreateMetadata.jar -c createMetadata.properties -indivCert i15n_transport.cer
-indivURL https://[YOURINDIVSERVER:PORT] onpremdrm.metadata
```

.
