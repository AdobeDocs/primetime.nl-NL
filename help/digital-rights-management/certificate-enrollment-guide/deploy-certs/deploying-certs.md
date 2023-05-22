---
title: Certificaten implementeren
description: Certificaten implementeren
copied-description: true
exl-id: 649c4f24-f74e-4529-84a2-65bcd6d7677c
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 0%

---

# Certificaten implementeren{#deploy-certificates}

Om te voorkomen dat het PFX-wachtwoord in duidelijke tekst beschikbaar is op de licentieserver, vereisen de Reference Implementation en Adobe Primetime DRM Server for Protected Streaming dat het wachtwoord wordt gecodeerd wanneer dit is opgegeven in het configuratiebestand. Zie *Implementaties van de Primetime DRM-naslaggids gebruiken* of *De Primetime DRM-server gebruiken* voor Protected Streaming voor instructies voor het uitvoeren van de hulpprogramma&#39;s voor schuiven. Elk van deze omvat zijn eigen scramble nut, en de gecodeerde wachtwoorden zijn niet onderling verwisselbaar tussen deze twee implementaties van de Server van de Vergunning.

Als u de certificaten en het gescande wachtwoord wilt gebruiken op uw licentieserver, raadpleegt u *Implementaties van de Primetime DRM-naslaggids gebruiken* of *De Primetime DRM-server gebruiken voor beveiligde streaming*.
