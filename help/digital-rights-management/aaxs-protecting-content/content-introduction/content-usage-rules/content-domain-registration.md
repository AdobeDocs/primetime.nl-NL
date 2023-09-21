---
title: Domeinregistratie apparaatgroep
description: Domeinregistratie apparaatgroep
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# Domeinregistratie apparaatgroep{#device-group-domain-registration}

Als alternatief voor het binden van een vergunning aan een specifiek apparaat, steunt de Toegang 3.0 van de Adobe en hoger bindende vergunningen aan een apparatendomein. De veelvoudige apparaten kunnen zich bij een domein aansluiten en domeintokens ontvangen. Nadat een apparaat in het domein een vergunning verwerft, kan de vergunning worden overgebracht naar om het even welk ander apparaat in het domein, en die apparaten kunnen de inhoud spelen zonder een vergunning direct van de vergunningsserver te verwerven.

Om de domein-gebonden vergunningen te steunen, moet het beleid de domeinserver specificeren waarmee de cliënt moet registreren. Het beleid zal ook de authentificatievereisten voor de domeinserver (of anonieme toegang wordt toegestaan of of de server gebruikersbenaming/wachtwoord of douaneauthentificatie vereist) specificeren.

Domeinregistratie en domeingebonden licenties worden ondersteund door Adobe Access-clients versie 3.0 en hoger. Als een oudere cliënt of een cliënt van de Toegang 3.0 van de Adobe in Flash Player om een vergunning voor inhoud verzoekt die domeinregistratie steunt, kan de vergunningsserver een vergunning uitgeven gebruikend een alternatief beleid dat band aan een specifiek apparaat steunt.
