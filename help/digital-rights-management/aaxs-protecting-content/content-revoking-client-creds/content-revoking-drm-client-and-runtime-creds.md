---
title: Referenties van DRM-client en runtime intrekken
description: Referenties van DRM-client en runtime intrekken
copied-description: true
exl-id: f39d6523-9215-49ec-bb3b-e60fe6690dca
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# Referenties van DRM-client en runtime intrekken{#revoking-drm-client-and-runtime-credentials}

DRM/Runtime versies worden geïdentificeerd door veiligheidsniveau, versienummer, en andere attributen met inbegrip van OS en runtime. Als u de toegestane DRM/Runtime-versies wilt beperken, stelt u de modulebeperkingen in een beleid of in een `HandlerConfiguration`. Modulebeperkingen kunnen een minimaal beveiligingsniveau en een lijst met moduleversies bevatten die geen licentie mogen krijgen. Zie [Lijst van gewezen personen van DRM-clients die geen toegang hebben tot beveiligde inhoud](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-runtime-application-restrictions/content-blocklist-drm-clients.md) voor meer informatie over de kenmerken die worden gebruikt om een DRM/Runtime-module te identificeren.

Als het minimale beveiligingsniveau is ingesteld, moet de versie op de client (opgegeven in de computertoken) groter zijn dan of gelijk zijn aan de opgegeven waarde.

Als een lijst van uitgesloten versies wordt gespecificeerd en de versie van de cliënt om het even welke versie herkenningstekens in de lijst aanpast, zal de cliënt niet worden toegestaan om een recht te gebruiken die deze instantie ModuleRequirements bevat. Een module die overeenkomt met de versiegegevens, vereist dat alle parameters die in de versiegegevens zijn opgegeven, behalve de releaseversie, exact overeenkomen met de waarden van de modules. De releaseversie komt overeen als de waarde van de clientmodule kleiner is dan of gelijk is aan de waarde in de versiegegevens.

Als een inbreuk wordt gemeld met een bepaalde DRM-client of runtimeversie, kunnen de eigenaar van de inhoud en de contentdistributeur (die de licentieserver uitvoert) de server zodanig configureren dat deze weigeren licenties uit te geven gedurende een periode waarin Adobe geen oplossing beschikbaar heeft. Dit kan door `HandlerConfiguration` zoals hierboven beschreven, of door wijzigingen aan te brengen in al het beleid. In het laatste geval kunt u een lijst met beleidsupdates bijhouden en deze gebruiken om te controleren of een beleid is bijgewerkt of ingetrokken.

Als u een nieuwere versie van de Adobe® Flash® Player/Adobe® AIR® Runtime of de Adobe Content Protection-bibliotheek (DRM-module) nodig hebt, werkt u uw beleid bij zoals in [Een beleid bijwerken met de Java API](../../aaxs-protecting-content/content-working-with-policies/content-updating-policy-using-java-api.md) en maak een lijst met beleidsupdates of stel beperkingen in in `HandlerConfiguration` door `HandlerConfiguration.setRuntimeModuleRequirements()` of `HandlerConfiguration.setDRMModuleRequirements()`. Wanneer een gebruiker een nieuwe licentie aanvraagt waarvoor deze lijsten van gewezen personen zijn ingeschakeld, moeten de nieuwere runtimes en bibliotheken zijn geïnstalleerd voordat een licentie kan worden uitgegeven. Zie de voorbeeldcode in de [Een beleid bijwerken met de Java API](../../aaxs-protecting-content/content-working-with-policies/content-updating-policy-using-java-api.md).
