---
seo-title: Domeinregistratieverzoeken afhandelen
title: Domeinregistratieverzoeken afhandelen
uuid: 6f056b2b-374d-4e4d-926a-68605b2c923b
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---


# De-Registratieverzoeken van het Domein behandelen{#handling-domain-de-registration-requests}

Als de clienttoepassing een domein moet verlaten, wordt de `DRMManager.removeFromDeviceGroup()`ActionScript-API of de `leaveLicenseDomain()` iOS-API aangeroepen om het deregistratieproces voor domeinen te starten. Domeinderegistratie is een proces in twee fasen. De client verzendt eerst een aanvraag voor de deregistratievoorvertoning. De domeinserver onderzoekt de aanvraag en bepaalt of de client het domein mag verlaten (er kan een fout worden geretourneerd als de computer momenteel geen deel uitmaakt van het domein). Na een geslaagde reactie verwijdert de client de domeinreferenties en eventuele licenties die aan dat domein zijn uitgegeven en verzendt vervolgens een aanvraag tot deregistratie.

* De klasse van de verzoekmanager is `com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationHandler`
* De klasse van het verzoekbericht is `com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationRequestMessage`
* Als zowel de client als server protocol versie 5 ondersteunen, is de aanvraag-URL &quot;Domain Server URL in metadata: + &quot;/flashaccess/dereg/v4&quot;. Anders is de aanvraag-URL de domeinserver-URL in metagegevens&quot; + &quot;/flashaccess/dereg/v3&quot;

Bij het verwerken van domeinderegistratievragen gebruikt de server `getRequestPhase()` om te bepalen of de client zich in de voorvertoning- of deregistratiefase bevindt. In de voorproeffase, onderzoekt de domeinserver het verzoek en bepaalt of de cliënt wordt toegelaten om het domein te verlaten (het verzoek kan worden ontkend, bijvoorbeeld, als de machine momenteel geen deel van het domein is). In de deregistratiefase registreert de server het feit dat de computer het domein heeft verlaten. De server wordt sterk geadviseerd om de zelfde logica in het voorproefverzoek te evalueren zoals in het daadwerkelijke deregistratieverzoek om de kans van het tweede mislukken van de fase te minimaliseren.
