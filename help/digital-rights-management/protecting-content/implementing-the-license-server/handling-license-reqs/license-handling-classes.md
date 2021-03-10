---
title: Overzicht
description: Overzicht
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---


# Overzicht {#overview}

Om een licentie te verkrijgen, vormen clients een verzoek uit de metagegevens die zijn ingesloten in inhoud in het pakket, en verzenden ze dat verzoek vervolgens naar de licentieserver. De licentieserver gebruikt informatie die uit de metagegevens voor de inhoud is geëxtraheerd voor het genereren van een licentie.

Als de client en server beide protocolversie 5 ondersteunen, is de aanvraag-URL &quot;Licence Server URL in metadata&quot; + &quot; [!DNL /flashaccess/license/v4]&quot;. Als protocolversie 3 het maximum is dat door de client of server wordt ondersteund, sturen Primetime DRM-clients vervolgens verificatieverzoeken naar &quot;Licentieserver-URL in metagegevens&quot; + &quot; [!DNL /flashaccess/license/v3]&quot;. Anders worden verificatieaanvragen verzonden naar &quot;Licentieserver-URL in metagegevens&quot; + &quot; [!DNL /flashaccess/license/v1]&quot;

Een apparaat kan meerdere licenties voor dezelfde inhoud hebben (dezelfde licentie-id), maar kan slechts één licentie voor een bepaalde licentie-id en een bepaalde DRM-beleidsidentiteitskaart hebben. Als het een licentie ontvangt met een dubbele LicenseID/PolicyID, vervangt de nieuwe licentie de oude alleen als de uitgiftedatum van de nieuwe licentie later is dan de uitgiftedatum van de bestaande licentie. Deze logica wordt gebruikt om licenties te verwerken die zijn ingesloten in inhoud. Daarom wordt het niet aanbevolen om meer dan één licentie met dezelfde DRM-beleidsidentiteitskaart in te sluiten in een blok inhoud. Dezelfde logica geldt voor licenties die via de ActionScript3-API `DRMManager.storeVoucher()` aan de client worden doorgegeven; als de klant al over een licentie met een latere uitgiftedatum beschikt, kan de opgegeven licentie worden genegeerd.

## Klassen {#section_190E3BEF316C4B09ACC21E4C2BAC5C75} voor het verwerken van licentieaanvragen

* `com.adobe.flashaccess.sdk.protocol.license.LicenseHandler` - Dit is de de managerklasse van het vergunningsverzoek. Het leest en ontleedt vergunningsverzoeken. De methode `getRequests()` retourneert een lijst met `LicenseRequestMessage`-objecten.
* `com.adobe.flashaccess.sdk.protocol.license.LicenseRequestMessage` - Dit is de aanvraagberichtklasse. De bezoeker zou door de `LicenseRequestMessage` lijst moeten herhalen die door `getRequests()` is teruggekeerd, en voor elk verzoek of zou of een vergunning moeten produceren of een foutencode plaatsen. Roep `LicenseRequestMessage.getContentInfo()` aan om informatie te verkrijgen die uit de inhoudsmeta-gegevens, met inbegrip van inhoudsidentiteitskaart, vergunning ID, en DRM beleid wordt gehaald.

Licenties en fouten worden tegelijk verzonden wanneer de methode `LicenseHandler.close()` wordt aangeroepen.

Zie de [Referentiedocumentatie van de DRM Server API](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/overview-summary.html) voor meer informatie.
