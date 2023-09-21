---
title: Verzoeken om licentieverstrekking verwerken
description: Verzoeken om licentieverstrekking verwerken
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# Verzoeken om licentieverstrekking verwerken{#handle-license-return-requests}

Als de clienttoepassing een licentie moet retourneren, wordt het `DRMManager.returnVoucher()` ActionScript API om het proces te starten. Deze API kan werken in een `immediateCommit` of een `confirmFirst` -modus. Indien `immediateCommit` is ingesteld op `true`, verwijdert de klant de lokale licentie(s) onmiddellijk zonder te wachten op bevestiging van de licentieserver dat hij het verzoek om de licentie(s) te retourneren heeft ontvangen. De Adobe Primetime DRM-licentieserver moet de aanvraag verwerken en een antwoord naar de client verzenden. Of de licentieserver het verzoek verwerkt, zoals het verlagen van het aantal licenties voor een opgegeven gebruiker, wordt bepaald door de licentieserver.

* De klasse request handler is `com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnHandler`
* De klasse request message is `com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnRequestMessage`

Het minimum `Adobe Primetime DRM` De SDK-versie is vereist op versie 5. De aanvraag-URL is &quot; [!DNL /flashaccess/lreturn/v5]&quot;. Net als bij Domeinderegistratie gebruikt de server `getRequestPhase()` om te bepalen of de client een voorvertoning van een licentieresultaat kan weergeven.
