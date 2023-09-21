---
description: Als u wilt voorkomen dat gebruikers back-ups maken van bestanden en deze herstellen om de deregistratie van domeinen te omzeilen, moet u een aantal benaderingen voor domeinbeheer implementeren.
title: Domeinen beheren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Domeinen beheren {#managing-domains}

Als u wilt voorkomen dat gebruikers back-ups maken van bestanden en deze herstellen om de deregistratie van domeinen te omzeilen, moet u een aantal benaderingen voor domeinbeheer implementeren.

Hier volgen enkele methoden voor domeinbeheer:

* Beperk de hoeveelheid tijd de domeingeloofsbrieven geldig zijn.

  Clients moeten contact opnemen met de domeinserver om domeinreferenties opnieuw te verkrijgen wanneer de referenties verlopen. Op dat ogenblik, kan de Server van het Domein verifiëren dat de machine nog wordt gemachtigd om een lid van het domein te zijn.
* Beweeg de cursor over de domeintoetsen wanneer een gebruiker de toepassing deregiseert.

  De licentieserver mag alleen licenties uitgeven voor clients die over de nieuwste domeinsleutel beschikken. Deze benadering veronderstelt dat de Server van de Vergunning met de Server van het Domein kan coördineren om te weten welke sleutel de recentste is. Wanneer u de domeinsleutels overschrijft, genereert u een nieuw sleutelpaar voor het domein. Wanneer u de toetsen voor een domein overschrijft, verhoogt u de sleutelversie in `generateDomainCredential`.
* Als de domeinserver hetzelfde is als de licentieserver, kan de server de terugdraaiteller gebruiken om een back-up en herstel te detecteren.

  Zie voor meer informatie [Adobe Primetime DRM-aanvragen verwerken](../../protecting-content/implementing-the-license-server/processing-drm-requests.md).
