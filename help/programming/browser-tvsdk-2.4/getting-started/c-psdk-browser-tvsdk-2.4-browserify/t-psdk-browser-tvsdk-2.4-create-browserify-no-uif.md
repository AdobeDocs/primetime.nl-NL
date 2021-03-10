---
description: Gebruik het bibliotheekbestand Browser van TVSDK van Browser in uw app om een speler te maken die compatibel is met Browser.
title: Creeer een Browser-Compatibele speler zonder UI-Kader
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---


# Creeer een Browser-Compatibele speler zonder UI-Kader{#create-a-browserify-compatible-player-without-the-ui-framework}

Gebruik het bibliotheekbestand Browser van TVSDK van Browser in uw app om een speler te maken die compatibel is met Browser.

Het onderwerp [](../../../browser-tvsdk-2.4/getting-started/c-psdk-browser-tvsdk-2.4-create-a-basic-player/t-psdk-browser-tvsdk-2.4-create-basic-player-tvsdk.md) maakt een lijst van de Browser bibliotheken van TVSDK die u normaal omvat wanneer u een basisvideospeler creeert. Hiervoor voegt u `script`-tags toe met `src`-kenmerken die naar de bibliotheken verwijzen.

Het proces is iets anders voor het maken van een speler die compatibel is met Browser. Hiervoor gebruikt u de opdracht `require` om het bestand [!DNL AdobePSDK.module.js] (opgegeven door de TVSDK van de browser) op te nemen in uw app. Dit bestand bundelt de basisbibliotheekbestanden van de speler in de juiste volgorde van afhankelijkheid en retourneert de naamruimte `AdobePSDK` die u gebruikt om functies voor uw speler te implementeren.

Browser TVSDK biedt de volgende voorbeeldtoepassing Browser en bouwt bestanden in het releasepakket:

* [!DNL [..]/samples/browserify/reference/build/Gruntfile.js]
* [!DNL [..]/samples/browserify/reference/build/package.json]
* [!DNL [..]/samples/browserify/reference/examples/sample.html]
* [!DNL [..]/samples/browserify/reference/examples/sample.js]

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
