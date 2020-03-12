---
seo-title: Time-out voor verificatietokens
title: Time-out voor verificatietokens
uuid: 41b0fbf5-a567-4118-bec1-c05e6e0b6d1f
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Time-out voor verificatietokens{#timeout-for-authentication-tokens}

Alle verificatietokens die door de Adobe Access SDK worden gegenereerd, hebben een time-outinterval om de beveiliging van de toepassing te beschermen. De vervaldatum voor het verificatietoken wordt opgegeven met de Adobe Access SDK wanneer een verificatieaanvraag wordt afgehandeld. Zodra de vervaldatum is overgegaan, is het authentificatietoken niet meer geldig en de gebruiker moet opnieuw voor authentiek verklaren met de vergunningsserver.

Zie AuthenticationHandler in de *Adobe Access API-naslaggids* voor meer informatie over verificatieverzoeken.
