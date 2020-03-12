---
seo-title: Clients upgraden
title: Clients upgraden
uuid: 9c9bc7da-2a97-4659-945a-554d778d30a3
translation-type: tm+mt
source-git-commit: 5cf90a75d8805fb64d7d145722ad10a1ce77a14d

---


# Clients upgraden{#upgrading-clients}

Als een FMRMS 1.x-client contact opneemt met een Adobe Access-server, moet de server de client vragen een upgrade uit te voeren.

* De klasse van de verzoekmanager is `com.adobe.flashaccess.sdk.protocol.compatibility.FMRMSv1RequestHandler`.
* De aanvraag-URL is &quot;*Basis-URL van 1.x-inhoud*&quot; + &quot;/edcws/services/urn:EDCLicenseService&quot;

   In tegenstelling tot andere Adobe Access-aanvraaghandlers biedt deze handler geen toegang tot informatie over een verzoek of moet er geen reactiegegevens worden ingesteld. Creeer een geval van `FMRMSv1RequestHandler`, en roep dan `close()`