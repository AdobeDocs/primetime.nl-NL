---
description: U kunt aangepaste machtigingslogica aanroepen tijdens het aanschaffen van licenties om te bepalen of een licentie moet worden uitgegeven aan de client die deze aanvraagt.
seo-description: U kunt aangepaste machtigingslogica aanroepen tijdens het aanschaffen van licenties om te bepalen of een licentie moet worden uitgegeven aan de client die deze aanvraagt.
seo-title: Aangepaste extensies voor machtigingen
title: Aangepaste extensies voor machtigingen
uuid: 588b05e5-3402-4586-bbd4-58b7e9a58ee4
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---


# Aangepaste extensies voor machtigingen{#custom-authorization-extensions}

U kunt aangepaste machtigingslogica aanroepen tijdens het aanschaffen van licenties om te bepalen of een licentie moet worden uitgegeven aan de client die deze aanvraagt.

Als u uw eigen uitbreiding van de klantenvergunning wilt uitvoeren, moet u eerst een blik bij de [!DNL SampleAuthorizer.java] steekproefcode nemen die in de steekproeffolder wordt gevestigd. De gecompileerde versie van dit voorbeeld bevindt zich in [!DNL flashaccess-license-server-ext-sample.jar].

Als u uw eigen uitbreiding wilt bouwen, moet u `com.adobe.flashaccess.server.license.extension.auth.IAuthorizer` interface uitvoeren en ervoor zorgen [!DNL flashaccess-license-server-exts.jar] en [!DNL commons-logging.jar] in de bouwstijlweg zijn ( [!DNL adobe-flashaccess-sdk.jar] moet ook in de bouwstijlweg zijn als u bepaalde gebieden in `IMessageFacade` gebruikt).

Als u de extensie wilt implementeren, moet u de jar- of klassebestanden kopiëren naar *LicenseServer.ConfigRoot* [!DNL /flashaccessserver/libs].

Als u de jar- of klassebestanden wilt bijwerken, moet u de server opnieuw starten voordat de bijgewerkte versie kan worden gebruikt. U moet ook de naam van de machtigingsklasse aan het dossier van de huurdersconfiguratie toevoegen.
