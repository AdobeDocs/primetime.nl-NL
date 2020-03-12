---
seo-title: Licentieketens
title: Licentieketens
uuid: dcc12663-ef9e-4c73-b837-66fcec39358b
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Licentieketens{#license-chaining}

Als het beleid dat wordt gebruikt om de licentie te genereren licentietekeningen ondersteunt, moet de server beslissen of een Leaf-licentie, een Root-licentie of beide moeten worden uitgegeven. Om te bepalen welk type van vergunning die een beleid ketent steunt, gebruik `Policy.getLicenseChainType()`, of vraag `Policy.getRootLicenseId()` om te bepalen als het beleid een wortelvergunning heeft. Met een certificaatketen voor Adobe Access 2.0 geeft de server doorgaans een bladlicentie uit wanneer de gebruiker voor het eerst een licentie voor een bepaalde computer en daarna een hoofdlicentie aanvraagt. Om te bepalen als de machine reeds een bladvergunning voor het gespecificeerde beleid heeft, roep `LicenseRequestMessage.clientHasLeafForPolicy()`.
