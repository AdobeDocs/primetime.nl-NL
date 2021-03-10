---
description: De belangrijkste componenten van Adobe Access bestaan uit een Java SDK en de Flash Player en Adobe AIR-clientruntimeomgevingen.
title: Java SDK, Flash Player en Adobe AIR-client
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '924'
ht-degree: 0%

---


# Adobe Access-componenten{#adobe-access-components}

De belangrijkste componenten van Adobe Access bestaan uit een Java SDK en de Flash Player en Adobe AIR-clientruntimeomgevingen.

Zie De SDK instellen in *De SDK van Adobe Access gebruiken voor het beschermen van inhoud voor meer informatie over het instellen van de SDK.*

Met de Adobe Access SDK kunt u een oplossing voor digitaal rechtenbeheer ontwikkelen die kan worden geïntegreerd met de bestaande zakelijke infrastructuur van uw organisatie, zoals contentbeheer, facturering en toegangsbeheersystemen voor gebruikers. Met Flash Player en Adobe AIR kunt u toepassingen maken en eenvoudig implementeren waarmee consumenten toegang hebben tot grote bibliotheken met digitale inhoud en deze kunnen bekijken.

## Adobe Access SDK {#section_6AA3DC7BAE354472AE179BBC9AF6BD27}

Adobe Access wordt geleverd als een Java SDK die de bouwstenen biedt waarmee u een serverimplementatie kunt maken. Gebruikend SDK kunt u een oplossing tot stand brengen van de Toegang van Adobe die aan het bedrijfsmodel van uw organisatie wordt aangepast.

De Java API&#39;s in de SDK worden in de volgende subsecties beschreven.

## Java API&#39;s voor het beheer van apparaatgroepdomeinen {#java-apis-for-managing-device-group-domains}

Deze APIs wordt gebruikt om de server toe te staan om cliëntverzoeken te behandelen om zich bij te sluiten van en het verlaten van de domeinen van de apparatengroep.

Een apparaatgroepdomein is een logische verzameling apparaten die licenties tussen elkaar kunnen delen. Dit kan alleen gebeuren als elk apparaat zich eerst bij hetzelfde domein aansluit/zich registreert. De Adobe Access SDK, die op een server wordt uitgevoerd, moet de aanvragen voor Device Domain join (register) en aanvragen voor het verlaten van het apparaatdomein (deregister) afhandelen. Apparaten die niet zijn verbonden met een domein, krijgen licenties toegewezen die zijn gebonden aan dat apparaat, dat niet kan worden gedeeld met een ander apparaat.

## Java API&#39;s voor het beveiligen van inhoud {#java-apis-for-protecting-content}

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

   Met het oog op achterwaartse compatibiliteit heeft de SDK API&#39;s voor het afhandelen van aanvragen van AIR-toepassingen die zijn gemaakt voor gebruik met AIR versie 1.5 en eerdere clients en beveiligde inhoud.

## Referentie-implementatie {#reference-implementation}

De SDK bevat een voorbeeldimplementatie, een eenvoudige Adobe Access-implementatie die aantoont hoe u de Java API&#39;s kunt gebruiken. De verwijzingsimplementatie verstrekt een Server van de Vergunning, de Controlemapverpakker, de toepassing van de Manager van de Toegang van de Adobe, AIR, en bevellijnhulpmiddelen voor inhoudspakketten en beleidsbeheer dat op Java APIs wordt gebaseerd. Meer over de de verwijzingsimplementatie van de Toegang van de Adobe leren, zie *Beschermend Inhoud*.

## Adobe Access Server for Protected Streaming {#adobe-access-server-for-protected-streaming}

Voor het stromen gebruik gevallen waar de inhoud met Adobe Access, zoals voor Adobe HTTP Dynamic Streaming wordt beschermd, omvat de software ook Adobe Access Server voor Beschermde Streaming. Deze oplossing kan gemakkelijk op een servletcontainer zoals Tomcat worden opgesteld en kan een hoog niveau van scalability en prestaties bereiken om aan de grootste behoeften van de inhoudsdistributie te voldoen.

## Adobe Flash Player {#adobe-flash-player}

Flash Player is een lichtgewicht browserplug-in en runtime die een consistente en aantrekkelijke gebruikerservaring biedt, het afspelen van audio/video verbluffend en doordringend bereik biedt. Flash Player biedt een hoogwaardige weergave van gestreamde of gedownloade video-inhoud. Voor uitgevers van inhoud biedt Flash Player de mogelijkheid om de afspeelschermen rondom inhoud aan te passen, waardoor het mogelijk wordt om merken en monetisatie te verbeteren via advertenties met banners en overlays. Voor consumenten biedt Flash Player een intuïtieve en visueel aantrekkelijke manier om video-inhoud weer te geven.

Ga voor meer informatie over Flash Player naar: [www.adobe.com/go/flashplayer](https://www.adobe.com/go/flashplayer)

## Adobe AIR {#adobe-air}

Adobe AIR is een besturingssysteem overschrijdend runtime-programma waarmee inhoudsproducenten hun bestaande investeringen in het web kunnen uitbreiden naar het bureaublad door aangepaste multimediatoepassingen te ontwerpen. Het is gebaseerd op beproefde, open technologieën en biedt een betrouwbare, vereenvoudigde manier voor bedrijven om aangepaste toepassingen te ontwikkelen en te implementeren die vertrouwd kunnen worden voor een veiligere, prettigere gebruikerservaring. Met Adobe AIR kunnen bedrijven op eenvoudige wijze rijke media integreren om een indrukwekkende en interactieve gebruikerservaring te creëren. Ontwikkelaars kunnen vertrouwde hulpprogramma&#39;s zoals HTML, JavaScript, Flash of Adobe® Flex® gebruiken om hun unieke combinatie van geavanceerde internettoepassingen te implementeren in Windows, Macintosh of Linux.

De ondernemingen hebben volledige controle van het gebruikersinterface, en zij kunnen een gebruikerservaring ontwerpen om hun merk te weerspiegelen en te versterken. Met ingebouwde ondersteuning voor het afspelen van inhoud die is beveiligd met Adobe Access SDK, helpt Adobe AIR om aangepaste, end-to-end contentdistributieketens te maken.

Ga voor meer informatie over Adobe AIR naar: [www.adobe.com/go/air](https://www.adobe.com/go/air)

## Systeemeigen iOS- en Android-toepassingen {#native-ios-and-android-applications}

Native iOS- en Android-toepassingen die alleen beschikbaar zijn voor Adobe Primetime-klanten, kunnen Adobe Access DRM 4.0 en hoger worden gebruikt om video te beschermen die wordt gebruikt binnen native (niet-Flash) toepassingen op mobiele apparaten. Een toepassing kan deze beveiligde inhoud alleen gebruiken als deze is geïmplementeerd met behulp van de Adobe Primetime Client-bibliotheken.

Ga voor meer informatie over Adobe Primetime naar: [https://www.adobe.com/solutions/primetime.html](https://www.adobe.com/solutions/primetime.html)