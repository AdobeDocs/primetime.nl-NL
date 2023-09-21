---
title: Algemene serverconfiguratiegegevens
description: Algemene serverconfiguratiegegevens
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---

# Algemene serverconfiguratiegegevens{#global-server-configuration-data}

Naast de configuratie die door de licentieserver wordt gebruikt, `HandlerConfiguration` slaat configuratieinformatie op die naar de cliënt kan worden verzonden om te controleren hoe de vergunningen worden afgedwongen. Dit doet u door een `ServerConfigData` klasse en aanroepen `HandlerConfiguration.setServerConfigData()` (Deze instellingen zijn alleen van toepassing op licenties die door deze licentieserver zijn uitgegeven). De tolerantie van de klokwindback is één bezit dat door de vergunningsserver kan worden geplaatst om te controleren hoe de cliënt vergunningen afdwingt. Standaard kunnen gebruikers de computerklok 4 uur terugzetten zonder licenties ongeldig te maken. Als een licentieserveroperator een andere instelling wil gebruiken, kan de nieuwe waarde worden ingesteld in het dialoogvenster `ServerConfigData` klasse. Wanneer u de waarde van een van deze instellingen wijzigt, moet u het versienummer verhogen door `setVersion()`. De nieuwe waarden worden alleen naar de client verzonden als de versie op de client lager is dan de huidige `ServerConfigData` versie.
