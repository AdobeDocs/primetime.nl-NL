---
title: Problemen oplossen en fouten opsporen
description: null
translation-type: tm+mt
source-git-commit: 242b5a2875ebc0e0020296ce9489dd54438b5ad0
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 0%

---


# {#troubleshooting-debugging} problemen oplossen en fouten opsporen

De Ad Insertion van Primetime biedt hulpmiddelen om kwesties te identificeren en te diagnostiseren die in alle fasen van videolevering, zoals CDN leveringsfouten, en creatieve fouten of de fouten van de cliëntconnectiviteit kunnen voorkomen.

Primetime Ad Insertion ondersteunt uitgebreide logboekregistratie via de [Bootstrap API-parameter](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md) `ptdebug=true` of `ptdebug=AdCall` naar de bootstrap-URL. Logboeken worden uitgevoerd naar zowel HTTP-antwoordheaders als naar de Primetime Ad Insertion-console. Deze parameter is alleen bedoeld voor gelokaliseerde tests, niet voor productiestromen. Voor meer informatie over berichttypes wanneer het verbose registreren wordt toegelaten, zie [ptdebug registrerengebeurtenissen in verbose registreren](verbose-logging.md#ptdebug-logging-events).

Primetime Ad Insertion verstrekt prestaties het zuiveren op alle verzoeken ook van X-ADBE-AI-X1 kopbal, die kan worden gebruikt om prestaties en toevoegingen op om het even welk bepaald verzoek te meten. Deze verzoekkopbal is beschikbaar ongeacht of verbose het registreren wordt toegelaten. Zie [Uitgebreide koppen voor meer informatie: X-ADBE-PTAI-X1](debugging-headers.md).
