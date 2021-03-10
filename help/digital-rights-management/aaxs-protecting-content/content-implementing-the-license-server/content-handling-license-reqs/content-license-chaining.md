---
title: Licentieketens
description: Licentieketens
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---


# Licentieketting{#license-chaining}

Als het beleid dat wordt gebruikt om de licentie te genereren licentietekeningen ondersteunt, moet de server beslissen of een Leaf-licentie, een Root-licentie of beide moeten worden uitgegeven. Om te bepalen welk type van vergunning die een beleid ketent steunt, gebruik `Policy.getLicenseChainType()`, of vraag `Policy.getRootLicenseId()` om te bepalen als het beleid een wortelvergunning heeft. Met Adobe Access 2.0-licentieketting geeft de server doorgaans een bladlicentie uit wanneer de gebruiker voor het eerst een licentie voor een bepaalde computer en daarna een hoofdlicentie aanvraagt. Om te bepalen als de machine reeds een bladvergunning voor het gespecificeerde beleid heeft, roep `LicenseRequestMessage.clientHasLeafForPolicy()`.
