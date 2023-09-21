---
title: Aangepaste extensies voor machtigingen
description: Aangepaste machtigingslogica kan tijdens licentieverwerving worden aangeroepen om te beslissen of een licentie aan de verzoekende cliënt moet worden verleend.
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# Aangepaste extensies voor machtigingen {#custom-authorization-extensions}

Aangepaste machtigingslogica kan tijdens licentieverwerving worden aangeroepen om te beslissen of een licentie aan de verzoekende cliënt moet worden verleend.

Om uw eigen uitbreiding van de klantenvergunning uit te voeren, bekijk eerst [!DNL SampleAuthorizer.java] voorbeeldcode in de steekproeffolder (de gecompileerde versie van deze steekproef wordt gevestigd in flashaccess-license-server-ext-sample.jar).

Om uw eigen uitbreiding te bouwen, voer uit `com.adobe.flashaccess.server.license.extension.auth.IAuthorizer` interface en zorg ervoor `flashaccess-license-server-exts.jar` en `commons-logging.jar` bevinden zich op het bouwstijlpad `adobe-flashaccess-sdk.jar` moet zich ook op de bouwstijlweg bevinden als u bepaalde gebieden in `IMessageFacade`). Als u de extensie wilt implementeren, kopieert u uw jar- of klassebestanden naar *LicenseServer.ConfigRoot* `/flashaccessserver/libs`. Als u de jar- of klassebestanden moet bijwerken, moet de server opnieuw worden gestart voordat de bijgewerkte versie wordt gebruikt. U moet ook de naam van de machtigingsklasse aan het dossier van de huurdersconfiguratie toevoegen.
