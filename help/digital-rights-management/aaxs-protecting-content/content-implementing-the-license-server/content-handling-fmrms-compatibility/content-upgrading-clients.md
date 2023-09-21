---
title: Clients upgraden
description: Clients upgraden
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '75'
ht-degree: 0%

---

# Clients upgraden{#upgrading-clients}

Als een FMRMS 1.x- cliënt een server van de Toegang van de Adobe contacteert, moet de server de cliënt ertoe aanzetten om te bevorderen.

* De klasse request handler is `com.adobe.flashaccess.sdk.protocol.compatibility.FMRMSv1RequestHandler`.
* De aanvraag-URL is &quot;*Basis-URL van 1.x-inhoud*&quot; + &quot;/edcws/services/urn:EDCLicenseService&quot;

  In tegenstelling tot andere het verzoekmanagers van de Toegang van de Adobe, verleent deze manager geen toegang tot om het even welke verzoekinformatie of vereist om het even welke reactiegegevens om worden geplaatst. Maak een instantie van het dialoogvenster `FMRMSv1RequestHandler`en vervolgens bellen `close()`
