---
description: De SEES verwijzingsserver toont u hoe te om de apparaat-bindende machtigingsdienst toe te laten gebruikend ExpressPlay.
title: Referentie-service Device-Binding Entitlement
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---


# Referentieservice: Device-Binding Entitlement {#reference-service-device-binding-entitlement}

De SEES verwijzingsserver toont u hoe te om de apparaat-bindende machtigingsdienst toe te laten gebruikend ExpressPlay.

>[!NOTE]
>
>De apparaat-gebonden machtigingsdienst kan ook tijd-gebonden zijn of huurduur verstrekken.

Als u de `device_id`-informatie wilt opladen, kunt u een dummy M3U8-inhoud afspelen. Vervolgens kunt u een cookie insluiten in het ExpressPlay-token, een SPC genereren (die de `device_id` bevat) en een `getToken` naar de ExpressPlay-server verzenden.

![](assets/fees-device-binding.png)

De reeks begint met het afspelen van een dummy M3U8. Er wordt een cookie verzonden naar de SES-server om de ExpressPlay-token-URL op te halen. Na het ontvangen van het koekjesgebonden symbolische URL ExpressPlay, moet de volgende stap SPC produceren en het verzenden naar de Server ExpressPlay. De ExpressPlay-server extraheert de `device_id` uit SPC, het cookie van de ExpressPlay-token-URL, en plaatst het cookie en `device_id` in het transactielogboek.

De klant dient een echte licentieaanvraag in bij SEES die dezelfde cookie verzendt. SEES gebruikt het cookie om de `device_id` van de ExpressPlay-server op te halen.

SEES vraagt om een token ExpressPlay dat zowel apparaat-gebonden als tijdgebonden is en retourneert dat token naar de client.

De client vraagt de licentie aan met het ExpressPlay-token.

De ExpressPlay-server vergelijkt `device_id` in de SPC met `device_id` in het ExpressPlay-token. De ExpressPlay-server geeft alleen een licentie uit als de twee `device_id`-waarden overeenkomen.
