---
seo-title: Implementatieopties voor licentieservers
title: Implementatieopties voor licentieservers
uuid: 732b948f-8037-423e-9f85-770d6316cbae
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Implementatieopties voor licentieservers{#license-server-deployment-options}

U kunt de licentieserver implementeren door een van de volgende opties te gebruiken:

* Adobe Primetime DRM Server for Protected Streaming—Deze licentieserver is geoptimaliseerd voor streaming. U kunt bijvoorbeeld de server instellen voor dynamische streaming van Adobe HTTP met Primetime DRM. Deze server kan gemakkelijk met zeer weinig vereiste configuratie worden opgesteld en steunt veelvoudige huurders. Het kan een hoog niveau van scalability bereiken. Omdat deze implementatie is geoptimaliseerd voor streaming, worden de volledige Primetime DRM-functies niet ondersteund. Gebruikersnamen-/wachtwoordverificatie, domeinen en licentietekens worden bijvoorbeeld niet ondersteund. De gebruiksregels in licenties die door deze server worden uitgegeven, worden beheerd via een serverconfiguratiebestand, dat het beleid overschrijft dat tijdens het verpakken wordt gebruikt.

   Zie de *Adobe Primetime DRM Server voor de Beveiligde Streaming Guide* voor meer informatie over de gebruiksregels die worden ondersteund door de licentieserver.
* De Server van de Vergunning van de Implementatie van de verwijzing-u kunt deze opstelling gebruiken om uw serverimplementatie aan te passen. Dit is een voorbeeldimplementatie van de vergunningsserver, met inbegrip van broncode, die aantoont hoe te om APIs in Primetime DRM SDK te gebruiken om alle soorten verzoeken te beheren en hoe te om douanebedrijfslogica uit te voeren die door een gegevensbestand wordt gesteund. De gebruiksregels in licenties die door deze server worden uitgegeven, worden beheerd via het beleid dat aan de inhoud tijdens het verpakken is gekoppeld.
* Implementatie van aangepaste server—U kunt ook uw eigen licentieserver implementeren met de SDK. De informatie beschrijft hoe APIs wordt gebruikt om een vergunningsserver uit te voeren.

