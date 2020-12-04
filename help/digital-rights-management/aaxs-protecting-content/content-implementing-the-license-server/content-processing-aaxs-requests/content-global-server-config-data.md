---
seo-title: Algemene serverconfiguratiegegevens
title: Algemene serverconfiguratiegegevens
uuid: f6d6cb01-2645-4cd2-83ec-0272323a67cd
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---


# Algemene configuratiegegevens van de server{#global-server-configuration-data}

Naast de configuratie die door de licentieserver wordt gebruikt, slaat `HandlerConfiguration` configuratiegegevens op die naar de client kunnen worden verzonden om te bepalen hoe licenties worden afgedwongen. Dit gebeurt door een `ServerConfigData`-klasse te maken en `HandlerConfiguration.setServerConfigData()` aan te roepen (deze instellingen zijn alleen van toepassing op licenties die door deze licentieserver zijn uitgegeven). De tolerantie van de klokwindback is één bezit dat door de vergunningsserver kan worden geplaatst om te controleren hoe de cliënt vergunningen afdwingt. Standaard kunnen gebruikers de computerklok 4 uur terugzetten zonder licenties ongeldig te maken. Als een licentieserveroperator een andere instelling wil gebruiken, kan de nieuwe waarde worden ingesteld in de klasse `ServerConfigData`. Wanneer u de waarde van om het even welk van deze montages verandert, ben zeker om het versieaantal te verhogen door `setVersion()` te roepen. De nieuwe waarden worden alleen naar de client verzonden als de versie op de client lager is dan de huidige `ServerConfigData`-versie.
