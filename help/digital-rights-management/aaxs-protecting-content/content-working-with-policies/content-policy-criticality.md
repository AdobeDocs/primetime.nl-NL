---
title: Kritiek op beleid
description: Kritiek op beleid
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---

# Kritiek op beleid{#policy-criticality}

Als de nieuwe gebruiksregels in het beleid worden gebruikt en dit beleid in inhoud wordt gebruikt die voor oudere vergunningsservers (die de nieuwe gebruiksregels niet begrijpen) wordt verpakt, kunt u specificeren hoe de oudere vergunningsservers zich zouden moeten gedragen. Door gebrek, is de beleidskritiek &quot;waar&quot;, betekenend dat de vergunningsserver alle delen van het beleid moet begrijpen om een vergunning te produceren gebruikend het beleid. Als de beleidskritiek aan &quot;vals&quot;wordt geplaatst, kan een oudere vergunningsserver delen van het beleid negeren het niet begrijpt, en de vergunningen die door de server worden geproduceerd zullen niet de nieuwe gebruiksregels bevatten.

De servers van de Toegang van de Adobe die versie 2.0.2 van SDK en hoger gebruiken zullen het beleid kritieke plaatsen respecteren.
