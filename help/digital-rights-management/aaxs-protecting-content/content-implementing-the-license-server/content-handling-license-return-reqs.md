---
seo-title: Verzoeken om licentieverstrekking verwerken
title: Verzoeken om licentieverstrekking verwerken
uuid: d184faea-88cb-44f3-a253-e5314d577f17
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---


# Behandeling van aanvragen voor licentieteruggave{#handling-license-return-requests}

Als de clienttoepassing een licentie moet retourneren, roept deze de ActionScript-API van DRMManager.returnVoucher() aan om het proces te starten. Deze API kan op een directe wijze toewijzen, of een confirmFirst wijze werken. Als directCommit is ingesteld op true, verwijdert de client de lokale licentie(s) onmiddellijk, zonder te wachten op bevestiging van de licentieserver dat de aanvraag is ontvangen om de licentie(s) te retourneren. De Adobe Access-licentieserver moet het verzoek verwerken en een antwoord naar de client sturen. Of de licentieserver al dan niet iets met het verzoek doet (zoals het verlagen van het aantal licenties voor de opgegeven gebruiker) is aan de licentieserver om te beslissen.

* De klasse van de verzoekmanager is com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnHandler
* De aanvraagberichtklasse is com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnRequestMessage

De minimaal vereiste versie van Adobe Access SDK is versie 5. de aanvraag-URL is &quot; `/flashaccess/lreturn/v5`&quot;. Net als bij Domeinderegistratie moet de server `getRequestPhase()` gebruiken om te bepalen of de client een voorvertoning van een licentierendement weergeeft.
