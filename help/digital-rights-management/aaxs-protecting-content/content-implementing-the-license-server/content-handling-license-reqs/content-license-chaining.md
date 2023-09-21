---
title: Licentieketens
description: Licentieketens
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---

# Licentieketens{#license-chaining}

Als het beleid dat wordt gebruikt om de licentie te genereren licentietekeningen ondersteunt, moet de server beslissen of een Leaf-licentie, een Root-licentie of beide moeten worden uitgegeven. Om te bepalen welk type vergunning die een beleid ketent steunt, gebruik `Policy.getLicenseChainType()`, of bel `Policy.getRootLicenseId()` om te bepalen of het beleid een wortelvergunning heeft. Met Adobe Access 2.0-licentieketting geeft de server doorgaans een bladlicentie uit wanneer de gebruiker voor het eerst een licentie voor een bepaalde computer en daarna een hoofdlicentie aanvraagt. Als u wilt bepalen of de computer al een bladlicentie voor het opgegeven beleid heeft, roept u `LicenseRequestMessage.clientHasLeafForPolicy()`.
