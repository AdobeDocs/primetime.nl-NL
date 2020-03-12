---
description: Met Multi CDN kunt u een of meer CDN-locaties instellen voor getranscodeerde advertenties.
seo-description: Met Multi CDN kunt u een of meer CDN-locaties instellen voor getranscodeerde advertenties.
seo-title: Ondersteuning voor Multi CDN
title: Ondersteuning voor Multi CDN
uuid: 2b6d71f0-61c8-486b-a35a-f7ef3a9519d2
translation-type: tm+mt
source-git-commit: 6863b63c7fa0068c3c5060fb946515c6cc5e3bff

---


# Ondersteuning voor Multi CDN {#multi-cdn-support}

Met Multi CDN kunt u een of meer CDN-locaties instellen voor getranscodeerde advertenties.

Standaard worden alle getranscodeerde elementen gehost op de Akamai CDN die eigendom is van Adobe. Nochtans, kunt u nul of meer extra plaatsen CDN van uw kiezen waar CRS het getranscodeerde element zal ontvangen. In dit geval, kunnen uw getranscodeerde activa en inhoud van zelfde CDN worden gediend.

Wanneer de manifestserver omhoog voor getranscodeerde verzoeken maakt, gebruikt het een laarzentrekker URL die een aantal vraagparameters bevat. Als u opstelling een multi-CDN milieu hebt, zal bootstrap URL ook de `ptcdn` parameter moeten bevatten.De manifestserver gebruikt deze parameter om de server te identificeren CDN waarvan om de getranscodeerde versie van de advertentie te krijgen.

Ondersteuning voor meerdere CDN is ook beschikbaar voor de volgende Primetime-oplossingen:

1. TVSDK voor Android
1. TVSDK voor desktop HLS
1. TVSDK voor iOS

## CDN-ondersteuning inschakelen {#section_1BA344F2300B49F291865A7461EDFEAE}

CRS is standaard uitgeschakeld voor alle klanten

Neem contact op met uw technische accountmanager van Adobe om uw CRS-account te configureren voor het gebruik van andere CDN&#39;s voor het hosten van de getranscodeerde advertentie-elementen. U moet de volgende informatie opgeven die CRS nodig heeft om de getranscodeerde en elementen naar de CDN te uploaden

1. CDN-URL
1. Verificatiedetails
1. Output URL-indeling

Ook geeft uw technische accountmanager van Adobe u een bijnaam voor deze CDN. U moet dit doorgeven als de waarde van de `ptcdn` parameter in de Bootstrap-URL.

U kunt meerdere CDN&#39;s op CRS-niveau configureren via de ondersteuning van Adobe. Nochtans, zou CDN die wordt gebruikt om te selecteren en activa die via de manifestserver moeten worden vastgemaakt moeten zijn die als waarde van de `ptcdn` parameter in Bootstrap URL wordt overgegaan.
