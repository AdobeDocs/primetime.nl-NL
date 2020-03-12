---
seo-title: Referenties van DRM-client en runtime intrekken
title: Referenties van DRM-client en runtime intrekken
uuid: 774b8ac7-51bb-42fc-a05d-cfa718e24a81
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Referenties van DRM-client en runtime intrekken{#revoking-drm-client-and-runtime-credentials}

DRM/Runtime versies worden geïdentificeerd door veiligheidsniveau, versienummer, en andere attributen met inbegrip van OS en runtime. Als u de toegestane DRM/Runtime-versies wilt beperken, stelt u de modulebeperkingen in een beleid of in een `HandlerConfiguration`beleid in. Modulebeperkingen kunnen een minimaal beveiligingsniveau en een lijst met moduleversies bevatten die geen licentie mogen krijgen. Zie [Zwart-lijst met DRM-clients waarvoor de toegang tot beveiligde inhoud](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-runtime-application-restrictions/content-blacklist-drm-clients.md) is beperkt voor meer informatie over de kenmerken die worden gebruikt om een DRM/Runtime-module te identificeren.

Als het minimale beveiligingsniveau is ingesteld, moet de versie op de client (opgegeven in de computertoken) groter zijn dan of gelijk zijn aan de opgegeven waarde.

Als een lijst van uitgesloten versies wordt gespecificeerd en de versie van de cliënt om het even welke versie herkenningstekens in de lijst aanpast, zal de cliënt niet worden toegestaan om een recht te gebruiken die deze instantie ModuleRequirements bevat. Een module die overeenkomt met de versiegegevens, vereist dat alle parameters die in de versiegegevens zijn opgegeven, behalve de releaseversie, exact overeenkomen met de waarden van de modules. De releaseversie komt overeen als de waarde van de clientmodule kleiner is dan of gelijk is aan de waarde in de versiegegevens.

Als er een schending wordt gemeld met een bepaalde DRM-client of runtimeversie, kunnen de eigenaar van de inhoud en de distributeur van de inhoud (die de licentieserver uitvoert) de server zodanig configureren dat deze weigeren licenties uit te geven gedurende een periode waarin Adobe geen oplossing beschikbaar heeft. Dit kan door `HandlerConfiguration` zoals hierboven beschreven worden gevormd, of door veranderingen in al beleid aan te brengen. In het laatste geval kunt u een lijst met beleidsupdates bijhouden en deze gebruiken om te controleren of een beleid is bijgewerkt of ingetrokken.

Als u een nieuwere versie van de runtime Adobe® Flash® Player/Adobe® AIR® of de Adobe Content Protection-bibliotheek (DRM-module) nodig hebt, werkt u uw beleid bij zoals wordt weergegeven in Een beleid bijwerken met de Java API [en maakt u een lijst met beleidsupdates of stelt u beperkingen in](../../aaxs-protecting-content/content-working-with-policies/content-updating-policy-using-java-api.md) door een beleid aan te roepen `HandlerConfiguration` of `HandlerConfiguration.setRuntimeModuleRequirements()` `HandlerConfiguration.setDRMModuleRequirements()`. Wanneer een gebruiker een nieuwe licentie aanvraagt waarvoor deze zwarte lijsten zijn ingeschakeld, moeten de nieuwere runtimes en bibliotheken zijn geïnstalleerd voordat een licentie kan worden afgegeven. Zie de voorbeeldcode in [Een beleid bijwerken met de Java API](../../aaxs-protecting-content/content-working-with-policies/content-updating-policy-using-java-api.md)voor een voorbeeld over het op een zwarte lijst zetten van DRM- en runtimeversies.
