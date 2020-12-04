---
seo-title: Overzicht van DRM-beleid gebruiken
title: Overzicht van DRM-beleid gebruiken
uuid: 32423448-013c-4183-bea8-e14b6690abdb
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---


# Overzicht {#working-with-drm-policies-overview}

Inhoudsproviders kunnen DRM-beleid toepassen op mediabestanden met de Primetime DRM SDK. Beheerders kunnen vervolgens DRM-beleid maken, weergeven en bijwerken met API&#39;s voor beleidsbeheer.

A *`DRM policy`* is een inzameling van informatie die veiligheidsmontages, authentificatievereisten, en gebruiksrechten omvat. Het beleid bepaalt hoe de gebruikers inhoud kunnen bekijken. Met DRM-beleid, -codering en -ondertekening kunnen leveranciers van inhoud hun inhoud blijven beheren, ongeacht hoe breed de inhoud wordt gedistribueerd.

Een DRM-beleid fungeert als een sjabloon die de licentieserver gebruikt wanneer deze een licentie genereert. Een client kan ook naar het DRM-beleid verwijzen voordat een licentie wordt aangevraagd, om te bepalen of de client de gebruiker moet vragen om verificatie voordat deze een licentieaanvraag aan de server afgeeft.

U kunt beveiligde inhoud leveren met Adobe Flash Media Server of een HTTP-server. Gebruikers kunnen beveiligde inhoud downloaden en afspelen in aangepaste spelers die zijn gemaakt met de Primetime DRM SDK.

Een DRM-beleid geeft een of meer rechten aan die aan de client zijn toegekend. Een DRM-beleid bevat doorgaans minimaal de *`Play Right`*. U kunt ook meerdere afspeelrechten opgeven, elk met verschillende beperkingen. Wanneer de client een licentie met meerdere Play Rights ontvangt, wordt de eerste licentie gebruikt die aan alle beperkingen voldoet. U kunt bijvoorbeeld verschillende uitvoerbeveiligingsinstellingen op verschillende platforms toepassen.

Zie `CreatePolicyWithOutputProtection.java` in de folder van de Hulpmiddelen [!DNL samples] van de Lijn van het Bevel van de Implementatie van de Verwijzing voor steekproefcode die dit voorbeeld illustreert.

U kunt de volgende taken uitvoeren met de Primetime DRM-API&#39;s voor beleidsbeheer:

* Beleid maken en bijwerken
* DRM-beleidsdetails weergeven
* Update-lijsten voor DRM-beleid beheren

Zie *Primetime DRM API Reference* voor meer informatie over de Java API.

Zie *Het gebruiken van de Implementaties van de Verwijzing Primetime DRM* gids voor informatie over de Manager van het Beleid Primetime DRM.
