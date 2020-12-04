---
description: U kunt HTML-overlays met StageVideo gebruiken om UI-elementen weer te geven in het videovlak van de weergavelijst Flash. Dit vlak bevindt zich boven het StageVideo-vlak, zodat StageVideo altijd achter alle Flash-weergaveoverzichtelementen wordt weergegeven.
seo-description: U kunt HTML-overlays met StageVideo gebruiken om UI-elementen weer te geven in het videovlak van de weergavelijst Flash. Dit vlak bevindt zich boven het StageVideo-vlak, zodat StageVideo altijd achter alle Flash-weergaveoverzichtelementen wordt weergegeven.
seo-title: StageVideo- en HTML-overlays
title: StageVideo- en HTML-overlays
uuid: 84e862ab-4c35-47a2-9c4e-f792d3ef5363
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# StageVideo- en HTML-overlays{#stagevideo-and-html-overlays}

U kunt HTML-overlays met StageVideo gebruiken om UI-elementen weer te geven in het videovlak van de weergavelijst Flash. Dit vlak bevindt zich boven het StageVideo-vlak, zodat StageVideo altijd achter alle Flash-weergaveoverzichtelementen wordt weergegeven.

HTML-overlays zijn UI-elementen die u in het weergavevlak Flash kunt weergeven op video die wordt gerenderd door `StageVideo` op een eigen vlak. Vóór Flash 15 kon u geen HTML-overlays gebruiken wanneer hardwareversnelling niet beschikbaar was. Vanaf Flash 15 worden HTML-overlays weergegeven wanneer `StageVideo` terugvalt op softwarerendering.

>[!IMPORTANT]
>
>Afhankelijk van de mogelijkheden van uw systeem kunnen de prestaties in meer of mindere mate afnemen wanneer u HTML-overlays gebruikt.

Overweeg de volgende informatie:

* In Flash Player 15:

   * U kunt HTML-overlays gebruiken, ongeacht of hardwareversnelling beschikbaar is.
   * Als u HTML-overlays wilt gebruiken, stelt u `wmode` in op `opaque`.

* In Flash Player 14:

   * Als hardwareversnelling beschikbaar is, bevindt `StageVideo` zich onder de weergavelijst Flash, zodat u HTML-overlays kunt gebruiken.
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

