---
seo-title: Aangepaste extensies voor machtigingen
title: Aangepaste extensies voor machtigingen
description: Aangepaste machtigingslogica kan tijdens licentieverwerving worden aangeroepen om te beslissen of een licentie aan de verzoekende cliënt moet worden verleend.
seo-description: Aangepaste machtigingslogica kan tijdens licentieverwerving worden aangeroepen om te beslissen of een licentie aan de verzoekende cliënt moet worden verleend.
uuid: fb40db6f-30aa-46e3-9eeb-faff3cfedab1
translation-type: tm+mt
source-git-commit: fe9493d610bc6fb97d30351c707b73cda92c67a0
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---


# Aangepaste extensies voor machtigingen {#custom-authorization-extensions}

Aangepaste machtigingslogica kan tijdens licentieverwerving worden aangeroepen om te beslissen of een licentie aan de verzoekende cliënt moet worden verleend.

Om uw eigen uitbreiding van de klantenvergunning uit te voeren, bekijk eerst [!DNL SampleAuthorizer.java] steekproefcode in de steekproeffolder (de gecompileerde versie van dit monster wordt gevestigd in flashaccess-license-server-ext-sample.jar).

Als u uw eigen extensie wilt maken, implementeert u de `com.adobe.flashaccess.server.license.extension.auth.IAuthorizer`-interface en zorgt u ervoor dat `flashaccess-license-server-exts.jar` en `commons-logging.jar` zich op het bouwpad bevinden. `adobe-flashaccess-sdk.jar` moet zich ook op het bouwpad bevinden als u bepaalde velden gebruikt in `IMessageFacade`). Als u de extensie wilt implementeren, kopieert u uw jar- of klassebestanden naar *LicenseServer.ConfigRoot* `/flashaccessserver/libs`. Als u de jar- of klassebestanden moet bijwerken, moet de server opnieuw worden gestart voordat de bijgewerkte versie wordt gebruikt. U moet ook de naam van de machtigingsklasse aan het dossier van de huurdersconfiguratie toevoegen.
