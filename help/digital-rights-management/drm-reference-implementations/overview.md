---
title: Informatie over de referentie-implementaties
description: Informatie over de referentie-implementaties
copied-description: true
exl-id: fe387330-9449-4977-be15-069c814354bf
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 0%

---

# Informatie over de referentie-implementaties{#about-the-reference-implementations}

In deze handleiding worden de installatie, configuratie en werking van de Adobe Primetime DRM-referentieimplementaties beschreven.

>[!NOTE]
>
>Primetime DRM werd eerder Adobe Access genoemd, en daarvoor, Flash Access.

De Primetime DRM verwijzingsimplementaties omvatten deze componenten:

* **Opdrachtregelprogramma&#39;s** - Deze gereedschappen zijn gebaseerd op dezelfde Primetime DRM SDK-code die wordt gebruikt in de Primetime DRM-licentieserver. U kunt verpakken, licenties en andere DRM-taken uitvoeren vanaf de opdrachtregel en naadloos schakelen tussen het gebruik van de opdrachtregelprogramma&#39;s en de licentieserver.
* **Licentieserver** - Een volledig functionele, aanpasbare licentieserver (hieronder beschreven als een van uw opties voor licentieservers).

**Licentieserveropties:**

* **De Primetime DRM-verwijzingsimplementaties** - Het onderwerp van deze handleiding, deze verwijzingsimplementatie kenmerkt een robuuste DRM vergunningsserver die alle eigenschappen toont die door Primetime DRM SDK worden verstrekt. Deze implementatie wordt geleverd met broncode en instructies voor het samenstellen van de code. Deze implementatie is niet bedoeld als zodanig (hoewel [!DNL .war] Het bestand is opgenomen en u kunt het snel implementeren.) Het is hoofdzakelijk bedoeld als verwijzing u kunt gebruiken om uw eigen server van de douanevergunning te bouwen.

   Functies van licentieserver:

   * Beheert verificatieaanvragen met behulp van een database voor het valideren van gebruikersnaam en wachtwoord.
   * Beheert vergunningsverzoeken en bepaalt het type vergunning dat wordt uitgegeven wanneer de vergunning het ketenen wordt toegepast.
   * Geeft licenties voor inhoud die meerdere Primetime DRM-beleidsregels bevat.
   * Geeft licenties die levering via Remote Key aan iOS-clients ondersteunen. Hiervoor is Primetime DRM vereist.
   * Kwesties vergunningen die een externe raadpleging en herwinning van de Sleutel van de Encryptie van de Inhoud (CEK) vereisen.
   * Zoekt een gegevensbestand om te bepalen als een gebruiker wordt gemachtigd om inhoud te bekijken.
   * Zoekt in Primetime DRM-beleidsupdate de lijsten.
   * Hiermee zoekt u lijsten met intrekkingen van machines.
   * Gebruikt een HSM- of PKCS12-bestand om referenties op te slaan.
   * Codeert wachtwoorden die u in een eigenschappenbestand hebt opgegeven.
   * Geeft meerdere licentieserver- of transportreferenties op nadat de referenties zijn vernieuwd.

      De oude gegevens blijven behouden op de server, zodat gebruikers bestaande inhoud kunnen blijven bekijken zonder opnieuw te moeten verpakken.
   * Beperkt DRM/Runtime versies die verzoeken aan een vergunningsserver mogen indienen.
   * Hiermee stelt u voorkeuren voor het terugdraaien van de clientklok in.
   * Beperkt het tijdverschil dat tussen de verzoektijd en de servertijd wordt toegestaan om replay aanvallen te verhinderen.
   * Beheert aanvragen van FMRMS 1.x-clients

      Bijvoorbeeld, wordt de cliënt FMRMS 1.x teweeggebracht om aan Primetime DRM 2.0 of later te bevorderen.
   * FMRMS 1.x-metagegevens worden op verzoek omgezet naar DRM-metagegevens in primetime door FMRMS 1.x-licentiegegevens te gebruiken die in een database zijn opgeslagen.
   * Converteert FMRMS 1.x-beleid naar primetime DRM-beleid voor voorbeeldcode.
   * Hiermee importeert u FMRMS 1.x-licentiegegevens uit een bestaande database voor voorbeeldscripts.
   * Hiermee wordt de serverversie opgehaald
   * Domeinregistratie
   * Domein deregistration
   * Synchronisatieverzoeken
   * Licentie terugsturen

* **De Primetime DRM-server voor beveiligde streaming** - Dit is een kant-en-klare binaire oplossing die u snel en met minimale moeite kunt implementeren. Het is een goede optie voor klanten die het Bewijs van Concept snel willen tonen, of het *kon* zijn een productieoptie als uw aangepaste DRM-behoeften minimaal zijn. Zie Verwante informatie hieronder voor meer informatie.

* **De Primetime Cloud DRM-service** - Dit is een op Adobe gehoste licentieserver die u kunt gebruiken voor het bedienen van licenties. (U moet een Primetime-licentienemer zijn om deze service te kunnen gebruiken.) Met deze Adobe-cloudservice verliest u de kosten, het onderhoud en de engineering die nodig zijn om uw eigen service te maken. Zie Verwante informatie hieronder voor meer informatie.
