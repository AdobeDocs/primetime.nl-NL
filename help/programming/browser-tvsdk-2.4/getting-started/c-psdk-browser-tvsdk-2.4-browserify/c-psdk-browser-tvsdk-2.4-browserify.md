---
description: U kunt een Browser-Compatibele speler tot stand brengen gebruikend JS dossiers die door Browser TVSDK worden verstrekt.
title: Browsercompatibele speler
exl-id: 3e9751d8-7a7e-465b-8d46-d07e4ccb1f5b
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---

# Overzicht {#browserify-compatible-player-overview}

U kunt een Browser-Compatibele speler tot stand brengen gebruikend JS dossiers die door Browser TVSDK worden verstrekt.

Browser TVSDK biedt twee JS-bestanden die compatibel zijn met Browser. Een is bedoeld voor gebruik met de AdobePSDK-module. Dit is voor het ontwikkelen van apps zonder het UI-Kader. andere is voor gebruik met de module UI-Kader; het keert PTP namespace terug u voor het schrijven apps gebruikend UI-Kader gebruikt.

Om met Browser te beginnen, stel de volgende opstellingsbevelen in werking om te creëren [!DNL final.js] bestanden (uw Browserbundelbestand) in het dialoogvenster [!DNL example] mappen onder [!DNL samples/browerify/reference] en [!DNL samples/browerify/ui-framework]:

1. Navigeren naar [!DNL samples/browserify/reference/build].
1. Voer de volgende opdrachten uit:

   1. [!DNL npm install]
   1. [!DNL node_modules/.bin/grunt]

1. Navigeren naar [!DNL samples/browserify/ui-framework/build].
1. Voer dezelfde opdrachten uit als in Stap 2.

Als u deze setup hebt uitgevoerd, kunt u verdergaan met het maken van TVSDK-apps die compatibel zijn met browserify, op basis van de voorbeelden die bij de TVSDK worden geleverd.
