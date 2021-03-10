---
title: Willekeurige getallen genereren
description: Willekeurige getallen genereren
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---


# Willekeurige getallen genereren{#generating-random-numbers}

Hardware random number generators kunnen op de servers van Linux worden gebruikt om ervoor te zorgen dat voldoende entropie wordt geproduceerd. Als de machine niet genoeg entropie kan produceren, zullen de verrichtingen van de Toegang van Adobe die een bron van willekeur vereisen blokkeren terwijl het wachten op gegevens van `/dev/random`.
