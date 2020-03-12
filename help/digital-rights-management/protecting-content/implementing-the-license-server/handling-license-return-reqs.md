---
seo-title: Verzoeken om licentieverstrekking verwerken
title: Verzoeken om licentieverstrekking verwerken
uuid: 994df5af-476a-4ee8-b371-8900241be83d
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Verzoeken om licentieverstrekking verwerken{#handle-license-return-requests}

Als de clienttoepassing een licentie moet retourneren, wordt de `DRMManager.returnVoucher()` ActionScript API aangeroepen om het proces te starten. Deze API kan in een `immediateCommit` modus of een `confirmFirst` modus werken. Als deze `immediateCommit` is ingesteld op `true`, verwijdert de client de lokale licentie(s) onmiddellijk zonder te wachten op bevestiging van de licentieserver dat de aanvraag om de licentie(s) te retourneren is ontvangen. De Adobe Primetime DRM-licentieserver moet de aanvraag verwerken en een antwoord naar de client verzenden. Of de licentieserver het verzoek verwerkt, zoals het verlagen van het aantal licenties voor een opgegeven gebruiker, wordt bepaald door de licentieserver.

* De klasse request handler is `com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnHandler`
* De klasse request message is `com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnRequestMessage`

De minimaal vereiste `Adobe Primetime DRM` SDK-versie is versie 5. de aanvraag-URL is &quot; [!DNL /flashaccess/lreturn/v5]&quot;. Net als bij Domeinderegistratie gebruikt de server om te bepalen of de client een voorvertoning van een licentierendement kan weergeven. `getRequestPhase()`
