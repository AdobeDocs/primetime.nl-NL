---
description: U kunt aangepaste machtigingslogica aanroepen tijdens het aanschaffen van licenties om te bepalen of een licentie moet worden uitgegeven aan de client die deze aanvraagt.
title: Aangepaste extensies voor machtigingen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---

# Aangepaste extensies voor machtigingen{#custom-authorization-extensions}

U kunt aangepaste machtigingslogica aanroepen tijdens het aanschaffen van licenties om te bepalen of een licentie moet worden uitgegeven aan de client die deze aanvraagt.

Als u uw eigen uitbreiding van de klantenvergunning wilt uitvoeren, moet u eerst een blik nemen bij [!DNL SampleAuthorizer.java] voorbeeldcode in de map samples. De gecompileerde versie van dit voorbeeld bevindt zich in [!DNL flashaccess-license-server-ext-sample.jar].

Als u uw eigen uitbreiding wilt bouwen, moet u uitvoeren `com.adobe.flashaccess.server.license.extension.auth.IAuthorizer` interface en zorg ervoor [!DNL flashaccess-license-server-exts.jar] en [!DNL commons-logging.jar] bevinden zich in het bouwstijlpad ( [!DNL adobe-flashaccess-sdk.jar] moet ook in de bouwstijlweg als u bepaalde gebieden in `IMessageFacade`).

Als u de extensie wilt implementeren, moet u de klasse- of jar-bestanden kopiëren naar *LicenseServer.ConfigRoot* [!DNL /flashaccessserver/libs].

Als u de jar- of klassebestanden wilt bijwerken, moet u de server opnieuw starten voordat de bijgewerkte versie kan worden gebruikt. U moet ook de naam van de machtigingsklasse aan het dossier van de huurdersconfiguratie toevoegen.
