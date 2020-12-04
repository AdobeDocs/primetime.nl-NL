---
seo-title: Clients upgraden
title: Clients upgraden
uuid: 9c9bc7da-2a97-4659-945a-554d778d30a3
translation-type: tm+mt
source-git-commit: 5cf90a75d8805fb64d7d145722ad10a1ce77a14d
workflow-type: tm+mt
source-wordcount: '75'
ht-degree: 0%

---


# Clients upgraden{#upgrading-clients}

Als een FMRMS 1.x- cliënt een server van de Toegang van Adobe contacteert, moet de server de cliënt ertoe aanzetten om te bevorderen.

* De klasse van de verzoekmanager is `com.adobe.flashaccess.sdk.protocol.compatibility.FMRMSv1RequestHandler`.
* De aanvraag-URL is &quot;*Basis-URL van 1.x-inhoud*&quot; + &quot;/edcws/services/urn:EDCLicenseService&quot;

   In tegenstelling tot andere het verzoekmanagers van de Toegang van Adobe, verleent deze manager geen toegang tot om het even welke verzoekinformatie of vereist om het even welke reactiegegevens om worden geplaatst. Creeer een geval van `FMRMSv1RequestHandler`, en roep dan `close()`