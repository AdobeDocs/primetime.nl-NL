---
seo-title: Domeinregistratieverzoeken afhandelen
title: Domeinregistratieverzoeken afhandelen
uuid: 80dbbb60-9005-4a3d-86bf-26cdbed86452
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Domeinregistratieverzoeken afhandelen {#handle-domain-de-registration-requests}

Als de clienttoepassing een domein moet verlaten, wordt de `DRMManager.removeFromDeviceGroup()`ActionScript-API of de `leaveLicenseDomain()` iOS-API aangeroepen om het deregistratieproces voor domeinen te starten. Domeinderegistratie is een proces in twee fasen. De client verzendt eerst een aanvraag voor de deregistratievoorvertoning. De domeinserver onderzoekt de aanvraag en bepaalt of de client het domein mag verlaten. Er kan een fout worden geretourneerd als de computer momenteel geen deel uitmaakt van het domein. Na een geslaagde reactie verwijdert de client de domeinreferenties en alle licenties die aan dat domein zijn uitgegeven. Vervolgens wordt een aanvraag tot verwijdering van de registratie verzonden.

* De klasse request handler is `com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationHandler`
* De klasse request message is `com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationRequestMessage`
* Als zowel de client als server protocol versie 5 ondersteunen, is de aanvraag-URL &quot;Domain Server URL in metadata: + &quot; [!DNL /flashaccess/dereg/v4]&quot;. Anders is de aanvraag-URL de domeinserver-URL in metagegevens&quot; + &quot; [!DNL /flashaccess/dereg/v3]&quot;

Bij het verwerken van aanvragen voor deregistratie van domeinen, gebruikt de server `getRequestPhase()` om te bepalen of de client zich in de voorvertoning- of deregistratiefase bevindt. In de voorproeffase, onderzoekt de domeinserver het verzoek en bepaalt of de cliënt het domein mag verlaten omdat het verzoek kan worden ontkend. de aanvraag kan bijvoorbeeld worden afgewezen als de computer momenteel geen deel uitmaakt van het domein. In de deregistratiefase registreert de server het feit dat de computer het domein heeft verlaten. De server wordt sterk geadviseerd om de zelfde logica in het voorproefverzoek te evalueren zoals in het daadwerkelijke deregistratieverzoek om de kans van het tweede mislukken van de fase te minimaliseren.
