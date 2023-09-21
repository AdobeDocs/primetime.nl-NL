---
title: Time-out voor verificatietokens
description: Time-out voor verificatietokens
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---

# Time-out voor verificatietokens{#timeout-for-authentication-tokens}

Alle authentificatietokens die door de Toegang SDK van de Adobe worden geproduceerd hebben een onderbrekingsinterval om toepassingsveiligheid te beschermen. Het verlopen voor het authentificatietoken wordt gespecificeerd gebruik de Toegang SDK van de Adobe wanneer het behandelen van een authentificatieverzoek. Zodra de vervaldatum is overgegaan, is het authentificatietoken niet meer geldig en de gebruiker moet opnieuw voor authentiek verklaren met de vergunningsserver.

Meer over authentificatieverzoeken leren, zie AuthenticationHandler in *API-naslaggids voor Adobe*.
