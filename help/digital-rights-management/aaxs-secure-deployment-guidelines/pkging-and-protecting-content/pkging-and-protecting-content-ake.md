---
title: Asymmetrische sleutelversleuteling
description: Asymmetrische sleutelversleuteling
copied-description: true
exl-id: 5962176e-07ec-4606-b1d8-39946ba59127
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---

# Asymmetrische sleutelversleuteling{#asymmetric-key-encryption}

Bij asymmetrische sleutelversleuteling (ook wel versleuteling met een openbare sleutel genoemd) worden sleutelparen gebruikt. Eén sleutel wordt gebruikt voor versleuteling. de andere voor ontsleuteling. De decryptiesleutel wordt geheim gehouden en wordt bedoeld als a *persoonlijke sleutel*. De coderingssleutel, de *openbare sleutel*, beschikbaar wordt gesteld aan iedereen die gemachtigd is om inhoud te versleutelen. Iedereen met toegang tot de openbare sleutel kan inhoud coderen, maar alleen iemand met toegang tot de persoonlijke sleutel kan de inhoud decoderen. De persoonlijke sleutel kan niet opnieuw worden opgebouwd op basis van de openbare sleutel.

Bij het verpakken van inhoud wordt de openbare sleutel van de Server van de Vergunning gebruikt om de sleutel van de inhoudsencryptie (CEK) in de meta-gegevens te coderen DRM. U moet ervoor zorgen dat alleen de licentieserver toegang heeft tot de persoonlijke sleutel van de licentieserver. als iemand anders over de sleutel beschikt, kan hij de inhoud decoderen en bekijken.

***Let op:**Zorg ervoor dat u het certificaat van de Server van de Vergunning (dat de openbare sleutel bevat) van een vertrouwde bron verkrijgt zodat u zeker kunt zijn het de sleutel van de Server van de Vergunning, en niet een schurken openbare sleutel is. Als een aanvaller zijn openbare sleutel voor de sleutel van de Server van de Vergunning moest vervangen, zouden zij uw inhoud kunnen decrypteren.*

Voor meer informatie over verpakkingsinhoud raadpleegt u *De SDK van Adobe Access gebruiken voor het beschermen van inhoud*.
