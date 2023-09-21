---
description: De belangrijkste onderdelen van Adobe Access bestaan uit een Java SDK en de Flash Player- en Adobe AIR-clientruntimeomgevingen.
title: Java SDK, Flash Player en Adobe AIR-client
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '910'
ht-degree: 0%

---

# Adobe Access-componenten{#adobe-access-components}

De belangrijkste onderdelen van Adobe Access bestaan uit een Java SDK en de Flash Player- en Adobe AIR-clientruntimeomgevingen.

Zie De SDK instellen in voor meer informatie over het instellen van de SDK. *De Adobe Access SDK gebruiken voor het beveiligen van inhoud.*

Met de Adobe Access SDK kunt u een oplossing voor digitaal rechtenbeheer ontwikkelen die kan worden geïntegreerd met de bestaande zakelijke infrastructuur van uw organisatie, zoals contentbeheer, facturering en toegangsbeheersystemen voor gebruikers. Met Flash Player en Adobe AIR kunt u toepassingen maken en eenvoudig implementeren waarmee consumenten toegang hebben tot grote bibliotheken met digitale inhoud en deze kunnen bekijken.

## Adobe Access SDK {#section_6AA3DC7BAE354472AE179BBC9AF6BD27}

De Toegang van de Adobe wordt geleverd als SDK van Java die de bouwstenen verstrekt waarvan u een serverimplementatie kunt tot stand brengen. Gebruikend SDK kunt u een oplossing van de Toegang van de Adobe tot stand brengen die aan het bedrijfsmodel van uw organisatie wordt aangepast.

De Java API&#39;s in de SDK worden in de volgende subsecties beschreven.

## Java API&#39;s voor het beheer van apparaatgroepdomeinen {#java-apis-for-managing-device-group-domains}

Deze APIs wordt gebruikt om de server toe te staan om cliëntverzoeken te behandelen om zich bij te sluiten en apparatengroepsdomeinen te verlaten.

Een apparaatgroepdomein is een logische verzameling apparaten die licenties tussen elkaar kunnen delen. Dit kan alleen gebeuren als elk apparaat zich eerst bij hetzelfde domein aansluit/zich registreert. De Adobe Access SDK, die op een server wordt uitgevoerd, moet de aanvragen voor Device Domain join (register) en aanvragen voor het verlaten van het apparaatdomein (deregister) verwerken. Apparaten die niet zijn verbonden met een domein, krijgen licenties toegewezen die zijn gebonden aan dat apparaat, dat niet kan worden gedeeld met een ander apparaat.

## Java API&#39;s voor inhoudsbeveiliging {#java-apis-for-protecting-content}

Deze API&#39;s worden gebruikt om rechten te definiëren en inhoud voor te bereiden voor verspreiding. De API&#39;s voor inhoudsbeveiliging zijn:

* Beleidsbeheer

  De API voor beleidsbeheer wordt gebruikt om beleid te maken en te wijzigen dat op inhoud moet worden toegepast. Het beleid kan worden tot stand gebracht of worden bijgewerkt, met inbegrip van het krijgen/plaatsen van alle gebruiksregels en het toestaan van extra parameters in een douanenamespace.

* Inhoud verpakken

  De API voor het verpakken van inhoud wordt gebruikt om inhoud te coderen en metagegevens van de inhoud in het pakket op te halen.

## Java API&#39;s voor het afgeven van licenties {#java-apis-for-issuing-licenses}

Deze API&#39;s worden gebruikt wanneer een client een licentie aanvraagt bij de server. De SDK ondersteunt de volgende verzoeken van de client:

* Verificatie

  De verificatie-API kan worden gebruikt om verificatieaanvragen af te handelen en verificatietokens te genereren.

* Vergunning genereren en verwerven

  De licentie-API voor genereren en aanschaffen wordt gebruikt om een licentie voor de gebruiker te genereren.

* Ondersteuning voor Adobe AIR versie 1.5-clients en -inhoud

  Met het oog op achterwaartse compatibiliteit heeft de SDK API&#39;s om aanvragen van AIR-toepassingen af te handelen die zijn gemaakt voor gebruik met AIR versie 1.5 en eerdere clients en beveiligde inhoud.

