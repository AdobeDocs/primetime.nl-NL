---
title: Kritiek op beleid
description: Kritiek op beleid
copied-description: true
exl-id: 6c6971fe-0c0a-4998-917c-aebbf1c4a9df
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---

# Kritiek op beleid{#policy-criticality}

Als de nieuwe gebruiksregels in het beleid worden gebruikt en dit beleid in inhoud wordt gebruikt die voor oudere vergunningsservers (die de nieuwe gebruiksregels niet begrijpen) wordt verpakt, kunt u specificeren hoe de oudere vergunningsservers zich zouden moeten gedragen. Door gebrek, is de beleidskritiek &quot;waar&quot;, betekenend dat de vergunningsserver alle delen van het beleid moet begrijpen om een vergunning te produceren gebruikend het beleid. Als de beleidskritiek aan &quot;vals&quot;wordt geplaatst, kan een oudere vergunningsserver delen van het beleid negeren het niet begrijpt, en de vergunningen die door de server worden geproduceerd zullen niet de nieuwe gebruiksregels bevatten.

De servers van de Toegang van Adobe die versie 2.0.2 van SDK en hoger gebruiken zullen het plaatsen van de beleidsKritiek respecteren.
