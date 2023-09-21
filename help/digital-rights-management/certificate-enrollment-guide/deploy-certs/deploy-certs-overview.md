---
title: Overzicht van certificaten implementeren
description: Overzicht van certificaten implementeren
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# Overzicht {#deploy-certificates-overview}

Als u certificaten wilt toevoegen aan de Adobe Primetime DRM-eigenschappenbestanden, converteert u het PKCS#7-bestand naar een PFX-bestand met de persoonlijke sleutel en genereert u een PEM-bestand of een DER-bestand.

* Wanneer een referentie (certificaat en persoonlijke sleutel) vereist is, hebben de opdrachtregelprogramma&#39;s van Primetime DRM en de Adobe HTTP Dynamic Streaming packager een PFX-bestand nodig. De SDK, de Implementatie van de Verwijzing, en de Server Primetime DRM voor Beschermde Streaming kunnen een PFX- dossier goedkeuren en kunnen een referentie ook gebruiken die op HSM wordt opgeslagen.
* Wanneer alleen een certificaat is vereist, kunnen de meeste Primetime DRM-componenten een PEM-bestand, DER-bestand of een certificaat op een HSM gebruiken. De Adobe HTTP Dynamic Streaming packager accepteert alleen DER-bestanden voor certificaten.
