---
title: Domeinregistratieverzoeken afhandelen
description: Domeinregistratieverzoeken afhandelen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# Domeinregistratieverzoeken afhandelen {#handle-domain-de-registration-requests}

Als de clienttoepassing een domein moet verlaten, wordt het `DRMManager.removeFromDeviceGroup()`ActionScript-API of de `leaveLicenseDomain()` iOS API start het deregistratieproces voor domeinen. Domeinderegistratie is een proces in twee fasen. De client verzendt eerst een aanvraag voor de deregistratievoorvertoning. De domeinserver onderzoekt de aanvraag en bepaalt of de client het domein mag verlaten. Er kan een fout worden geretourneerd als de computer momenteel geen deel uitmaakt van het domein. Na een geslaagde reactie verwijdert de client de domeinreferenties en alle licenties die aan dat domein zijn uitgegeven. Vervolgens wordt een aanvraag tot verwijdering van de registratie verzonden.

* De klasse request handler is `com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationHandler`
* De klasse request message is `com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationRequestMessage`
* Als zowel de client als het serverondersteuningsprotocol versie 5 is, is de aanvraag-URL &quot;Domain Server URL in metadata: + &quot; [!DNL /flashaccess/dereg/v4]&quot;. Anders is de aanvraag-URL de domeinserver-URL in metagegevens&quot; + &quot; [!DNL /flashaccess/dereg/v3]&quot;

Bij het verwerken van aanvragen voor deregistratie van domeinen, gebruikt de server `getRequestPhase()` om te bepalen of de cliënt in de voorproef of de deregistratiefase is. In de voorproeffase, onderzoekt de domeinserver het verzoek en bepaalt of de cliënt het domein mag verlaten omdat het verzoek kan worden ontkend; bijvoorbeeld, kan het verzoek worden ontkend als de machine momenteel geen deel van het domein uitmaakt. In de deregistratiefase registreert de server het feit dat de computer het domein heeft verlaten. De server wordt sterk geadviseerd om de zelfde logica in het voorproefverzoek te evalueren zoals in het daadwerkelijke deregistratieverzoek om de kans van de tweede fase te minimaliseren ontbreken.
