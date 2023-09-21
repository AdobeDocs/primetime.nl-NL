---
title: Willekeurige getallen genereren
description: Willekeurige getallen genereren
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---

# Willekeurige getallen genereren{#generating-random-numbers}

Hardware random number generators kunnen op de servers van Linux worden gebruikt om ervoor te zorgen dat voldoende entropie wordt geproduceerd. Als de machine niet genoeg entropie kan produceren, zullen de verrichtingen van de Toegang van de Adobe die een bron van willekeur vereisen blokkeren terwijl het wachten op gegevens van `/dev/random`.
