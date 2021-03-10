---
description: Een manier om licenties en beleidshandhaving te coördineren, is deze functies op te nemen in een machtigingsserver. Adobe verstrekt de SEES server van de verwijzingsrecht waarmee u kunt werken om uw eigen server te bouwen.
title: Referentieservervoorbeeld ExpressPlay Entitlement Server (SEES)
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---


# Referentieserver: Voorbeeld ExpressPlay Entitlement Server (SES) {#reference-server-sample-expressplay-entitlement-server-sees}

Een manier om licenties en beleidshandhaving te coördineren, is deze functies op te nemen in een machtigingsserver. Adobe verstrekt de SEES server van de verwijzingsrecht waarmee u kunt werken om uw eigen server te bouwen.

De verwijzingsserver SEES toont de ExpressPlay Dienst van de Entitlement aan, die twee diensten toont: elementaire op tijd gebaseerde machtiging en rechten voor apparaatbinding.

De SES is gebaseerd op twee ExpressPlay Fairplay-services:

1. Expressplaytoken-aanvraagservice
1. Service voor het ophalen van expressrecords

De URL-indeling voor het ExpressPlay Token-verzoek bestaat uit twee vormen: een voor productie en een voor de testomgeving:

**Productie**: <span></span>https://fp-gen.{prod_domain}/hms/fp/token

**Testen**: <span></span>https://fp-gen.test.expressplay.com/hms/fp/token

De URL-indeling voor het ophalen van ExpressPlay Record bestaat uit twee vormen: een voor productie en een voor de testomgeving:

**Productie**: <span></span>https://api.{prod_domain}/cmiapi/getrecord/

**Testen**: <span></span>https://api.test.expressplay.com/cmiapi/getrecord/
