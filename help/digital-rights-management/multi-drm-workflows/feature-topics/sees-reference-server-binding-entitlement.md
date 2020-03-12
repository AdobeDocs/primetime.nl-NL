---
description: De SEES verwijzingsserver toont u hoe te om de apparaat-bindende machtigingsdienst toe te laten gebruikend ExpressPlay.
seo-description: De SEES verwijzingsserver toont u hoe te om de apparaat-bindende machtigingsdienst toe te laten gebruikend ExpressPlay.
seo-title: Referentie-service Device-Binding Entitlement
title: Referentie-service Device-Binding Entitlement
uuid: 22ce2f8e-1758-4528-8caf-60d209839afe
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Referentieservice: Machtiging voor apparaatbinding {#reference-service-device-binding-entitlement}

De SEES verwijzingsserver toont u hoe te om de apparaat-bindende machtigingsdienst toe te laten gebruikend ExpressPlay.

>[!NOTE]
>
>De apparaat-gebonden machtigingsdienst kan ook tijd-gebonden zijn of huurduur verstrekken.

Als u de `device_id` informatie wilt opladen, kunt u een dummy M3U8-inhoud afspelen. U kunt dan een koekje in het token insluiten ExpressPlay, een SPC (dat bevat `device_id`) produceren, en een `getToken` naar de Server verzenden ExpressPlay.

![](assets/fees-device-binding.png)

De reeks begint met het afspelen van een dummy M3U8. Er wordt een cookie verzonden naar de SES-server om de ExpressPlay-token-URL op te halen. Na het ontvangen van het koekjesgebonden symbolische URL ExpressPlay, moet de volgende stap SPC produceren en het verzenden naar de Server ExpressPlay. De ExpressPlay-server extraheert het cookie `device_id` uit SPC, het cookie uit de ExpressPlay-token-URL, en plaatst het cookie en `device_id` in het transactielogboek.

De klant dient een echte licentieaanvraag in bij SEES die dezelfde cookie verzendt. SEES gebruikt het cookie om het bestand op te halen `device_id` van de ExpressPlay-server.

SEES vraagt om een token ExpressPlay dat zowel apparaat-gebonden als tijdgebonden is en retourneert dat token naar de client.

De client vraagt de licentie aan met het ExpressPlay-token.

De ExpressPlay-server vergelijkt het bestand `device_id` in de SPC met het `device_id` bestand in het ExpressPlay-token. De ExpressPlay-server geeft alleen een licentie uit als de twee `device_id` waarden overeenkomen.
