---
title: Overzicht
description: Overzicht
copied-description: true
exl-id: 267188d0-83f8-42dc-88e3-78b52945cb6c
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---

# Overzicht {#overview}

Om een licentie te verkrijgen, vormen clients een verzoek uit de metagegevens die zijn ingesloten in inhoud in het pakket, en verzenden ze dat verzoek vervolgens naar de licentieserver. De licentieserver gebruikt informatie die uit de metagegevens voor de inhoud is geëxtraheerd voor het genereren van een licentie.

Als de client en server beide protocolversie 5 ondersteunen, is de aanvraag-URL &quot;Licence Server URL in metadata&quot; + &quot; [!DNL /flashaccess/license/v4]&quot;. Als protocolversie 3 het maximum is dat door of de cliënt of de server wordt gesteund, verzenden de cliënten van Primetime DRM dan authentificatieverzoeken naar &quot;De Server URL van de Vergunning in meta-gegevens&quot; + &quot; [!DNL /flashaccess/license/v3]&quot;. Anders worden verificatieaanvragen verzonden naar &quot;Licentieserver-URL in metagegevens&quot; + &quot; [!DNL /flashaccess/license/v1]&quot;

Een apparaat kan meerdere licenties voor dezelfde inhoud hebben (dezelfde licentie-id), maar kan slechts één licentie voor een bepaalde licentie-id en een bepaalde DRM-beleidsidentiteitskaart hebben. Als het een licentie ontvangt met een dubbele LicenseID/PolicyID, vervangt de nieuwe licentie de oude alleen als de uitgiftedatum van de nieuwe licentie later is dan de uitgiftedatum van de bestaande licentie. Deze logica wordt gebruikt om licenties te verwerken die zijn ingesloten in inhoud. Daarom wordt het niet aanbevolen om meer dan één licentie met dezelfde DRM-beleidsidentiteitskaart in te sluiten in een blok inhoud. Dezelfde logica geldt voor licenties die via de `DRMManager.storeVoucher()` ActionScript3 API; als de klant al over een licentie met een latere uitgiftedatum beschikt, kan de opgegeven licentie worden genegeerd.

## Afhandelingsklassen voor licentieaanvragen {#section_190E3BEF316C4B09ACC21E4C2BAC5C75}

* `com.adobe.flashaccess.sdk.protocol.license.LicenseHandler` - Dit is de de managerklasse van het vergunningsverzoek. Het leest en ontleedt vergunningsverzoeken. haar `getRequests()` methode retourneert een lijst met `LicenseRequestMessage` objecten.
* `com.adobe.flashaccess.sdk.protocol.license.LicenseRequestMessage` - Dit is de aanvraagberichtklasse. De bezoeker zou door moeten herhalen `LicenseRequestMessage` lijst geretourneerd door `getRequests()`en voor elke aanvraag genereert u een licentie of stelt u een foutcode in. Bellen `LicenseRequestMessage.getContentInfo()` om informatie op te halen uit de metagegevens van de inhoud, zoals de inhoud-id, licentie-id en DRM-beleid.

Vergunningen en fouten worden tegelijk verzonden wanneer de `LicenseHandler.close()` wordt aangeroepen.

Zie de [Referentiedocumentatie voor de DRM Server-API](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/overview-summary.html) voor meer informatie.
