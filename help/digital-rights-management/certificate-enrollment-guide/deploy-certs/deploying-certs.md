---
title: Certificaten implementeren
description: Certificaten implementeren
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 0%

---


# Certificaten implementeren{#deploy-certificates}

Om te voorkomen dat het PFX-wachtwoord in duidelijke tekst beschikbaar is op de licentieserver, vereisen de Reference Implementation en Adobe Primetime DRM Server for Protected Streaming dat het wachtwoord wordt gecodeerd wanneer dit is opgegeven in het configuratiebestand. Zie *De Primetime DRM Reference Implementations* of *De Primetime DRM Server* gebruiken voor Beveiligde streaming voor instructies voor het uitvoeren van de hulpprogramma&#39;s voor schuiven. Elk van deze omvat zijn eigen scramble nut, en de gecodeerde wachtwoorden zijn niet onderling verwisselbaar tussen deze twee implementaties van de Server van de Vergunning.

Zie *De Primetime DRM Reference Implementations* of *De Primetime DRM-server gebruiken voor beveiligde streaming* als u de certificaten en het gescande wachtwoord op uw licentieserver wilt gebruiken.
