---
description: De belangrijkste componenten van Primetime DRM bestaan uit een Java SDK en de Flash Player- en Adobe AIR-clientruntimeomgevingen.
seo-description: De belangrijkste componenten van Primetime DRM bestaan uit een Java SDK en de Flash Player- en Adobe AIR-clientruntimeomgevingen.
seo-title: Java SDK, Flash Player en Adobe AIR-client
title: Java SDK, Flash Player en Adobe AIR-client
uuid: e6daed27-3803-4ef7-ba25-4a180af7502f
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5

---


# Adobe Primetime DRM SDK {#section_522E57DFEEFF4794978FF2D366B83690}

Primetime DRM wordt geleverd als een Java SDK die de bouwstenen verstrekt waarvan u een serverimplementatie kunt tot stand brengen. Met de SDK kunt u een Primetime DRM-oplossing maken die geschikt is voor het bedrijfsmodel van uw organisatie.

De Java API&#39;s in de SDK worden in de volgende subsecties beschreven.

## Java API&#39;s voor het beheer van apparaatgroepdomeinen{#java-apis-for-managing-device-group-domains}

Deze APIs wordt gebruikt om de server toe te staan om cliëntverzoeken te behandelen om zich bij te sluiten van en het verlaten van de domeinen van de apparatengroep.

Een apparaatgroepdomein is een logische verzameling apparaten die licenties tussen elkaar kunnen delen. Dit kan alleen gebeuren als elk apparaat zich eerst bij hetzelfde domein aansluit/zich registreert. De Primetime DRM SDK, die op een server wordt uitgevoerd, moet de verzoeken van de de toetreding van het Domein van het Apparaat (register), evenals verzoeken van het de verlaten van het Domein van het Apparaat behandelen (deregister). Apparaten die niet zijn verbonden met een domein, krijgen licenties toegewezen die zijn gebonden aan dat apparaat, dat niet kan worden gedeeld met een ander apparaat.

## Java API&#39;s voor het beveiligen van inhoud{#java-apis-for-protecting-content}

Deze API&#39;s worden gebruikt om rechten te definiëren en inhoud voor te bereiden voor verspreiding. De API&#39;s voor inhoudsbeveiliging zijn:

* Beleidsbeheer

   De API voor beleidsbeheer wordt gebruikt om beleid te maken en te wijzigen dat op inhoud moet worden toegepast. Het beleid kan worden tot stand gebracht of worden bijgewerkt, met inbegrip van het krijgen/plaatsen van alle gebruiksregels en het toestaan van extra parameters in een douanenamespace.

* Inhoud verpakken

   De API voor het verpakken van inhoud wordt gebruikt om inhoud te coderen en metagegevens van de inhoud in het pakket op te halen.

## Java API&#39;s voor het afgeven van licenties{#java-apis-for-issuing-licenses}

Deze API&#39;s worden gebruikt wanneer een client een licentie aanvraagt bij de server. De SDK ondersteunt de volgende verzoeken van de client:

* Verificatie

   De verificatie-API kan worden gebruikt om verificatieaanvragen af te handelen en verificatietokens te genereren.

* Vergunning genereren en verwerven

   De licentie-API voor genereren en aanschaffen wordt gebruikt om een licentie voor de gebruiker te genereren.

* Ondersteuning voor Adobe AIR versie 1.5-clients en -inhoud

   Met het oog op achterwaartse compatibiliteit heeft de SDK API&#39;s voor het afhandelen van aanvragen van AIR-toepassingen die zijn gemaakt voor gebruik met AIR versie 1.5 en eerdere clients en beveiligde inhoud.

## Referentie-implementatie {#reference-implementation}

De SDK bevat een voorbeeldimplementatie, een eenvoudige Adobe Primetime DRM-implementatie die aantoont hoe u de Java API&#39;s kunt gebruiken. De voorbeeldimplementatie biedt een licentieserver, een gecontroleerde mapverpakker, een Primetime DRM Manager AIR-toepassing en opdrachtregelprogramma&#39;s voor het verpakken van inhoud en beleidsbeheer op basis van de Java API&#39;s. Zie Inhoud beschermen voor meer informatie over de Primetime DRM-voorbeeldimplementatie.