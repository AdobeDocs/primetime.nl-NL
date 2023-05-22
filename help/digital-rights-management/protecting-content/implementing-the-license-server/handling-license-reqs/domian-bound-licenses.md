---
title: Domeingebonden licenties afgeven
description: Domeingebonden licenties afgeven
copied-description: true
exl-id: c29e61e5-d05a-4744-9ec8-7508ed814a57
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# Domeingebonden licenties afgeven{#issuing-domain-bound-licenses}

Om een vergunning uit te geven die een beleid DRM gebruikt dat domeinregistratie vereist, moet het verzoek van de cliënt een geldig domeinteken omvatten dat door de domeinserver wordt uitgegeven die in het beleid wordt gespecificeerd. Wanneer de client een licentie aanvraagt, worden de domeintokens automatisch opgenomen voor elke domeinserver die is opgegeven in de metagegevens voor inhoud, mits deze is geregistreerd bij die domeinservers. Als voor het geselecteerde DRM-beleid domeinregistratie is vereist, selecteert de SDK vervolgens automatisch een domeintoken in de aanvraag om de licentie te binden aan of retourneert deze een fout als er geen geschikt domeintoken is gevonden.

Een domeinteken wordt als geldig beschouwd als het niet verlopen is en als het door een geautoriseerd Domein CA werd uitgegeven. De vergunningsserver moet de domeinautoriteiten specificeren waarvan het dan domeintokens goedkeurt door te vormen `HandlerConfiguration.setDomainCAs()`. Als er geen domein-CA&#39;s zijn geconfigureerd, kan de licentieserver geen domeingebonden licenties uitgeven.

Als de metagegevens meerdere DRM-beleidsregels bevatten, kan de bedrijfslogica van de licentieserver een DRM-beleid selecteren dat is gebaseerd op het feit of de client een domeintoken heeft gepresenteerd. U kunt `LicenseRequestMessage.getDomainTokens()` om de domeinen te bepalen waarmee de cliënt heeft geregistreerd.
