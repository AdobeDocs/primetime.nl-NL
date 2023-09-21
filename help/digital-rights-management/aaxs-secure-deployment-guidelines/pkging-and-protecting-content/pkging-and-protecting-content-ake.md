---
title: Asymmetrische sleutelversleuteling
description: Asymmetrische sleutelversleuteling
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---

# Asymmetrische sleutelversleuteling{#asymmetric-key-encryption}

Bij asymmetrische sleutelversleuteling (ook wel versleuteling met een openbare sleutel genoemd) worden sleutelparen gebruikt. De ene sleutel wordt gebruikt voor versleuteling, de andere voor decodering. De decryptiesleutel wordt geheim gehouden en wordt bedoeld als a *persoonlijke sleutel*. De coderingssleutel, de *openbare sleutel*, beschikbaar wordt gesteld aan iedereen die gemachtigd is om inhoud te versleutelen. Iedereen met toegang tot de openbare sleutel kan inhoud coderen, maar alleen iemand met toegang tot de persoonlijke sleutel kan de inhoud decoderen. De persoonlijke sleutel kan niet opnieuw worden opgebouwd op basis van de openbare sleutel.

Bij het verpakken van inhoud wordt de openbare sleutel van de Server van de Vergunning gebruikt om de sleutel van de inhoudsencryptie (CEK) in de meta-gegevens te coderen DRM. U moet ervoor zorgen dat alleen de licentieserver toegang heeft tot de persoonlijke sleutel van de licentieserver. Als iemand anders over de sleutel beschikt, kan hij of zij de inhoud decoderen en bekijken.

***Let op:**Zorg ervoor dat u het certificaat van de Server van de Vergunning (dat de openbare sleutel bevat) van een vertrouwde bron verkrijgt zodat u zeker kunt zijn het de sleutel van de Server van de Vergunning, en niet een schurken openbare sleutel is. Als een aanvaller zijn openbare sleutel voor de sleutel van de Server van de Vergunning moest vervangen, zouden zij uw inhoud kunnen decrypteren.*

Zie voor meer informatie over verpakkingsinhoud *De Adobe Access SDK gebruiken voor het beveiligen van inhoud*.
