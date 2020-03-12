---
seo-title: Overzicht
title: Overzicht
uuid: 2bbf0aa1-df35-429d-84df-db357fa53e47
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Overzicht {#overview}

Om een licentie te verkrijgen, vormen clients een verzoek uit de metagegevens die zijn ingesloten in inhoud in het pakket, en verzenden ze dat verzoek vervolgens naar de licentieserver. De licentieserver gebruikt informatie die uit de metagegevens voor de inhoud is geëxtraheerd voor het genereren van een licentie.

Als de client en server beide protocolversie 5 ondersteunen, is de aanvraag-URL &quot;Licence Server URL in metadata&quot; + &quot; [!DNL /flashaccess/license/v4]&quot;. Als protocolversie 3 het maximum is dat door of de cliënt of de server wordt gesteund, verzenden de cliënten van Primetime DRM dan authentificatieverzoeken naar &quot;Server URL van de Vergunning in meta-gegevens&quot; + &quot; [!DNL /flashaccess/license/v3]&quot;. Anders worden verificatieaanvragen verzonden naar &quot;Licentieserver-URL in metagegevens&quot; + &quot; [!DNL /flashaccess/license/v1]&quot;

Een apparaat kan meerdere licenties voor dezelfde inhoud hebben (dezelfde licentie-id), maar kan slechts één licentie voor een bepaalde licentie-id en een bepaalde DRM-beleidsidentiteitskaart hebben. Als het een licentie ontvangt met een dubbele LicenseID/PolicyID, vervangt de nieuwe licentie de oude alleen als de uitgiftedatum van de nieuwe licentie later is dan de uitgiftedatum van de bestaande licentie. Deze logica wordt gebruikt om licenties te verwerken die zijn ingesloten in inhoud. Daarom wordt het niet geadviseerd om meer dan één vergunning met zelfde identiteitskaart van het Beleid DRM in een brok van inhoud in te bedden. Dezelfde logica is van toepassing op licenties die via de `DRMManager.storeVoucher()` ActionScript3-API aan de client worden doorgegeven; als de klant al over een licentie met een latere uitgiftedatum beschikt, kan de opgegeven licentie worden genegeerd.

## Afhandelingsklassen voor licentieaanvragen {#section_190E3BEF316C4B09ACC21E4C2BAC5C75}

* `com.adobe.flashaccess.sdk.protocol.license.LicenseHandler` - Dit is de de managerklasse van het vergunningsverzoek. Het leest en ontleedt vergunningsverzoeken. De `getRequests()` methode retourneert een lijst met `LicenseRequestMessage` objecten.
* `com.adobe.flashaccess.sdk.protocol.license.LicenseRequestMessage` - Dit is de aanvraagberichtklasse. De bezoeker zou door de `LicenseRequestMessage` lijst moeten herhalen door is teruggekeerd `getRequests()`, en voor elk verzoek of produceert een vergunning of plaatst een foutencode. Vraag `LicenseRequestMessage.getContentInfo()` om informatie te verkrijgen die uit de inhoudsmeta-gegevens, met inbegrip van inhoudsidentiteitskaart, vergunning ID, en beleid DRM wordt gehaald.

Licenties en fouten worden tegelijk verzonden wanneer de `LicenseHandler.close()` methode wordt aangeroepen.

Zie de [DRM Server API-naslagdocumentatie](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/overview-summary.html) voor meer informatie.
