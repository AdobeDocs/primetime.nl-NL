---
title: Willekeurige getallen genereren
description: Willekeurige getallen genereren
copied-description: true
exl-id: 9a816570-753e-4b05-a6ea-2d4b20ffa3d4
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---

# Willekeurige getallen genereren{#generating-random-numbers}

Hardware random number generators kunnen op de servers van Linux worden gebruikt om ervoor te zorgen dat voldoende entropie wordt geproduceerd. Als de machine niet genoeg entropie kan produceren, zullen de verrichtingen van de Toegang van Adobe die een bron van willekeur vereisen blokkeren terwijl het wachten op gegevens van `/dev/random`.
