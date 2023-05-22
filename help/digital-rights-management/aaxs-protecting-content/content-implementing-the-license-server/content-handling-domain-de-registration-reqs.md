---
title: Domeinregistratieverzoeken afhandelen
description: Domeinregistratieverzoeken afhandelen
copied-description: true
exl-id: f29507b5-d32a-4b22-a02e-6701b86db133
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Domeinregistratieverzoeken afhandelen{#handling-domain-de-registration-requests}

Als de clienttoepassing een domein moet verlaten, wordt het `DRMManager.removeFromDeviceGroup()`ActionScript API of de `leaveLicenseDomain()` iOS API start het deregistratieproces voor domeinen. Domeinderegistratie is een proces in twee fasen. De client verzendt eerst een aanvraag voor de deregistratievoorvertoning. De domeinserver onderzoekt de aanvraag en bepaalt of de client het domein mag verlaten (er kan een fout worden geretourneerd als de computer momenteel geen deel uitmaakt van het domein). Na een geslaagde reactie verwijdert de client de domeinreferenties en eventuele licenties die aan dat domein zijn uitgegeven en verzendt vervolgens een aanvraag tot deregistratie.

* De klasse request handler is `com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationHandler`
* De klasse request message is `com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationRequestMessage`
* Als zowel de client als server protocol versie 5 ondersteunen, is de aanvraag-URL &quot;Domain Server URL in metadata: + &quot;/flashaccess/dereg/v4&quot;. Anders is de aanvraag-URL de domeinserver-URL in metagegevens&quot; + &quot;/flashaccess/dereg/v3&quot;

Bij het verwerken van aanvragen voor deregistratie van domeinen, gebruikt de server `getRequestPhase()` om te bepalen of de cliënt in de voorproef of de deregistratiefase is. In de voorproeffase, onderzoekt de domeinserver het verzoek en bepaalt of de cliënt wordt toegelaten om het domein te verlaten (het verzoek kan worden ontkend, bijvoorbeeld, als de machine momenteel geen deel van het domein is). In de deregistratiefase registreert de server het feit dat de computer het domein heeft verlaten. De server wordt sterk geadviseerd om de zelfde logica in het voorproefverzoek te evalueren zoals in het daadwerkelijke deregistratieverzoek om de kans van het tweede mislukken van de fase te minimaliseren.
