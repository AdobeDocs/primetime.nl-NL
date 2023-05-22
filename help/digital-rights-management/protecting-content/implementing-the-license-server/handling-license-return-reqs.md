---
title: Verzoeken om licentieverstrekking verwerken
description: Verzoeken om licentieverstrekking verwerken
copied-description: true
exl-id: de577cb9-4ede-440e-8b71-1b39c6cc3c5b
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# Verzoeken om licentieverstrekking verwerken{#handle-license-return-requests}

Als de clienttoepassing een licentie moet retourneren, wordt het `DRMManager.returnVoucher()` ActionScript API om het proces te starten. Deze API kan werken in een `immediateCommit` of een `confirmFirst` in. Indien `immediateCommit` is ingesteld op `true`, verwijdert de klant de lokale licentie(s) onmiddellijk zonder te wachten op bevestiging van de licentieserver dat hij het verzoek om de licentie(s) te retourneren heeft ontvangen. De Adobe Primetime DRM-licentieserver moet de aanvraag verwerken en een antwoord naar de client verzenden. Of de licentieserver het verzoek verwerkt, zoals het verlagen van het aantal licenties voor een opgegeven gebruiker, wordt bepaald door de licentieserver.

* De klasse request handler is `com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnHandler`
* De klasse request message is `com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnRequestMessage`

Het minimum `Adobe Primetime DRM` De vereiste SDK-versie is versie 5; de aanvraag-URL is &quot; [!DNL /flashaccess/lreturn/v5]&quot;. Net als bij Domeinderegistratie gebruikt de server `getRequestPhase()` om te bepalen of de client een voorvertoning van een licentieresultaat kan weergeven.
