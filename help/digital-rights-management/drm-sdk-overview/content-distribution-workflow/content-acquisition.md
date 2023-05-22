---
description: Wanneer een consument een beveiligd inhoudsbestand van een website of CDN verkrijgt, moet de consument ook een licentie verkrijgen die een sleutel bevat om de video te decoderen voordat deze kan worden afgespeeld. De volgende stappen illustreren een algemene workflow voor hoe beveiligde inhoud wordt benaderd door een computer waarop Flash Player of Adobe AIR wordt uitgevoerd
title: Inhoudsverwerving
exl-id: 92d51928-6021-4284-9310-4e6ce758bffc
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '695'
ht-degree: 0%

---

# Inhoudsverwerving{#content-acquisition}

Wanneer een consument een beveiligd inhoudsbestand van een website of CDN verkrijgt, moet de consument ook een licentie verkrijgen die een sleutel bevat om de video te decoderen voordat deze kan worden afgespeeld. De volgende stappen illustreren een algemene workflow voor hoe beveiligde inhoud wordt benaderd door een computer waarop Flash Player of Adobe AIR wordt uitgevoerd:

1. De consument bezoekt de website van de detailhandelaar, en selecteert een video om te letten op. De consument probeert de beveiligde video te downloaden of te streamen naar zijn of haar computer met behulp van Flash Player of een Adobe AIR-toepassing.

   Als dit de eerste keer is dat de consument probeert toegang te krijgen tot beveiligde inhoud met deze specifieke computer, moet de Flash Player- of Adobe AIR-runtime eerst worden geïndividualiseerd zoals beschreven in Stap 2. Als de runtime-client al is geïndividualiseerd, vindt het aanschaffen van een licentie plaats zoals beschreven in Stap 3.

1. De Flash Player- of Adobe AIR-runtime-client verkrijgt een uniek digitaal certificaat (ook wel een *machinecertificaat*) van een op Adobe gehoste server.

   Dit proces waarbij een uniek certificaat wordt toegewezen, wordt *individualisering*. Individualisatie identificeert op unieke wijze zowel de computer als de Flash Player- of Adobe AIR-runtime die wordt gebruikt voor het afspelen van inhoud.

   Met het individualisatieproces kunnen de gedownloade licenties worden gebonden aan een specifieke computer waarop de client is geïnstalleerd. Elke computer krijgt een unieke computerreferentie (persoonlijke sleutel en machinecertificaat). Als een bepaalde client gecompromitteerd raakt, kan deze worden ingetrokken en kan het hem worden verboden licenties voor nieuwe inhoud aan te schaffen.

1. De client parseert de beveiligde inhoud wanneer deze begint met downloaden of streamen naar de computer van de consument en haalt de URL van de licentieserver van de detailhandelaar uit de DRM-metagegevens van Primetime die in het bestand zijn ingesloten.

   De DRM-metagegevens van Primetime zijn doorgaans gescheiden van de inhoud, zoals ingesloten in een bijbehorend manifestbestand of als een binair blok, maar kunnen ook worden ingesloten in het inhoudsbestand. De client neemt contact op met de licentieserver op de opgegeven URL en verkrijgt een licentie (zoals hieronder in stap 4 wordt beschreven).
1. De client verkrijgt een licentie van de licentieserver van de detailhandelaar.

   Tijdens het aanschaffen van de licentie verstuurt de client gegevens ter identificatie van de gevraagde inhoud (de *Primetime DRM-metagegevens*) en het machinecertificaat (ter identificatie van de computer van de consument) voor de licentieserver van de detailhandelaar. Het licentieverzoek dat naar de server wordt verzonden, wordt versleuteld met de openbare sleutel Transport, die ook in de DRM-metagegevens van Primetime is opgenomen.

   De server van de Vergunning — die in de het factureren en authentificatieinfrastructuur van de detailhandelaar kan worden geïntegreerd — kan een bedrijfsregelcontrole uitvoeren om te verifiëren dat de gebruiker wordt gemachtigd om de gevraagde inhoud te bekijken. Als de bedrijfsregels dit toestaan, geeft de Server van de Vergunning een vergunning uit die de sleutel van de inhoudsencryptie bevat om de inhoud en de gebruiksregels verbonden aan de rekening van die gebruiker te decrypteren. Om een vergunningsverzoek te verwerken, decrypteert de Server van de Vergunning het verzoek gebruikend zijn privé sleutel van het Vervoer. De CEK in de meta-gegevens wordt gedecrypteerd gebruikend de privé sleutel van de Server van de Vergunning, en opnieuw gecodeerd om de vergunning te binden aan het apparaat dat het verzoek indient. De licentie wordt ondertekend met de persoonlijke sleutel van de licentieserver. De licentiereactie wordt ondertekend met de persoonlijke sleutel Transport en gecodeerd voordat deze wordt geretourneerd aan de client.

   Indien toegestaan door de licentie slaat de client de licentie op om *offline toegang* op de vergunning. Door een licentie in cache te plaatsen, kan de consument de beveiligde inhoud bekijken zonder telkens opnieuw een licentie aan te schaffen als hij of zij de inhoud wil bekijken.

1. Zodra de Flash Player- of Adobe AIR-runtime-client over een licentie beschikt, haalt de client de CEK uit de licentie en kan de consument de inhoud bekijken waartoe hij of zij gemachtigd is.

   <!--<a id="fig_s43_gc2_44"></a>-->

   ![](assets/FMRMS_fig01_web.png)

   In het vorige voorbeeld wordt slechts één mogelijke workflow getoond. U kunt ook een workflow gebruiken met een proactieve download van inhoud, waarbij de licentieverwerving veel later plaatsvindt. Een andere optie is het implementeren van een vooraf ingestelde workflow waarbij de licentieverkoop plaatsvindt voordat de inhoud wordt benaderd.
