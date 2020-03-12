---
seo-title: Implementatieopties voor licentieservers
title: Implementatieopties voor licentieservers
uuid: 297c587f-23e2-4bb5-911b-72d7b82370f4
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Implementatieopties voor licentieservers{#license-server-deployment-options}

U kunt de licentieserver op een van de volgende manieren implementeren:

* **Adobe Access Server for Protected Streaming** — Deze licentieserver is geoptimaliseerd voor streaming. U kunt bijvoorbeeld de server instellen voor dynamische streaming van Adobe HTTP met Adobe Access. Deze server kan gemakkelijk met zeer weinig vereiste configuratie worden opgesteld en zal veelvoudige huurders steunen, en kan een hoog niveau van scalability bereiken. Aangezien deze implementatie echter is geoptimaliseerd voor streaming, worden niet alle Adobe Access-functies ondersteund. Gebruikersnamen-/wachtwoordverificatie, domeinen en licentietekens worden bijvoorbeeld niet ondersteund. De gebruiksregels in licenties die door deze server worden uitgegeven, worden beheerd via een serverconfiguratiebestand, dat het beleid overschrijft dat tijdens het verpakken wordt gebruikt. Zie de *Adobe Access-server voor de beveiligde streaminghandleiding* voor meer informatie over de gebruiksregels die door deze server worden ondersteund.
* **Referentie-implementatieserver** — Gebruik deze instelling als beginpunt voor een aangepaste serverimplementatie. Dit is een voorbeeld van de implementatie van de licentieserver, met inbegrip van broncode, die aantoont hoe te om APIs in de SDK van de Toegang van Adobe te gebruiken om alle types van verzoeken te behandelen en hoe te om douanebedrijfslogica uit te voeren die door een gegevensbestand wordt gesteund. De gebruiksregels in licenties die door deze server worden uitgegeven, worden beheerd via het beleid dat aan de inhoud tijdens het verpakken is gekoppeld.
* **Aangepaste serverimplementatie** — U kunt ook uw eigen licentieserver implementeren met de SDK. De informatie in dit hoofdstuk beschrijft APIs die worden gebruikt om een vergunningsserver uit te voeren.

