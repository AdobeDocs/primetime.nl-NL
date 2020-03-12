---
description: Gebruik het bibliotheekbestand Browser van TVSDK van Browser in uw app om een speler te maken die compatibel is met Browser.
seo-description: Gebruik het bibliotheekbestand Browser van TVSDK van Browser in uw app om een speler te maken die compatibel is met Browser.
seo-title: Creeer een Browser-Compatibele speler zonder UI-Kader
title: Creeer een Browser-Compatibele speler zonder UI-Kader
uuid: c4315bc8-c75d-4dd9-8680-946c1197be1e
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Creeer een Browser-Compatibele speler zonder UI-Kader{#create-a-browserify-compatible-player-without-the-ui-framework}

Gebruik het bibliotheekbestand Browser van TVSDK van Browser in uw app om een speler te maken die compatibel is met Browser.

Het onderwerp [](../../../browser-tvsdk-2.4/getting-started/c-psdk-browser-tvsdk-2.4-create-a-basic-player/t-psdk-browser-tvsdk-2.4-create-basic-player-tvsdk.md) bevat een lijst met Browser-TVSDK-bibliotheken die u normaal gesproken gebruikt wanneer u een eenvoudige videospeler maakt. Hiervoor voegt u eenvoudig `script` tags toe met `src` kenmerken die naar de bibliotheken verwijzen.

Het proces is iets anders voor het maken van een speler die compatibel is met Browser. Hiervoor gebruikt u de `require` opdracht om het [!DNL AdobePSDK.module.js] bestand (opgegeven door de Browser-TVSDK) op te nemen in uw app. Dit bestand bundelt de basisbibliotheekbestanden van de speler in de juiste volgorde van afhankelijkheid en retourneert de `AdobePSDK` naamruimte die u gebruikt om functies voor de speler te implementeren.

Browser TVSDK biedt de volgende voorbeeldtoepassing Browser en bouwt bestanden in het releasepakket:

* [!DNL [...]/samples/browserify/reference/build/Gruntfile.js]
* [!DNL [...]/samples/browserify/reference/build/package.json]
* [!DNL [...]/samples/browserify/reference/examples/sample.html]
* [!DNL [...]/samples/browserify/reference/examples/sample.js]

Een videospeler maken die compatibel is met Browser:

1. Vereisen het Browser-Compatibele bibliotheekdossier dat `AdobePSDK` namespace terugkeert:

   ```
   var AdobePSDK = require('./AdobePSDK.module.js'); 
   var player; 
   function Load () { 
       player = new AdobePSDK.MediaPlayer(); 
   […]
   ```

1. Maak de speler zoals beschreven in [](../../../browser-tvsdk-2.4/getting-started/c-psdk-browser-tvsdk-2.4-create-a-basic-player/t-psdk-browser-tvsdk-2.4-create-basic-player-tvsdk.md).

   Stap 1 in deze taak vervangt de stap in de basisspelerinstructies waarin u de afzonderlijke basisspelerbibliotheken in uw toepassingsbestand plaatst.
U kunt nu een bundel maken van uw toepassingsbestanden met behulp van Bladeren.
