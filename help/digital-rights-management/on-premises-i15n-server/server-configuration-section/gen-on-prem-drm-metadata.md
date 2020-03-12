---
seo-title: De DRM-metagegevens op locatie genereren
title: De DRM-metagegevens op locatie genereren
uuid: 89d53924-1a8d-42d4-a716-ce4f4566b6bf
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# De DRM-metagegevens op locatie genereren{#generate-the-on-premises-drm-metadata}

Een [!DNL CreateMetadata.jar] hulpprogramma wordt opgenomen in de [!DNL create_metadata] map. Het punt van dit nut is om te creëren op Bebouwen DRM Meta-gegevens die de cliënt in het uitvoeren van het individualisatieproces tegen gespecificeerde op de Server van de Individualisering van Bebouwen in werking zullen stellen.

1. Werk de Primetime DRM Reference Implementation - de Hulpmiddelen van de Lijn van het Bevel met de volgende dossiers bij:

   * [!DNL CreateMetadata.jar]
   * [!DNL commons-cli-1.2.jar]
   * [!DNL createMetadata.properties]

      De twee JAR-bestanden kunnen zich in de [!DNL Command Line Tools/libs] map bevinden. Het [!DNL createMetadata.properties] bestand kan zich naast het [!DNL flashaccesstools.properties] bestand bevinden.

<!--<a id="example_2116349CA33642CD9293EAD94A532ED8"></a>-->

Ingesloten is een [!DNL examplecreate.sh] script dat een voorbeeld van het maken van metagegevens weergeeft. Configureer de URL van de licentieserver en de URL van de Individualization-server in zowel het script als de eigenschappenbestanden voordat u probeert metagegevens te genereren.

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