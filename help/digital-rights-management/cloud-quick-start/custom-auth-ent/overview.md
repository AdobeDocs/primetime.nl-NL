---
title: BES-overzicht
description: BES-overzicht
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---


# BES-overzicht{#bees-overview}

U kunt een Back-end Entitlement Service (BES) implementeren om aangepaste machtigingen voor uw Primetime Cloud DRM-bewerking te bieden.

Voor Primetime Cloud DRM wordt standaard anonieme licentielevering gebruikt. Dit betekent dat alle licentieaanvragen die naar Primetime Cloud DRM worden verzonden een geldige licentie retourneren zonder aanvullende verificatie-/autorisatiecontroles uit te voeren (tenzij u een beleidsbeperking hebt toegepast die het gebruik van Adobe Primetime-verificatie aanroept).

Het licentieverzoek bevat het DRM-beleid dat is gebruikt tijdens het verpakken/coderen van de inhoud. Het DRM-beleid wordt gebruikt om de DRM-licentie te genereren die aan de client wordt geretourneerd. In het standaardscenario, moet u alle DRM beleidsbesluiten bij de tijd van het inhoudspakken nemen. Klanten die meer controle over deze workflows willen hebben de volgende opties:

1. Integreer Primetime-verificatie om extra machtigingscontroles toe te voegen voordat u het bestand afspeelt.
1. Maak een machtigingsservice op locatie die door Primetime Cloud DRM wordt opgevraagd voordat u een apparaat toestaat inhoud in een pakket af te spelen.

Uw on-premisse machtigingsservice moet een reactie op Primetime Cloud DRM leveren die de volgende twee gegevens bevat:

* `isAllowed`
* `drmPolicyToUse`

Deze bepalen of een apparaat de inhoud mag afspelen en welk DRM-beleid moet worden gebruikt om de DRM-licentie te genereren (als `isAllowed` true is).

Dit document behandelt wat u moet doen om Optie 2 hierboven te verwezenlijken: Implementeer uw eigen externe machtigingsservice op locatie en stel deze beschikbaar voor Primetime Cloud DRM voor inhoud die u hebt verpakt.
