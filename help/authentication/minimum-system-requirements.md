---
title: Minimale systeemvereisten
description: Minimale systeemvereisten
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---


# Minimale systeemvereisten {#minimum-system-requirements}

>[!NOTE]
>
>De inhoud op deze pagina wordt alleen ter informatie verstrekt. Voor het gebruik van deze API is een huidige licentie van Adobe vereist. Ongeautoriseerd gebruik is niet toegestaan.


## Overzicht {#overview}

Dit document bevat de huidige software- en hardwarevereisten voor de implementatie van Adobe Primetime Authentication-integratie op ondersteunde platforms. Alle ondersteunde web-/mobiele browsers en besturingssystemen die hieronder worden vermeld, krijgen volledige ondersteuning van het Adobe Primetime Authentication-team, dat gebonden is aan de overeengekomen SLA&#39;s.

Als Adobe Primetime Authentication-team stimuleren we het gebruik van de nieuwste stabiele versies van de browsers en besturingssystemen. We erkennen ook het bestaan van niet-compatibele/oudere platforms en browsers die momenteel in gebruik zijn. Deze verouderde apparaten werken nog steeds zonder problemen, maar ze zijn meer vatbaar voor fouten.

De eerste aanpak om problemen op deze verouderde platforms te verhelpen, moet bestaan uit het upgraden naar de nieuwste versies. Dit kan de OS-versie, de browserversie of de versie van de geïnstalleerde toepassing zijn.

Alle problemen die op deze platforms worden weergegeven, worden als best-inspanningsbasis opgelost door het Adobe Primetime-verificatieteam. 

Adobe Primetime moedigt aan om te overwegen om te upgraden naar de nieuwste versies om te profiteren van volledige Adobe support voor alle mogelijke problemen, naast prestatieverbeteringen, efficiëntie en beveiligingsverbeteringen. 


## Vereisten voor browser- en besturingssystemen {#browser-OS-system-requirements}


| Web/mobiele browser (†) | Ondersteunde versies |
|---|---|
| Google Chrome | **70** of hoger |
| Mozilla Firefox | **57** of hoger |
| Apple Safari | **14** of hoger |
| Microsoft Edge | **100** of hoger |

(†) Adobe adviseert tegen het gebruiken van privé of incognito wijze.

| Besturingssysteem | Ondersteunde versies |
|---|---|
| *Android* | **7,0** (Nougat) of hoger |
| *iOS* | **14** of hoger |
| *iPadOS* | **14** of hoger |
| *tvOS* | **14** of hoger |
| *Fire OS* | **5 (Android 5.1)** of hoger |
| *Mac OS* | **10,13** of hoger |
| *Microsoft Windows* | **10** of hoger |




>[!NOTE]
>
>Cookies van derden - Adobe Primetime-verificatierechten kunnen mislukken wanneer cookies van derden zijn uitgeschakeld.  Dit probleem kan alleen worden afgespeeld wanneer de browserinstellingen worden gewijzigd. Voor alle ondersteunde browsers moet Primetime-verificatie functioneren met de standaardinstellingen.\
 

## Apparaatvereisten voor implementaties zonder client (REST) {#general_clientless_reqs}

 
Om het even welk apparaat dat de Diensten van de Authentificatie van Adobe Primetime door cliëntless implementaties zal verbruiken **moet in staat zijn**:

* Geef een unieke hashed-apparaat-id op. Als het apparaat geen unieke hashed apparaat-id heeft, moet het apparaat een unieke id kunnen blijven gebruiken die door Adobe Primetime-verificatie wordt geleverd. Het apparaat moet de unieke id permanent in de lokale opslag kunnen behouden en de unieke id als de apparaat-id kunnen opgeven wanneer het apparaat wordt aangeroepen voor de Adobe Primetime-verificatie-API&#39;s.
* Digitale handtekeningen genereren met het HMAC-SHA1-algoritme
* Willekeurige HTTP-headers instellen
* RESTful-webservices gebruiken
* XML- en JSON-gegevensindelingen parseren
* Verkeer verzenden met HTTPS
* HTTP-foutcodes afhandelen
