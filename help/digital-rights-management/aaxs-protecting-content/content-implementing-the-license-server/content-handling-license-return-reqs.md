---
title: Verzoeken om licentieverstrekking verwerken
description: Verzoeken om licentieverstrekking verwerken
copied-description: true
exl-id: c8813f7a-9a12-4c71-a945-cee73b6784fd
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---

# Verzoeken om licentieverstrekking verwerken{#handling-license-return-requests}

Als de clienttoepassing een licentie moet retourneren, roept deze de ActionScript-API van DRMManager.returnVoucher() aan om het proces te starten. Deze API kan op een directe wijze toewijzen, of een confirmFirst wijze werken. Als directCommit is ingesteld op true, verwijdert de client de lokale licentie(s) onmiddellijk, zonder te wachten op bevestiging van de licentieserver dat de aanvraag is ontvangen om de licentie(s) te retourneren. De Adobe Access-licentieserver moet het verzoek verwerken en een antwoord naar de client sturen. Of de licentieserver al dan niet iets met het verzoek doet (zoals het verlagen van het aantal licenties voor de opgegeven gebruiker) is aan de licentieserver om te beslissen.

* De klasse van de verzoekmanager is com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnHandler
* De aanvraagberichtklasse is com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnRequestMessage

De minimaal vereiste versie van Adobe Access SDK is versie 5. de aanvraag-URL is &quot; `/flashaccess/lreturn/v5`&quot;. Net als bij Domeinderegistratie moet de server `getRequestPhase()` om te bepalen of de client een voorvertoning van een licentieresultaat weergeeft.
