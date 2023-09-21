---
description: U kunt een Browser-Compatibele speler tot stand brengen gebruikend JS dossiers die door Browser TVSDK worden verstrekt.
title: Browsercompatibele speler
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---

# Overzicht {#browserify-compatible-player-overview}

U kunt een Browser-Compatibele speler tot stand brengen gebruikend JS dossiers die door Browser TVSDK worden verstrekt.

Browser TVSDK biedt twee JS-bestanden die compatibel zijn met Browser. De ene is bedoeld voor gebruik met de AdobePSDK-module; dit is voor het ontwikkelen van toepassingen zonder het UI-Framework. Andere is voor gebruik met de module UI-Kader; het keert PTP namespace terug u voor het schrijven van apps gebruikend UI-Kader gebruikt.

Om met Browser te beginnen, stel de volgende opstellingsbevelen in werking om te creëren [!DNL final.js] bestanden (uw Browserbundelbestand) in het dialoogvenster [!DNL example] directory&#39;s onder [!DNL samples/browerify/reference] en [!DNL samples/browerify/ui-framework]:

1. Navigeren naar [!DNL samples/browserify/reference/build].
1. Voer de volgende opdrachten uit:

   1. [!DNL npm install]
   1. [!DNL node_modules/.bin/grunt]

1. Navigeren naar [!DNL samples/browserify/ui-framework/build].
1. Voer dezelfde opdrachten uit als in Stap 2.

Als u deze setup hebt uitgevoerd, kunt u verdergaan met het maken van TVSDK-apps die compatibel zijn met browserify, op basis van de voorbeelden die bij de TVSDK worden geleverd.
