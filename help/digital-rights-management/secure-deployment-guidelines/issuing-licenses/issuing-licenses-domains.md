---
description: Als u wilt voorkomen dat gebruikers back-ups maken van bestanden en deze herstellen om de deregistratie van domeinen te omzeilen, moet u een aantal benaderingen voor domeinbeheer implementeren.
title: Domeinen beheren
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---


# Domeinen {#managing-domains} beheren

Als u wilt voorkomen dat gebruikers back-ups maken van bestanden en deze herstellen om de deregistratie van domeinen te omzeilen, moet u een aantal benaderingen voor domeinbeheer implementeren.

Hier volgen enkele methoden voor domeinbeheer:

* Beperk de hoeveelheid tijd de domeingeloofsbrieven geldig zijn.

   Clients moeten contact opnemen met de domeinserver om domeinreferenties opnieuw te verkrijgen wanneer de referenties verlopen. Op dat ogenblik, kan de Server van het Domein verifiëren dat de machine nog wordt gemachtigd om een lid van het domein te zijn.
* Beweeg de cursor over de domeintoetsen wanneer een gebruiker de toepassing deregiseert.

   De licentieserver mag alleen licenties uitgeven voor clients die over de nieuwste domeinsleutel beschikken. Deze benadering veronderstelt dat de Server van de Vergunning met de Server van het Domein kan coördineren om te weten welke sleutel de recentste is. Wanneer u de domeinsleutels overschrijft, genereert u een nieuw sleutelpaar voor het domein. Wanneer u over de sleutels voor een domein rolt, verhogen de belangrijkste versie in `generateDomainCredential`.
* Als de domeinserver hetzelfde is als de licentieserver, kan de server de terugdraaiteller gebruiken om een back-up en herstel te detecteren.

   Zie [Adobe Primetime DRM-verzoeken verwerken](../../protecting-content/implementing-the-license-server/processing-drm-requests.md) voor meer informatie.

