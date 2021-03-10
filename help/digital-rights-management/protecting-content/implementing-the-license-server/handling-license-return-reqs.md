---
title: Verzoeken om licentieverstrekking verwerken
description: Verzoeken om licentieverstrekking verwerken
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---


# Terugzendverzoeken voor handmatige licentie{#handle-license-return-requests}

Als de clienttoepassing een licentie moet retourneren, wordt de ActionScript-API `DRMManager.returnVoucher()` aangeroepen om het proces te starten. Deze API kan op een `immediateCommit` wijze of een `confirmFirst` wijze werken. Als `immediateCommit` is ingesteld op `true`, verwijdert de client de lokale licentie(s) onmiddellijk zonder te wachten op bevestiging van de licentieserver dat de aanvraag is ontvangen om de licentie(s) te retourneren. De Adobe Primetime DRM-licentieserver moet de aanvraag verwerken en een antwoord naar de client verzenden. Of de licentieserver het verzoek verwerkt, zoals het verlagen van het aantal licenties voor een opgegeven gebruiker, wordt bepaald door de licentieserver.

* De klasse van de verzoekmanager is `com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnHandler`
* De klasse van het verzoekbericht is `com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnRequestMessage`

De minimaal `Adobe Primetime DRM` vereiste SDK-versie is versie 5; de aanvraag-URL is &quot; [!DNL /flashaccess/lreturn/v5]&quot;. Net als bij Domeinderegistratie gebruikt de server `getRequestPhase()` om te bepalen of de client een voorvertoning van een geretourneerde licentie kan weergeven.
