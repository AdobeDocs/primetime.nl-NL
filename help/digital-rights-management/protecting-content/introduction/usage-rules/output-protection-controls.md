---
seo-title: Besturingselementen voor uitvoerbeveiliging
title: Besturingselementen voor uitvoerbeveiliging
uuid: a0518392-cd33-4ef0-834c-f90145a9b421
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 0%

---


# Besturingselementen voor uitvoerbeveiliging{#output-protection-controls}

De uitvoerbeveiliging bepaalt de parameter of de uitvoer naar externe renderapparaten is beveiligd. U kunt onafhankelijk beperkingen voor analoge en digitale uitvoer opgeven.

Bepaalt of uitvoer naar externe renderingapparaten moet worden beperkt. Een extern apparaat wordt gedefinieerd als een video- of audioapparaat dat niet in de computer is ingesloten. Geïntegreerde beeldschermen, zoals in notebookcomputers, worden niet als extern beschouwd in het uitvoerbeveiligingsscenario.

Over de luchtverbindingstypen (OTA) worden standaard alle blokken vermeld, maar kunnen indien nodig expliciet worden vermeld. De gesteunde verbindingen OTA omvatten: Miracast, AirPlay, DLNA en WIDI.

**Op resolutie gebaseerde outputbescherming: (Beschikbaar vanaf versie 5.3.) ** Dit biedt uitvoerbescherming op basis van het verticale aantal pixels van de inhoud, waardoor een verscheidenheid aan beveiligingsvereisten kan worden opgegeven op basis van verticale aantallen pixels.

De volgende opties/niveaus van handhaving zijn beschikbaar:

| Option | Ondersteund in analoge apparaten | Ondersteund in digitale apparaten |
|---|---|---|
| **Vereist** — Analoge kopieerbeveiliging (ACP) of Copy Generation Management System — Analog (CGMS-A)-uitvoerbeveiliging moet zijn ingeschakeld om inhoud af te spelen op een extern apparaat. Primetime DRM-clients moeten uitvoerbeveiliging met ACS of CGMS-A inschakelen. Op apparaten die beide ondersteunen, proberen de Primetime DRM 3.0-clients beide in te schakelen. U moet echter slechts één speler inschakelen om de inhoud af te spelen. | JA | JA |
| **ACS vereist** — ACS-uitvoerbescherming is vereist. Afspelen is niet toegestaan op CGMS-A. Primetime DRM 2.0-clients bieden geen ondersteuning voor deze optie. Als deze optie is ingesteld, gedraagt een Primetime DRM 2.0-client zich alsof de optie &quot;Geen afspelen&quot; is opgegeven. | JA | - |
| **Gebruik indien beschikbaar** — Poging om ACS- en CGMS-A-uitvoerbeveiliging in te schakelen, indien beschikbaar, en afspelen toe te staan als deze niet beschikbaar is. Primetime DRM 3.0-clients proberen, indien mogelijk, zowel ACS als CGMS-A in te schakelen. Primetime DRM 2.0-clients proberen alleen ACS of CGMS-A in te schakelen. De Primetime DRM-client probeert bijvoorbeeld ACS of CGMS-A in te schakelen. Als de poging slaagt, kan de andere optie niet worden toegelaten. Als de poging mislukt, wordt een tweede poging gedaan om de andere optie in te schakelen. Zelfs als beide pogingen mislukken, wordt de inhoud toch afgespeeld. | JA | JA |
| **Gebruik ACS indien beschikbaar** — Poging om ACS-uitvoerbescherming in te schakelen indien beschikbaar, maar afspelen toestaan als deze niet beschikbaar is. De bescherming is niet beschikbaar op CGMS-A. Primetime DRM 2.0-clients bieden geen ondersteuning voor deze optie. Als deze optie is ingesteld, gedraagt een Primetime DRM 2.0-client zich alsof de optie &quot;Geen beveiliging&quot; is opgegeven. | JA | - |
| **Gebruik CGMS-A als dit beschikbaar is **— probeer CGMS-A-uitvoerbeveiliging in te schakelen als deze beschikbaar is, maar sta afspelen toe als deze niet beschikbaar is. De bescherming is niet beschikbaar op ACS. Primetime DRM 2.0-clients bieden geen ondersteuning voor deze optie. Als deze optie is ingesteld, gedraagt een Primetime DRM 2.0-client zich alsof de optie &quot;Geen beveiliging&quot; is opgegeven. | JA | - |
| **Geen bescherming** — Voor analoge en digitale uitvoer wordt geen uitvoerbescherming ingeschakeld. | JA | JA |
| **Geen afspelen** — Afspelen op een extern apparaat niet toestaan voor analoge en digitale uitvoer. | JA | JA |

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>Hoewel deze regels op alle platforms consistent worden toegepast, kunt u uitvoerbeveiliging alleen veilig inschakelen op Windows-platforms. Op andere platforms, zoals Macintosh en Linux, zijn er geen ondersteunende besturingssysteemfuncties beschikbaar voor toepassingen van derden.

Voorbeeld van gebruik: Sommige inhoud dwingt uitvoerbeveiligingselementen af en daarom kan de inhoudsdistributeur het beschermingsniveau instellen. Als &quot;Vereist&quot; is opgegeven en wordt geprobeerd de inhoud af te spelen op een Macintosh, wordt de inhoud niet afgespeeld op externe apparaten. De inhoud kan op interne monitoren worden afgespeeld.

Als &quot;Vereist&quot; is opgegeven en in Linux wordt geprobeerd de inhoud af te spelen, wordt de inhoud op geen enkel apparaat afgespeeld, omdat er geen onderscheid kan worden gemaakt tussen interne en externe apparaten.

Als u &quot;Gebruik indien beschikbaar&quot; opgeeft, wordt de uitvoerbeveiliging waar mogelijk ingeschakeld. Op Windows-systemen die het Certified Output Protection Protocol (COPP) ondersteunen, wordt de inhoud met uitvoerbeveiliging doorgegeven aan een extern scherm. Dit voorbeeld wordt soms ook wel *`selectable output control`* genoemd.
