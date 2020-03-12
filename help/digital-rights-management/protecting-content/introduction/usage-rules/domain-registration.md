---
seo-title: Domeinregistratie apparaatgroep
title: Domeinregistratie apparaatgroep
uuid: 221bf6c3-0568-443d-b761-64715a57ada6
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Domeinregistratie apparaatgroep{#device-group-domain-registration}

Als alternatief voor het binden van een licentie aan een specifiek apparaat, biedt Primetime DRM 3.0 of hoger ondersteuning voor het binden van licenties aan een apparaatdomein.

De veelvoudige apparaten kunnen zich bij een domein aansluiten en domeintokens ontvangen. Nadat een apparaat in het domein een vergunning verwerft, kan de vergunning worden overgebracht naar om het even welk ander apparaat in het domein, en die apparaten kunnen de inhoud spelen zonder een vergunning direct van de vergunningsserver te verwerven.

Als u om het even welke domein-gebonden vergunningen wilt steunen, dan moet het beleid Primetime DRM de domeinserver specificeren waarmee de cliënt moet registreren. Het Primetime DRM beleid moet de authentificatievereisten voor de domeinserver ook specificeren of anonieme toegang wordt toegelaten of of de server gebruikersbenaming/wachtwoord of douaneauthentificatie vereist.

Domeinregistratie en domeingebonden licenties worden ondersteund door Primetime DRM-clients versie 3.0 of hoger. Als een oudere client of een Adobe Primetime 3.0-client in Flash Player een licentie aanvraagt voor inhoud die domeinregistratie ondersteunt, kan de licentieserver een licentie uitgeven die een alternatief Primetime DRM-beleid gebruikt ter ondersteuning van binding aan een specifiek apparaat.
