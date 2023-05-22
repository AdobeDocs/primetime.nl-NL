---
title: Problemen oplossen en fouten opsporen
description: Problemen oplossen en fouten opsporen
copied-description: true
exl-id: 1fcacd29-627d-4536-a746-16ddcfc8bc34
source-git-commit: 3e63c187f12d1bff53370bbcde4d6a77f58f3b4f
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 0%

---

# Problemen oplossen en fouten opsporen {#troubleshooting-debugging}

De Ad Insertion van Primetime biedt hulpmiddelen om kwesties te identificeren en te diagnostiseren die in alle fasen van videolevering, zoals CDN leveringsfouten, en creatieve fouten of de fouten van de cliëntconnectiviteit kunnen voorkomen.

Primetime Ad Insertion ondersteunt uitgebreide logboekregistratie via de [Bootstrap API-parameter](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md) `ptdebug=true` of `ptdebug=AdCall` naar de laarzentrekker-URL. Logboeken worden uitgevoerd naar zowel HTTP-antwoordheaders als naar de Primetime Ad Insertion-console. Deze parameter is alleen bedoeld voor gelokaliseerde tests, niet voor productiestromen. Voor meer informatie over berichttypes wanneer het verbose registreren wordt toegelaten, zie [ptdebug-logboekgebeurtenissen in uitgebreide logboekregistratie](verbose-logging.md#ptdebug-logging-events).

Primetime Ad Insertion verstrekt prestaties het zuiveren op alle verzoeken ook van X-ADBE-AI-X1 kopbal, die kan worden gebruikt om prestaties en toevoegingen op om het even welk bepaald verzoek te meten. Deze verzoekkopbal is beschikbaar ongeacht of verbose het registreren wordt toegelaten. Zie voor meer informatie [Uitgebreide koppen: X-ADBE-PTAI-X1](debugging-headers.md).
