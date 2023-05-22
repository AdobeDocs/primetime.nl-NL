---
title: Clients upgraden
description: Clients upgraden
copied-description: true
exl-id: 0476c9ef-3622-4bc5-bb24-f8543470b7d3
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '75'
ht-degree: 0%

---

# Clients upgraden{#upgrading-clients}

Als een FMRMS 1.x- cliënt een server van de Toegang van Adobe contacteert, moet de server de cliënt ertoe aanzetten om te bevorderen.

* De klasse request handler is `com.adobe.flashaccess.sdk.protocol.compatibility.FMRMSv1RequestHandler`.
* De aanvraag-URL is &quot;*Basis-URL van 1.x-inhoud*&quot; + &quot;/edcws/services/urn:EDCLicenseService&quot;

   In tegenstelling tot andere het verzoekmanagers van de Toegang van Adobe, verleent deze manager geen toegang tot om het even welke verzoekinformatie of vereist om het even welke reactiegegevens om worden geplaatst. Maak een instantie van het dialoogvenster `FMRMSv1RequestHandler`en vervolgens `close()`
