---
description: Met Multi CDN kunt u een of meer CDN-locaties instellen voor getranscodeerde advertenties.
title: Ondersteuning voor Multi CDN
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---


# Ondersteuning voor Multi CDN {#multi-cdn-support}

Met Multi CDN kunt u een of meer CDN-locaties instellen voor getranscodeerde advertenties.

Standaard worden alle getranscodeerde elementen gehost op de Akamai CDN die eigendom is van de Adobe. Nochtans, kunt u nul of meer extra plaatsen CDN van uw kiezen waar CRS het getranscodeerde element zal ontvangen. In dit geval, kunnen uw getranscodeerde activa en inhoud van zelfde CDN worden gediend.

Wanneer de manifestserver omhoog voor getranscodeerde verzoeken maakt, gebruikt het een laarzentrekker URL die een aantal vraagparameters bevat. Als u een multi-CDN-omgeving hebt ingesteld, moet de bootstrap-URL ook het volgende bevatten `ptcdn` parameter.De manifestserver gebruikt deze parameter om de server te identificeren CDN waarvan om de getranscodeerde versie van de advertentie te krijgen.

Ondersteuning voor meerdere CDN is ook beschikbaar voor de volgende Primetime-oplossingen:

1. TVSDK voor Android
1. TVSDK voor desktop HLS
1. TVSDK voor iOS

## CDN-ondersteuning inschakelen {#section_1BA344F2300B49F291865A7461EDFEAE}

CRS is standaard uitgeschakeld voor alle klanten

Neem contact op met de technische accountmanager van Adobe om uw CRS-account te configureren voor het gebruik van andere CDN&#39;s voor het hosten van de getranscodeerde advertentie-elementen. U moet de volgende informatie opgeven die door CRS nodig is om de getranscodeerde en elementen naar de CDN te uploaden

1. CDN-URL
1. Verificatiedetails
1. Output URL-indeling

Ook, zal uw Adobe technische rekeningsmanager u een bijnaam voor dit CDN verstrekken.U moet dit als waarde van overgaan `ptcdn` in de URL van de Bootstrap.

U kunt veelvoudige CDNs hebben die op het eind van CRS via de Steun van Adobe wordt gevormd. Nochtans, zou CDN die wordt gebruikt om te selecteren en activa die via de duidelijke server moeten worden vastgemaakt moeten zijn die als waarde van wordt overgegaan `ptcdn` in de URL van de Bootstrap.
