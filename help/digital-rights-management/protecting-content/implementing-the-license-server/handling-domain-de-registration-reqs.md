---
title: Domeinregistratieverzoeken afhandelen
description: Domeinregistratieverzoeken afhandelen
copied-description: true
exl-id: 14b97ba2-9344-4d84-8c52-f33126337454
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# Domeinregistratieverzoeken afhandelen {#handle-domain-de-registration-requests}

Als de clienttoepassing een domein moet verlaten, wordt het `DRMManager.removeFromDeviceGroup()`ActionScript API of de `leaveLicenseDomain()` iOS API start het deregistratieproces voor domeinen. Domeinderegistratie is een proces in twee fasen. De client verzendt eerst een aanvraag voor de deregistratievoorvertoning. De domeinserver onderzoekt de aanvraag en bepaalt of de client het domein mag verlaten. Er kan een fout worden geretourneerd als de computer momenteel geen deel uitmaakt van het domein. Na een geslaagde reactie verwijdert de client de domeinreferenties en alle licenties die aan dat domein zijn uitgegeven. Vervolgens wordt een aanvraag tot verwijdering van de registratie verzonden.

* De klasse request handler is `com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationHandler`
* De klasse request message is `com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationRequestMessage`
* Als zowel de client als server protocol versie 5 ondersteunen, is de aanvraag-URL &quot;Domain Server URL in metadata: + &quot; [!DNL /flashaccess/dereg/v4]&quot;. Anders is de aanvraag-URL de domeinserver-URL in metagegevens&quot; + &quot; [!DNL /flashaccess/dereg/v3]&quot;

Bij het verwerken van aanvragen voor deregistratie van domeinen, gebruikt de server `getRequestPhase()` om te bepalen of de cliënt in de voorproef of de deregistratiefase is. In de voorproeffase, onderzoekt de domeinserver het verzoek en bepaalt of de cliënt het domein mag verlaten omdat het verzoek kan worden ontkend. de aanvraag kan bijvoorbeeld worden afgewezen als de computer momenteel geen deel uitmaakt van het domein. In de deregistratiefase registreert de server het feit dat de computer het domein heeft verlaten. De server wordt sterk geadviseerd om de zelfde logica in het voorproefverzoek te evalueren zoals in het daadwerkelijke deregistratieverzoek om de kans van het tweede mislukken van de fase te minimaliseren.
