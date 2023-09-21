---
description: U kunt HTML-overlays met StageVideo gebruiken om UI-elementen weer te geven in het videovlak van de weergavelijst van de Flash. Dit vlak bevindt zich boven het StageVideo-vlak, zodat StageVideo altijd achter de elementen van de weergavelijst van Flash wordt weergegeven.
title: StageVideo- en HTML-overlays
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# StageVideo- en HTML-overlays{#stagevideo-and-html-overlays}

U kunt HTML-overlays met StageVideo gebruiken om UI-elementen weer te geven in het videovlak van de weergavelijst van de Flash. Dit vlak bevindt zich boven het StageVideo-vlak, zodat StageVideo altijd achter de elementen van de weergavelijst van Flash wordt weergegeven.

HTML-overlays zijn UI-elementen die u in het weergavevlak van de Flash kunt weergeven op video die wordt gerenderd door `StageVideo` op zijn eigen vliegtuig. Vóór Flash 15 kon u geen HTML-overlays gebruiken wanneer hardwareversnelling niet beschikbaar was. Vanaf Flash 15 worden HTML-overlays weergegeven wanneer `StageVideo` gaat terug naar softwarerendering.

>[!IMPORTANT]
>
>Afhankelijk van de mogelijkheden van uw systeem, kunnen de prestaties tot een grotere of lagere graad verminderen wanneer u HTML overlays gebruikt.

Overweeg de volgende informatie:

* In Flash Player 15:

   * U kunt HTML-overlays gebruiken, ongeacht of hardwareversnelling beschikbaar is.
   * Als u HTML-bedekkingen wilt gebruiken, stelt u `wmode` tot `opaque`.

* In Flash Player 14:

   * Wanneer hardwareversnelling beschikbaar is, `StageVideo` bevindt zich onder het weergaveoverzicht van de Flash, zodat u HTML-overlays kunt gebruiken.
   * Wanneer hardwareversnelling niet beschikbaar is, wordt video weergegeven boven op alle andere elementen in de browser, waardoor het gebruik van HTML-overlays wordt voorkomen.

Hier volgen de minimale browservereisten voor het gebruik van HTML-overlays met `StageVideo`:

* Firefox versie 4 en hoger
* Safari versie 4 en hoger
* Internet Explorer:

   * Versie 9+ in Windows 7 en hoger
   * Versie 10+ onder Windows XP

* Chrome versie 26 en hoger

  >[!IMPORTANT]
  >
  >Chrome Pepper in Windows XP en Windows Vista wordt niet ondersteund.
