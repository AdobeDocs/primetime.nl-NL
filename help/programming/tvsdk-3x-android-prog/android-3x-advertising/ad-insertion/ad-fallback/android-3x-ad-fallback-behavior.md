---
description: Wanneer Primetime en beslissingsoningencounters een (creatieve) VAST-advertentie die leeg is of een mediatype heeft dat ongeldig is voor HLS, evalueert het de fallback-advertenties om te bepalen wat er moet worden geretourneerd.
seo-description: Wanneer Primetime en beslissingsoningencounters een (creatieve) VAST-advertentie die leeg is of een mediatype heeft dat ongeldig is voor HLS, evalueert het de fallback-advertenties om te bepalen wat er moet worden geretourneerd.
seo-title: Extra fallback-gedrag voor VAST en VMAP
title: Extra fallback-gedrag voor VAST en VMAP
uuid: 612416b9-d070-42e2-b68b-74ba52023345
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Extra fallback-gedrag voor VAST en VMAP {#ad-fallback-behavior-for-vast-and-vmap}

Wanneer Primetime en beslissingsoningencounters een (creatieve) VAST-advertentie die leeg is of een mediatype heeft dat ongeldig is voor HLS, evalueert het de fallback-advertenties om te bepalen wat er moet worden geretourneerd.

<!--<a id="section_9F60AF00CE9645848EAAF8C06A9E426B"></a>-->

In TVSDK is het enige geldige mediatype `application/x-mpegURL` (M3U8).

Wanneer er stand-alone reserveadvertenties zijn, onderzoekt Primetime en beslissingsstop - binnen deze advertenties in de volgende orde en keert de eerste advertentie met een geldig media type terug:

1. Als het opnieuw verpakken is ingeschakeld, wordt het eerste exemplaar van een advertentie met een ongeldig mediatype behandeld als andere ongeldige mediatypen.

   Als het opnieuw verpakken mislukt, is dit proces van toepassing op andere exemplaren van de advertentie.
1. Als TVSDK geen geldige fallback-advertenties vindt, wordt de oorspronkelijke advertentie met het ongeldige mediatype geretourneerd.
1. Als een fallback-advertentie met een geldig MIME-type wordt geretourneerd in plaats van de oorspronkelijke advertentie, beëindigt Primetime en decisions foutcode 403 aan de VAST-fout-URL, indien beschikbaar.
1. Als een fallback-advertentie een omslag is en meerdere advertenties retourneert, worden alleen advertenties met het juiste mediatype geretourneerd.

>[!IMPORTANT]
>
>Dit gedrag is altijd ingeschakeld voor advertenties in VAST-wrappers. Voor VAST-advertenties inline in een VMAP is het gedrag standaard uitgeschakeld, maar uw toepassing kan dit gedrag wel inschakelen.