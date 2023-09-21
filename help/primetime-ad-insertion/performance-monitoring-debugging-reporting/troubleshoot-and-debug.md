---
title: Problemen oplossen en fouten opsporen
description: Problemen oplossen en fouten opsporen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 0%

---

# Problemen oplossen en fouten opsporen {#troubleshooting-debugging}

De Ad Insertion van Primetime biedt hulpmiddelen om kwesties te identificeren en te diagnostiseren die in alle fasen van videolevering, zoals CDN leveringsfouten, en creatieve fouten of de fouten van de cliëntconnectiviteit kunnen voorkomen.

Primetime Ad Insertion ondersteunt uitgebreide logboekregistratie via [Bootstrap API, parameter](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md) `ptdebug=true` of `ptdebug=AdCall` naar de laarzentrekker-URL. Logboeken worden uitgevoerd naar zowel HTTP-antwoordheaders als naar de Primetime Ad Insertion-console. Deze parameter is alleen bedoeld voor gelokaliseerde tests, niet voor productiestromen. Voor meer informatie over berichttypes wanneer het verbose registreren wordt toegelaten, zie [ptdebug-logboekgebeurtenissen in uitgebreide logboekregistratie](verbose-logging.md#ptdebug-logging-events).

Primetime Ad Insertion verstrekt prestaties het zuiveren op alle verzoeken ook van X-ADBE-AI-X1 kopbal, die kan worden gebruikt om prestaties en toevoegingen op om het even welk bepaald verzoek te meten. Deze verzoekkopbal is beschikbaar ongeacht of verbose het registreren wordt toegelaten. Zie voor meer informatie [Uitgebreide koppen: X-ADBE-PTAI-X1](debugging-headers.md).
