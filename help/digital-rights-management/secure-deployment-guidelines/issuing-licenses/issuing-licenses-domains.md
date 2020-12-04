---
description: Als u wilt voorkomen dat gebruikers back-ups maken van bestanden en deze herstellen om de deregistratie van domeinen te omzeilen, moet u een aantal benaderingen voor domeinbeheer implementeren.
seo-description: Als u wilt voorkomen dat gebruikers back-ups maken van bestanden en deze herstellen om de deregistratie van domeinen te omzeilen, moet u een aantal benaderingen voor domeinbeheer implementeren.
seo-title: Domeinen beheren
title: Domeinen beheren
uuid: 30b73e38-d6ed-43c6-89ba-ae8616383779
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15
workflow-type: tm+mt
source-wordcount: '224'
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

