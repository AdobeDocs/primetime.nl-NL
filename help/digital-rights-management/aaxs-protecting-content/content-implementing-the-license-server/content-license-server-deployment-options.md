---
title: Implementatieopties voor licentieservers
description: Implementatieopties voor licentieservers
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---


# Implementatieopties voor licentieservers{#license-server-deployment-options}

U kunt de licentieserver op een van de volgende manieren implementeren:

* **Adobe Access Server for Protected Streaming**  - Deze licentieserver is geoptimaliseerd voor streaming. U kunt bijvoorbeeld de server instellen voor Adobe HTTP Dynamic Streaming met Adobe Access. Deze server kan gemakkelijk met zeer weinig vereiste configuratie worden opgesteld en zal veelvoudige huurders steunen, en kan een hoog niveau van scalability bereiken. Aangezien deze implementatie is geoptimaliseerd voor streaming, biedt deze echter geen ondersteuning voor de volledige Adobe Access-functies. Gebruikersnamen-/wachtwoordverificatie, domeinen en licentietekens worden bijvoorbeeld niet ondersteund. De gebruiksregels in licenties die door deze server worden uitgegeven, worden beheerd via een serverconfiguratiebestand, dat het beleid overschrijft dat tijdens het verpakken wordt gebruikt. Zie *Adobe Access Server for Protected Streaming Guide* voor meer informatie over de gebruiksregels die door deze server worden ondersteund.
* **Referentie-implementatieserver** : gebruik deze instelling als beginpunt voor een aangepaste serverimplementatie. Dit is een implementatie van de voorbeeldvergunningsserver, met inbegrip van broncode, die aantoont hoe te om APIs in de Toegang SDK van de Adobe te gebruiken om alle soorten verzoeken te behandelen en hoe te om douanebedrijfslogica uit te voeren die door een gegevensbestand wordt gesteund. De gebruiksregels in licenties die door deze server worden uitgegeven, worden beheerd via het beleid dat aan de inhoud tijdens het verpakken is gekoppeld.
* **Aangepaste serverimplementatie** : u kunt ook uw eigen licentieserver implementeren met de SDK. De informatie in dit hoofdstuk beschrijft APIs die worden gebruikt om een vergunningsserver uit te voeren.

