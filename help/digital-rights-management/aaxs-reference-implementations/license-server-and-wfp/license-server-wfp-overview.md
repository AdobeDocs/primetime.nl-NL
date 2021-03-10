---
title: Overzicht van licentieserver en gecontroleerde mappakketten
description: Overzicht van licentieserver en gecontroleerde mappakketten
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---


# Overzicht van licentieserver en gecontroleerde mapverpakker {#license-server-and-watched-folder-packager-overview}

De server van de verwijzings implementatie kan u helpen een vergunningsserver tot stand brengen gebruikend de Adobe Toegang SDK. In deze implementatie worden gebruikers geverifieerd op basis van gebruikersinvoer in een database. De server bevat demonstratie-bedrijfslogica voor het afgeven van licenties. Het voert ook verenigbaarheidssteun voor de Server 1.0 en 1.5 van het Rights Management van de Media van Flash uit.

De referentie-implementatieserver bevat ook een gecontroleerde mapimplementatie van de pakketsoftware. Deze component kan samen met de licentieserver of op een aparte computer worden geïmplementeerd. Met deze pakketimplementatie kunnen meerdere gecontroleerde mappen worden gemaakt. Wanneer inhoud in de gecontroleerde omslag wordt gelaten vallen, verpakt de pakketmanager automatisch de inhoud.

De licentieserver en de packager worden geïmplementeerd als afzonderlijke WAR-bestanden, zodat u kunt kiezen of u deze wilt uitvoeren op afzonderlijke servers of in één Apache Tomcat®-instantie. De licentieserver bevindt zich in de [!DNL flashaccess.war] en de pakketsoftware bevindt zich in [!DNL flashaccess-packager.war]. De optionele [!DNL edcws.war] bevat ondersteuning voor licentieaanvragen van FMRMS 1.x-clients.

De voorbeeldcode van de Reference Implementation demonstreert de volgende functies:

* Licentieserver:

   * Behandeling van verificatieaanvragen, met behulp van een database voor validatie van gebruikersnaam/wachtwoord
   * Vergunningsaanvragen afhandelen en bepalen welk type vergunning moet worden afgegeven wanneer een licentietak wordt gebruikt.
   * Licenties afgeven voor inhoud die meerdere beleidsregels bevat
   * Licenties verlenen die levering via Remote Key aan iOS-clients ondersteunen (Adobe Primetime vereist)
   * Vergunningen verlenen die een externe raadpleging/herwinning van de Sleutel van de Encryptie van de Inhoud (CEK) vereisen
   * Gebruikend gegevensbestand om te bepalen of de gebruiker wordt gemachtigd om inhoud te bekijken
   * Lijsten met beleidsupdates gebruiken
   * Intrekkingslijsten voor computers gebruiken
   * Een HSM- of PKCS12-bestand gebruiken om referenties op te slaan
   * Wachtwoorden coderen die zijn opgegeven in eigenschappenbestand
   * Het specificeren van veelvoudige vergunningsserver of vervoergeloofsbrieven (nadat de geloofsbrieven worden vernieuwd, worden de oude geloofsbrieven gehouden op de server zodat de bestaande inhoud kan worden verbruikt zonder het moeten opnieuw verpakken)
   * Het beperken van DRM/Runtime versies toegestaan om verzoeken aan de vergunningsserver te doen
   * Voorkeuren voor het terugdraaien van de client instellen
   * Het beperken van tijdsverschil toegestaan tussen verzoektijd en servertijd (om replay aanvallen te verhinderen)
   * Behandeling van aanvragen van FMRMS 1.x-clients (activeert FMRMS 1.x-client voor upgrade naar Adobe Access 2.0 of hoger)
   * FMRMS 1.x-metagegevens worden geconverteerd naar Adobe Access-metagegevens die direct beschikbaar zijn, met FMRMS 1.x-licentiegegevens die zijn opgeslagen in een database
   * Voorbeeldcode voor het converteren van FMRMS 1.x-beleid naar Adobe Access-beleid
   * Voorbeeldscripts voor het importeren van FMRMS 1.x-licentiegegevens uit een bestaande database
   * Serverversie ophalen
   * Domeinregistratie
   * Domein deregistration
   * Synchronisatieverzoeken
   * Licentie terugsturen

* Packager Server:

   * Implementeren van een pakketimplementatie die automatisch inhoud verpakt die aan een gecontroleerde map is toegevoegd
   * Een HSM- of PKCS12-bestand gebruiken om referenties op te slaan
   * Wachtwoorden coderen die zijn opgegeven in eigenschappenbestand
   * Packager configureren, beleid maken en lijsten met beleidsupdates maken met een AIR-toepassing

