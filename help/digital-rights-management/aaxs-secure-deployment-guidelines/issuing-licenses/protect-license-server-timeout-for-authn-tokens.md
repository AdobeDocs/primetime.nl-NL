---
title: Time-out voor verificatietokens
description: Time-out voor verificatietokens
copied-description: true
exl-id: ee9c5b2c-6a79-499c-bd60-718e33bc3a9b
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---

# Time-out voor verificatietokens{#timeout-for-authentication-tokens}

Alle authentificatietokens die door de Toegang SDK van de Adobe worden geproduceerd hebben een onderbrekingsinterval om toepassingsveiligheid te beschermen. De vervaldatum voor het authentificatietoken wordt gespecificeerd gebruik Adobe Access SDK wanneer het behandelen van een authentificatieverzoek. Zodra de vervaldatum is overgegaan, is het authentificatietoken niet meer geldig en de gebruiker moet opnieuw voor authentiek verklaren met de vergunningsserver.

Om meer over authentificatieverzoeken te leren, zie AuthenticationHandler in *Referentie voor Adobe Access API*.
