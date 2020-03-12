---
description: TVSDK voegt de alternatieve inhoud (advertenties) in de tijdlijn in die overeenkomt met de hoofdinhoud.
seo-description: TVSDK voegt de alternatieve inhoud (advertenties) in de tijdlijn in die overeenkomt met de hoofdinhoud.
seo-title: Ad-invoegfase
title: Ad-invoegfase
uuid: 4a8e9578-6e95-44c0-b045-ae3c20da75e9
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Ad-invoegfase{#ad-insertion-phase}

TVSDK voegt de alternatieve inhoud (advertenties) in de tijdlijn in die overeenkomt met de hoofdinhoud.

Wanneer de ad-resolving fase volledig is, heeft TVSDK een geordende lijst van ad middelen die in ad-einden worden gegroepeerd. Elk ad-einde wordt op de tijdlijn van de hoofdinhoud geplaatst met behulp van een beginwaarde die in milliseconden (ms) wordt uitgedrukt. Elke advertentie in een advertentie-einde heeft een eigenschap duration die ook wordt uitgedrukt in ms. De advertenties in een pauze zijn stuk voor stuk aan elkaar gekoppeld. Als gevolg hiervan is de duur van een ad-break gelijk aan de som van de tijdsduur van de afzonderlijke samenstellende advertenties.

Failover kan in deze fase optreden met conflicten die tijdens het invoegen op de tijdlijn kunnen optreden. Voor specifieke combinaties van beginwaarden/duurwaarden voor begintijd en eindtijd van advertentie kunnen ad-valesegmenten elkaar overlappen. De overlapping treedt op wanneer het laatste gedeelte van een advertentie-einde het begin van de eerste advertentie in de volgende advertentie-einde snijdt. In deze situaties verwijdert TVSDK het latere ad-invoegproces en gaat het ad-invoegproces verder met het volgende item in de lijst totdat alle ad-invoegingen zijn ingevoegd of verwijderd.

TVSDK geeft een waarschuwingsbericht over de fout weer en gaat door met de verwerking.
