---
title: Algemene serverconfiguratiegegevens
description: Algemene serverconfiguratiegegevens
copied-description: true
exl-id: 0afce045-1dd7-4fe7-84b7-d60068b3423a
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---

# Algemene serverconfiguratiegegevens{#global-server-configuration-data}

Naast de configuratie die door de licentieserver wordt gebruikt, `HandlerConfiguration` slaat configuratieinformatie op die naar de cliënt kan worden verzonden om te controleren hoe de vergunningen worden afgedwongen. Dit doet u door een `ServerConfigData` klasse en aanroepen `HandlerConfiguration.setServerConfigData()` (Deze instellingen zijn alleen van toepassing op licenties die door deze licentieserver zijn uitgegeven). De tolerantie van de klokwindback is één bezit dat door de vergunningsserver kan worden geplaatst om te controleren hoe de cliënt vergunningen afdwingt. Standaard kunnen gebruikers de computerklok 4 uur terugzetten zonder licenties ongeldig te maken. Als een licentieserveroperator een andere instelling wil gebruiken, kan de nieuwe waarde worden ingesteld in het dialoogvenster `ServerConfigData` klasse. Wanneer u de waarde van een van deze instellingen wijzigt, moet u het versienummer verhogen door `setVersion()`. De nieuwe waarden worden alleen naar de client verzonden als de versie op de client lager is dan de huidige `ServerConfigData` versie.
