---
description: U kunt een Browser-Compatibele speler tot stand brengen gebruikend JS dossiers die door Browser TVSDK worden verstrekt.
title: Browsercompatibele speler
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 3%

---


# Overzicht {#browserify-compatible-player-overview}

U kunt een Browser-Compatibele speler tot stand brengen gebruikend JS dossiers die door Browser TVSDK worden verstrekt.

Browser TVSDK biedt twee JS-bestanden die compatibel zijn met Browser. Een is bedoeld voor gebruik met de AdobePSDK-module. Dit is voor het ontwikkelen van apps zonder het UI-Kader. andere is voor gebruik met de module UI-Kader; het keert PTP namespace terug u voor het schrijven apps gebruikend UI-Kader gebruikt.

Als u aan de slag wilt gaan met Browser, voert u de volgende instellingsopdrachten uit om [!DNL final.js]-bestanden (uw bundelbestand Bladeren) te maken in de directory&#39;s [!DNL example] onder [!DNL samples/browerify/reference] en [!DNL samples/browerify/ui-framework]:

1. Ga naar [!DNL samples/browserify/reference/build].
1. Voer de volgende opdrachten uit:

   1. [!DNL npm install]
   1. [!DNL node_modules/.bin/grunt]

1. Ga naar [!DNL samples/browserify/ui-framework/build].
1. Voer dezelfde opdrachten uit als in Stap 2.

Als u deze setup hebt uitgevoerd, kunt u verdergaan met het maken van TVSDK-apps die compatibel zijn met browserify, op basis van de voorbeelden die bij de TVSDK worden geleverd.
