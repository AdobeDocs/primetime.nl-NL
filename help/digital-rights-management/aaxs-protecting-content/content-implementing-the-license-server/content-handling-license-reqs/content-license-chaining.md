---
title: Licentieketens
description: Licentieketens
copied-description: true
exl-id: 2f439e21-c748-45aa-a87c-36e70ee3722a
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---

# Licentieketens{#license-chaining}

Als het beleid dat wordt gebruikt om de licentie te genereren licentietekeningen ondersteunt, moet de server beslissen of een Leaf-licentie, een Root-licentie of beide moeten worden uitgegeven. Om te bepalen welk type vergunning die een beleid ketent steunt, gebruik `Policy.getLicenseChainType()`, of bel `Policy.getRootLicenseId()` om te bepalen of het beleid een wortelvergunning heeft. Met Adobe Access 2.0-licentieketting geeft de server doorgaans een bladlicentie uit wanneer de gebruiker voor het eerst een licentie voor een bepaalde computer en daarna een hoofdlicentie aanvraagt. Als u wilt bepalen of de computer al een bladlicentie voor het opgegeven beleid heeft, roept u `LicenseRequestMessage.clientHasLeafForPolicy()`.
