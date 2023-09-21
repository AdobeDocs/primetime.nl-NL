---
description: TVSDK voegt de alternatieve inhoud (advertenties) in de tijdlijn in die overeenkomt met de hoofdinhoud.
title: Ad-invoegfase
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# Ad-invoegfase{#ad-insertion-phase}

TVSDK voegt de alternatieve inhoud (advertenties) in de tijdlijn in die overeenkomt met de hoofdinhoud.

Wanneer de ad-resolving fase volledig is, heeft TVSDK een geordende lijst van ad middelen die in ad-einden worden gegroepeerd. Elk ad-einde wordt op de tijdlijn van de hoofdinhoud geplaatst met behulp van een beginwaarde die in milliseconden (ms) wordt uitgedrukt. Elke advertentie in een advertentie-einde heeft een eigenschap duration die ook wordt uitgedrukt in ms. De advertenties in een pauze zijn stuk voor stuk aan elkaar gekoppeld. Als gevolg hiervan is de duur van een ad-break gelijk aan de som van de tijdsduur van de afzonderlijke samenstellende advertenties.

Failover kan in deze fase optreden met conflicten die tijdens het invoegen op de tijdlijn kunnen optreden. Voor specifieke combinaties van beginwaarden/duurwaarden voor begintijd en eindtijd van advertentie kunnen de segmenten elkaar overlappen. De overlapping treedt op wanneer het laatste gedeelte van een advertentie-einde het begin van de eerste advertentie in de volgende advertentie-einde snijdt. In deze situaties verwijdert TVSDK het latere ad-invoegproces en gaat het ad-invoegproces verder met het volgende item in de lijst totdat alle ad-invoegingen zijn ingevoegd of verwijderd.

TVSDK geeft een waarschuwingsbericht over de fout weer en gaat door met de verwerking.
