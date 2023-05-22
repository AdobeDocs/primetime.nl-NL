---
title: Referenties van DRM-client en runtime intrekken
description: Referenties van DRM-client en runtime intrekken
copied-description: true
exl-id: 3a91a256-ab01-48d8-99f3-854195faae6f
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# Referenties van DRM-client en runtime intrekken {#revoking-drm-client-and-runtime-credentials}

DRM/Runtime versies worden geïdentificeerd door veiligheidsniveau, versienummer, en andere attributen met inbegrip van het Besturingssysteem en runtime. Als u de toegestane DRM/Runtime-versies wilt beperken, stelt u de modulebeperkingen in een DRM-beleid of in een `HandlerConfiguration`. Modulebeperkingen kunnen een minimaal beveiligingsniveau en een lijst met moduleversies bevatten die geen licentie mogen krijgen.

Zie [Lijst van gewezen personen van DRM-clients die geen toegang hebben tot beveiligde inhoud](../../protecting-content/introduction/usage-rules/runtime-application-restrictions/blocklist-drm-clients.md) voor meer informatie over de kenmerken die worden gebruikt om een DRM/Runtime-module te identificeren.

Als het minimale beveiligingsniveau is ingesteld, moet de versie op de client (opgegeven in de computertoken) groter zijn dan of gelijk zijn aan de opgegeven waarde.

Als een lijst van uitgesloten versies wordt gespecificeerd en de versie van de cliënt om het even welke versie herkenningstekens in de lijst aanpast, zal de cliënt niet worden toegestaan om een recht te gebruiken die deze instantie ModuleRequirements bevat. Een module die overeenkomt met de versiegegevens, vereist dat alle parameters die in de versiegegevens zijn opgegeven, behalve de releaseversie, exact overeenkomen met de waarden van de modules. De releaseversie komt overeen als de waarde van de clientmodule kleiner is dan of gelijk is aan de waarde in de versiegegevens.

Als een inbreuk wordt gemeld met een bepaalde DRM-client of runtimeversie, kunnen de eigenaar van de inhoud en de contentdistributeur (die de licentieserver uitvoert) de server zodanig configureren dat deze weigeren licenties uit te geven gedurende een periode waarin Adobe geen oplossing beschikbaar heeft. Dit kan door `HandlerConfiguration` zoals hierboven beschreven, of door wijzigingen aan te brengen in alle DRM-beleidsregels. In het laatste geval kunt u een DRM-lijst met beleidsupdates bijhouden en deze gebruiken om te controleren of een DRM-beleid is bijgewerkt of ingetrokken.

Als u een nieuwere versie van de Runtime van Adobe Flash Player/Adobe AIR of van de Adobe Inhoud van de Bescherming van de Bibliotheek (DRM module) vereist, moet u uw beleid DRM bijwerken.

Zie [Een beleid bijwerken met de Java API](../../protecting-content/working-policies-overview/updating-policy-using-java-api.md).

Vervolgens moet u een lijst met DRM-beleidsupdates maken of beperkingen instellen in `HandlerConfiguration` door `HandlerConfiguration.setRuntimeModuleRequirements()` of `HandlerConfiguration.setDRMModuleRequirements()`. Wanneer een gebruiker een nieuwe licentie aanvraagt waarvoor de opgegeven lijsten van gewezen personen zijn ingeschakeld, moet u de nieuwste runtimes en bibliotheken installeren voordat een licentie kan worden uitgegeven.

Zie de voorbeeldcode in [Een beleid bijwerken met de Java API Voor een voorbeeld in de bloklijst DRM en runtimeversies](../../protecting-content/working-policies-overview/updating-policy-using-java-api.md) voor een voorbeeld over de bloklijst van DRM en runtime versies.
