---
seo-title: Certificaten implementeren
title: Certificaten implementeren
uuid: adf72b51-be0f-49ec-83f7-152a378b04e6
translation-type: tm+mt
source-git-commit: b4b50471ab0ba98329862322a61bf73aa9e471d5
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 0%

---


# Certificaten implementeren{#deploy-certificates}

Om te voorkomen dat het PFX-wachtwoord in duidelijke tekst beschikbaar is op de licentieserver, vereisen de Reference Implementation en Adobe Primetime DRM Server for Protected Streaming dat het wachtwoord wordt gecodeerd wanneer dit is opgegeven in het configuratiebestand. Zie *De Primetime DRM Reference Implementations* of *De Primetime DRM Server* gebruiken voor Beveiligde streaming voor instructies voor het uitvoeren van de hulpprogramma&#39;s voor schuiven. Elk van deze omvat zijn eigen scramble nut, en de gecodeerde wachtwoorden zijn niet onderling verwisselbaar tussen deze twee implementaties van de Server van de Vergunning.

Zie *De Primetime DRM Reference Implementations* of *De Primetime DRM-server gebruiken voor beveiligde streaming* als u de certificaten en het gescande wachtwoord op uw licentieserver wilt gebruiken.
