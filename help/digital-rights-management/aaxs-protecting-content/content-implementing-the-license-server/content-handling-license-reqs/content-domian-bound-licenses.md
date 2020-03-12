---
seo-title: Domeingebonden licenties afgeven
title: Domeingebonden licenties afgeven
uuid: 175d3b7d-d1df-44ee-85ad-a0db4a1bdb9d
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Domeingebonden licenties afgeven{#issuing-domain-bound-licenses}

Om een vergunning uit te geven die een beleid gebruikt dat domeinregistratie vereist, moet het verzoek van de cliënt een geldig domeinteken omvatten dat door de domeinserver wordt uitgegeven die in het beleid wordt gespecificeerd. Wanneer de client een licentie aanvraagt, worden de domeintokens automatisch opgenomen voor domeinservers die zijn opgegeven in de metagegevens voor inhoud, als deze zijn geregistreerd bij die domeinservers. Als het geselecteerde beleid domeinregistratie vereist, zal SDK automatisch een domeinteken van het verzoek selecteren om de vergunning aan te binden, of een fout terugkeren als geen aangewezen domeinteken werd gevonden.

Een domeinteken wordt als geldig beschouwd als het niet verlopen is en als het door een geautoriseerd Domein CA werd uitgegeven. De vergunningsserver moet de domeinautoriteiten specificeren waarvan het domeintokens door het vormen zal goedkeuren `HandlerConfiguration.setDomainCAs()`. Als er geen domein-CA&#39;s zijn geconfigureerd, kan de licentieserver geen domeingebonden licenties uitgeven.

Als de metagegevens meerdere beleidsregels bevatten, kan de bedrijfslogica van de licentieserver een beleid selecteren dat is gebaseerd op het feit of de client een domeintoken heeft gepresenteerd. Gebruik deze optie `LicenseRequestMessage.getDomainTokens()` om de domeinen te bepalen waarmee de client zich heeft geregistreerd.
