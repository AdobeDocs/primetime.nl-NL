---
seo-title: Algemene serverconfiguratiegegevens
title: Algemene serverconfiguratiegegevens
uuid: f6d6cb01-2645-4cd2-83ec-0272323a67cd
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Algemene serverconfiguratiegegevens{#global-server-configuration-data}

Naast configuratie die door de vergunningsserver wordt gebruikt, `HandlerConfiguration` slaat configuratieinformatie op die naar de cliënt kan worden verzonden om te controleren hoe de vergunningen worden afgedwongen. Dit gebeurt door een `ServerConfigData` klasse te maken en aan te roepen `HandlerConfiguration.setServerConfigData()` (deze instellingen gelden alleen voor licenties die door deze licentieserver zijn uitgegeven). De tolerantie van de klokwindback is één bezit dat door de vergunningsserver kan worden geplaatst om te controleren hoe de cliënt vergunningen afdwingt. Standaard kunnen gebruikers de computerklok 4 uur terugzetten zonder licenties ongeldig te maken. Als een licentieserveroperator een andere instelling wil gebruiken, kan de nieuwe waarde in de `ServerConfigData` klasse worden ingesteld. Wanneer u de waarde van om het even welk van deze montages verandert, ben zeker om het versieaantal te verhogen door te roepen `setVersion()`. De nieuwe waarden worden alleen naar de client verzonden als de versie op de client lager is dan de huidige `ServerConfigData` versie.
