---
description: Een manier om licenties en beleidshandhaving te coördineren, is deze functies op te nemen in een machtigingsserver. Adobe verstrekt de SEES server van de verwijzingsrecht waarmee u kunt werken om uw eigen server te bouwen.
title: Referentieservervoorbeeld ExpressPlay Entitlement Server (SEES)
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# Referentieserver: Sample ExpressPlay Entitlement Server (SES) {#reference-server-sample-expressplay-entitlement-server-sees}

Een manier om licenties en beleidshandhaving te coördineren, is deze functies op te nemen in een machtigingsserver. Adobe verstrekt de SEES server van de verwijzingsrecht waarmee u kunt werken om uw eigen server te bouwen.

De referentieserver SEES demonstreert de ExpressPlay Entitlement Service en toont twee services: een basisrecht op basis van tijd en rechten voor apparaatbinding.

De SES is gebaseerd op twee ExpressPlay Fairplay-services:

1. Expressplaytoken-aanvraagservice
1. Service voor het ophalen van expressrecords

De URL-indeling voor het ExpressPlay Token-verzoek bestaat uit twee vormen: een voor productie en een voor de testomgeving:

**Productie**: ht<span></span>tps://fp-gen.{prod_domain}/hms/fp/token

**Testen**: ht<span></span>tps://fp-gen.test.expressplay.com/hms/fp/token

De URL-indeling voor het ophalen van ExpressPlay Record bestaat uit twee vormen: een voor productie en een voor de testomgeving:

**Productie**: ht<span></span>tps://api.{prod_domain}/cmiapi/getrecord/

**Testen**: ht<span></span>tps://api.test.expressplay.com/cmiapi/getrecord/
