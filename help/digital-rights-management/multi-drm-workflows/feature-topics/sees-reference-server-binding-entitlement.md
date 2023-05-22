---
description: De SEES verwijzingsserver toont u hoe te om de apparaat-bindende machtigingsdienst toe te laten gebruikend ExpressPlay.
title: Referentie-service Device-Binding Entitlement
exl-id: 91f9d406-f3f9-47d3-aa50-f47c4e81b9fc
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---

# Referentieservice: Machtiging voor apparaatbinding {#reference-service-device-binding-entitlement}

De SEES verwijzingsserver toont u hoe te om de apparaat-bindende machtigingsdienst toe te laten gebruikend ExpressPlay.

>[!NOTE]
>
>De apparaat-gebonden machtigingsdienst kan ook tijd-gebonden zijn of huurduur verstrekken.

Als u de opdracht `device_id` afspelen van een dummy M3U8-inhoud. U kunt dan een cookie insluiten in het ExpressPlay-token, een SPC genereren (die de `device_id`) en een `getToken` naar de ExpressPlay-server.

![](assets/fees-device-binding.png)

De reeks begint met het afspelen van een dummy M3U8. Er wordt een cookie verzonden naar de SES-server om de ExpressPlay-token-URL op te halen. Na het ontvangen van het koekjesgebonden symbolische URL ExpressPlay, moet de volgende stap SPC produceren en het verzenden naar de Server ExpressPlay. De ExpressPlay-server extraheert de `device_id` vanuit SPC, het cookie van de ExpressPlay token-URL en plaatst het cookie en `device_id` in het transactielogboek.

De klant dient een echte licentieaanvraag in bij SEES die dezelfde cookie verzendt. SEES gebruikt het cookie om de `device_id` van de ExpressPlay-server.

SEES vraagt om een token ExpressPlay dat zowel apparaat-gebonden als tijdgebonden is en retourneert dat token naar de client.

De client vraagt de licentie aan met het ExpressPlay-token.

De ExpressPlay-server vergelijkt de `device_id` in de SPC met de `device_id` in de ExpressPlay-token. De ExpressPlay-server geeft alleen een licentie uit als de twee `device_id` waarden komen overeen.
