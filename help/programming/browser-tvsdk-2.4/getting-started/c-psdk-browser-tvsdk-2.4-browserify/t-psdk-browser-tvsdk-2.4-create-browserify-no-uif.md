---
description: Gebruik het bibliotheekbestand Browser van TVSDK van Browser in uw app om een speler te maken die compatibel is met Browser.
title: Creeer een Browser-Compatibele speler zonder UI-Kader
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Creeer een Browser-Compatibele speler zonder UI-Kader{#create-a-browserify-compatible-player-without-the-ui-framework}

Gebruik het bibliotheekbestand Browser van TVSDK van Browser in uw app om een speler te maken die compatibel is met Browser.

Het onderwerp [](../../../browser-tvsdk-2.4/getting-started/c-psdk-browser-tvsdk-2.4-create-a-basic-player/t-psdk-browser-tvsdk-2.4-create-basic-player-tvsdk.md) Hier wordt een lijst weergegeven met de set TVSDK-bibliotheken van de browser die u normaal gesproken gebruikt wanneer u een eenvoudige videospeler maakt. Hiervoor voegt u eenvoudig `script` tags met `src` kenmerken die naar de bibliotheken verwijzen.

Het proces is iets anders voor het maken van een speler die compatibel is met Browser. Hiervoor gebruikt u de opdracht `require` gebruiken om de opdracht [!DNL AdobePSDK.module.js] bestand (opgegeven door de Browser-TVSDK) in uw app. Dit bestand bundelt de basisbibliotheekbestanden van de speler in de juiste volgorde van afhankelijkheid en retourneert de `AdobePSDK` naamruimte die u gebruikt om functies voor uw speler te implementeren.

Browser TVSDK biedt de volgende voorbeeldtoepassing Browser en bouwt bestanden in het releasepakket:

* [!DNL [...]/samples/browserify/reference/build/Gruntfile.js]
* [!DNL [...]/samples/browserify/reference/build/package.json]
* [!DNL [...]/samples/browserify/reference/examples/sample.html]
* [!DNL [...]/samples/browserify/reference/examples/sample.js]

Een videospeler maken die compatibel is met Browser:

1. Vereisen Browser-compatibel bibliotheekdossier dat terugkeert `AdobePSDK` naamruimte:

   ```
   var AdobePSDK = require('./AdobePSDK.module.js'); 
   var player; 
   function Load () { 
       player = new AdobePSDK.MediaPlayer(); 
   […]
   ```

1. De speler maken zoals beschreven in [](../../../browser-tvsdk-2.4/getting-started/c-psdk-browser-tvsdk-2.4-create-a-basic-player/t-psdk-browser-tvsdk-2.4-create-basic-player-tvsdk.md).

   Stap 1 in deze taak vervangt de stap in de basisspelerinstructies waarin u de afzonderlijke basisspelerbibliotheken in uw app-bestand opneemt.
U kunt nu een bundel maken van uw toepassingsbestanden met behulp van Bladeren.
