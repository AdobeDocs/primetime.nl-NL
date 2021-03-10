---
title: Domeinregistratieverzoeken afhandelen
description: Domeinregistratieverzoeken afhandelen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---


# De-Registratieverzoeken {#handle-domain-de-registration-requests} van het Domein behandelen

Als de clienttoepassing een domein moet verlaten, wordt de `DRMManager.removeFromDeviceGroup()`ActionScript-API of de `leaveLicenseDomain()` iOS-API aangeroepen om het deregistratieproces voor domeinen te starten. Domeinderegistratie is een proces in twee fasen. De client verzendt eerst een aanvraag voor de deregistratievoorvertoning. De domeinserver onderzoekt de aanvraag en bepaalt of de client het domein mag verlaten. Er kan een fout worden geretourneerd als de computer momenteel geen deel uitmaakt van het domein. Na een geslaagde reactie verwijdert de client de domeinreferenties en alle licenties die aan dat domein zijn uitgegeven. Vervolgens wordt een aanvraag tot verwijdering van de registratie verzonden.

* De klasse van de verzoekmanager is `com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationHandler`
* De klasse van het verzoekbericht is `com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationRequestMessage`
* Als zowel de client als server protocol versie 5 ondersteunen, is de aanvraag-URL &quot;Domain Server URL in metadata: + &quot; [!DNL /flashaccess/dereg/v4]&quot;. Anders is de aanvraag-URL de domeinserver-URL in metagegevens&quot; + &quot; [!DNL /flashaccess/dereg/v3]&quot;

Bij het verwerken van domeinderegistratievragen gebruikt de server `getRequestPhase()` om te bepalen of de client zich in de voorvertoning- of deregistratiefase bevindt. In de voorproeffase, onderzoekt de domeinserver het verzoek en bepaalt of de cliënt het domein mag verlaten omdat het verzoek kan worden ontkend. de aanvraag kan bijvoorbeeld worden afgewezen als de computer momenteel geen deel uitmaakt van het domein. In de deregistratiefase registreert de server het feit dat de computer het domein heeft verlaten. De server wordt sterk geadviseerd om de zelfde logica in het voorproefverzoek te evalueren zoals in het daadwerkelijke deregistratieverzoek om de kans van het tweede mislukken van de fase te minimaliseren.
