---
seo-title: Aangepaste extensies voor machtigingen
title: Aangepaste extensies voor machtigingen
description: Aangepaste machtigingslogica kan tijdens licentieverwerving worden aangeroepen om te beslissen of een licentie aan de verzoekende cliënt moet worden verleend.
seo-description: Aangepaste machtigingslogica kan tijdens licentieverwerving worden aangeroepen om te beslissen of een licentie aan de verzoekende cliënt moet worden verleend.
uuid: fb40db6f-30aa-46e3-9eeb-faff3cfedab1
translation-type: tm+mt
source-git-commit: fe9493d610bc6fb97d30351c707b73cda92c67a0

---


# Aangepaste extensies voor machtigingen {#custom-authorization-extensions}

Aangepaste machtigingslogica kan tijdens licentieverwerving worden aangeroepen om te beslissen of een licentie aan de verzoekende cliënt moet worden verleend.

Om uw eigen uitbreiding van de klantenvergunning uit te voeren, bekijk eerst de [!DNL SampleAuthorizer.java] steekproefcode die in de steekproeffolder wordt gevestigd (de gecompileerde versie van dit monster wordt gevestigd in flashaccess-vergunning-server-ext-sample.jar).

Om uw eigen uitbreiding te bouwen, voer de `com.adobe.flashaccess.server.license.extension.auth.IAuthorizer` interface uit en zorg ervoor `flashaccess-license-server-exts.jar` en `commons-logging.jar` op de bouwstijlweg `adobe-flashaccess-sdk.jar` moet ook op de bouwstijlweg zijn als u bepaalde gebieden in `IMessageFacade`) gebruikt. Als u de extensie wilt implementeren, kopieert u uw jar- of klassebestanden naar *LicenseServer.ConfigRoot* `/flashaccessserver/libs`. Als u de jar- of klassebestanden moet bijwerken, moet de server opnieuw worden gestart voordat de bijgewerkte versie wordt gebruikt. U moet ook de naam van de machtigingsklasse aan het dossier van de huurdersconfiguratie toevoegen.
