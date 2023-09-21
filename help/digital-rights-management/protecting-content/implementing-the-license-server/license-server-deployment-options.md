---
title: Implementatieopties voor licentieservers
description: Implementatieopties voor licentieservers
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Implementatieopties voor licentieservers{#license-server-deployment-options}

U kunt de licentieserver implementeren door een van de volgende opties te gebruiken:

* Adobe Primetime DRM Server for Protected Streaming—Deze licentieserver is geoptimaliseerd voor streaming. U kunt bijvoorbeeld de server instellen voor Adobe HTTP Dynamic Streaming met Primetime DRM. Deze server kan gemakkelijk met zeer weinig vereiste configuratie worden opgesteld en steunt veelvoudige huurders. Het kan een hoog niveau van scalability bereiken. Omdat deze implementatie is geoptimaliseerd voor streaming, worden de volledige Primetime DRM-functies niet ondersteund. Gebruikersnamen-/wachtwoordverificatie, domeinen en licentietekens worden bijvoorbeeld niet ondersteund. De gebruiksregels in licenties die door deze server worden uitgegeven, worden beheerd via een serverconfiguratiebestand, dat het beleid overschrijft dat tijdens het verpakken wordt gebruikt.

  Zie de *Adobe Primetime DRM Server for Protected Streaming Guide* voor meer informatie over de gebruiksregels die door de server van de Vergunning worden gesteund.
* De Server van de Vergunning van de Implementatie van de verwijzing-u kunt deze opstelling gebruiken om uw serverimplementatie aan te passen. Dit is een voorbeeldimplementatie van de vergunningsserver, met inbegrip van broncode, die aantoont hoe te om APIs in Primetime DRM SDK te gebruiken om alle soorten verzoeken te beheren en hoe te om douanebedrijfslogica uit te voeren die door een gegevensbestand wordt gesteund. De gebruiksregels in licenties die door deze server worden uitgegeven, worden beheerd via het beleid dat aan de inhoud tijdens het verpakken is gekoppeld.
* Implementatie van aangepaste server—U kunt ook uw eigen licentieserver implementeren met de SDK. De informatie beschrijft hoe APIs wordt gebruikt om een vergunningsserver uit te voeren.