## Referentie-implementatie {#reference-implementation}

SDK omvat een verwijzingsimplementatie, een eenvoudige plaatsing van de Toegang van de Adobe die aantoont hoe te om Java APIs te gebruiken. De verwijzingsimplementatie verstrekt een Server van de Vergunning, de Gecontroleerde Packager van de Omslag, de toepassing van de Manager van de Toegang van de Adobe AIR, en bevellijnhulpmiddelen voor inhoudspakketten en beleidsbeheer die op Java APIs wordt gebaseerd. Meer over de de verwijzingsimplementatie van de Toegang van de Adobe leren, zie *Inhoud beveiligen*.

## Adobe Access Server voor beveiligde streaming {#adobe-access-server-for-protected-streaming}

Voor het stromen gebruik gevallen waar de inhoud met de Toegang van de Adobe, zoals voor Adobe HTTP Dynamic Streaming wordt beschermd, omvat de software ook Adobe Access Server voor Beschermde Streaming. Deze oplossing kan gemakkelijk op een servletcontainer zoals Tomcat worden opgesteld en kan een hoog niveau van scalability en prestaties bereiken om aan de grootste behoeften van de inhoudsdistributie te voldoen.

## Adobe Flash Player {#adobe-flash-player}

Flash Player is een lichtgewicht browserplug-in en runtime die een consistente en aantrekkelijke gebruikerservaring biedt, het afspelen van audio/video verbluffend en doordringend bereik biedt. Flash Player biedt een hoogwaardige weergave van gestreamde of gedownloade video-inhoud. Voor uitgevers van inhoud biedt Flash Player de mogelijkheid om de afspeelschermen rondom inhoud aan te passen, waardoor het mogelijk wordt om merken en monetisatie te verbeteren via advertenties met banners en overlays. Voor consumenten biedt Flash Player een intuïtieve en visueel aantrekkelijke manier om video-inhoud weer te geven.

Ga voor meer informatie over Flash Player naar: [www.adobe.com/go/flashplayer](https://www.adobe.com/go/flashplayer)

## Adobe AIR {#adobe-air}

Adobe AIR is een besturingssysteem overschrijdend runtime-programma waarmee inhoudsproducenten hun bestaande investeringen in het web kunnen uitbreiden naar het bureaublad door aangepaste multimediatoepassingen te ontwerpen. Het is gebaseerd op beproefde, open technologieën en biedt een betrouwbare, vereenvoudigde manier voor bedrijven om aangepaste toepassingen te ontwikkelen en te implementeren die vertrouwd kunnen worden om een veiligere, prettigere gebruikerservaring te bieden. Met Adobe AIR kunnen bedrijven op eenvoudige wijze rijke media integreren om een indrukwekkende en interactieve gebruikerservaring te creëren. Het laat ontwikkelaars vertrouwde hulpmiddelen zoals HTML, JavaScript, Flash, of de software van de Flex® gebruiken Adobe® om hun unieke combinatie rijke toepassingen van Internet aan of Vensters, Macintosh, of Linux op te stellen.

De ondernemingen hebben volledige controle van het gebruikersinterface, en zij kunnen een gebruikerservaring ontwerpen om hun merk te weerspiegelen en te versterken. Met ingebouwde ondersteuning voor het afspelen van inhoud die is beveiligd met Adobe Access SDK, helpt Adobe AIR aangepaste, end-to-end-contentdistributieketens te maken.

## Systeemeigen iOS- en Android-toepassingen {#native-ios-and-android-applications}

Native iOS- en Android-toepassingen die alleen beschikbaar zijn voor Adobe Primetime-klanten, kunnen via Adobe Access DRM 4.0 en hoger worden gebruikt om video te beschermen die wordt gebruikt binnen native (niet-Flash) toepassingen op mobiele apparaten. Een toepassing kan deze beveiligde inhoud alleen gebruiken als deze is geïmplementeerd met behulp van de Adobe Primetime Client-bibliotheken.

Ga voor meer informatie over Adobe Primetime naar: [https://www.adobe.com/solutions/primetime.html](https://www.adobe.com/solutions/primetime.html)
