---
title: Domeinregistratie apparaatgroep
description: Domeinregistratie apparaatgroep
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---


# Domeinregistratie{#device-group-domain-registration} van apparaatgroep

Als alternatief voor het binden van een vergunning aan een specifiek apparaat, steunen Adobe Access 3.0 en hoger bindende vergunningen aan een apparatendomein. De veelvoudige apparaten kunnen zich bij een domein aansluiten en domeintokens ontvangen. Nadat een apparaat in het domein een vergunning verwerft, kan de vergunning worden overgebracht naar om het even welk ander apparaat in het domein, en die apparaten kunnen de inhoud spelen zonder een vergunning direct van de vergunningsserver te verwerven.

Om de domein-gebonden vergunningen te steunen, moet het beleid de domeinserver specificeren waarmee de cliënt moet registreren. Het beleid zal ook de authentificatievereisten voor de domeinserver (of anonieme toegang wordt toegestaan of of de server gebruikersbenaming/wachtwoord of douaneauthentificatie vereist) specificeren.

Domeinregistratie en domeingebonden licenties worden ondersteund door Adobe Access-clients versie 3.0 en hoger. Als een oudere cliënt of een Adobe Access 3.0 cliënt in Flash Player om een vergunning voor inhoud verzoekt die domeinregistratie steunt, kan de vergunningsserver een vergunning uitgeven gebruikend een alternatief beleid dat band aan een specifiek apparaat steunt.
