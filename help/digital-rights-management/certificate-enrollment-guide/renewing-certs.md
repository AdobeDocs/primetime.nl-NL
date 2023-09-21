---
title: Certificaten vernieuwen
description: Certificaten vernieuwen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---

# Certificaten vernieuwen{#renew-certificates}

Houd rekening met de volgende beperkingen voor certificaatvernieuwing die zijn gebaseerd op uw Adobe Primetime DRM SDK-configuratie:

* Primetime DRM Production SDK

  Adobe biedt de eerste set gratis certificaten voor de Primetime DRM Production SDK wanneer u een ondersteuningscontract aanschaft. Als u geen supportcontract hebt, kunt u een reeks vernieuwingscertificaten kopen die twee jaar geldig zijn.
* Primetime DRM Evaluation SDK

  Het certificaat dat voor deze SDK is ingesteld, is één jaar geldig en kan niet worden verlengd.
* Primetime DRM-proefversie van SDK

  De proefversie van Primetime DRM SDK is drie maanden geldig en Adobe biedt één set gratis vernieuwingscertificaten.

## Nieuwe certificaten implementeren en oude certificaten gebruiken voor bestaande inhoud {#section_345C92D1C9794B0BBB9A9B0702EC95FF}

In Primetime DRM kunt u toestaan dat een licentieserver een licentie geeft voor inhoud die is verpakt met vorige (of zelfs verlopen) pakketcertificaten. Als u uw server wilt configureren voor het accepteren van licentieaanvragen van eerder verpakte inhoud, geeft u uw oude certificaat op aan uw server en werkt u het configuratiebestand van uw server bij, zodat de server weet waar de oude certificaten moeten worden gevonden. Zie voor meer informatie *Certificaatupdates verwerken wanneer door Adobe uitgegeven certificaten verlopen* in *De Adobe Primetime DRM SDK gebruiken voor het beschermen van inhoud*.

Als uw servertoepassing is gebaseerd op de Primetime DRM-naslagimplementatie, hoeft u uw serverprogramma niet bij te werken. In de `flashaccess-refimpl.properties` het dossier, zijn er gebieden waarin u extra certificaten van de Server van het Vervoer en van de Vergunning kunt specificeren. Als u slechts één certificaat hebt, hoeft u deze eigenschappen niet in te vullen. Als u certificaten hebt verlopen en deze certificaten wilt gebruiken wanneer u licentiereacties uitgeeft, moet u deze certificaten aan het configuratiebestand verstrekken en de server opnieuw starten.

Gebruik de volgende eigenschappen om oude certificaten op te geven:

* `#HandlerConfiguration.AdditionalServerTransportCredential.1=transport.pfx`
* `#HandlerConfiguration.AdditionalServerTransportCredential.1.password=[password]`
* `#AsymmetricKeyRetrieval.ServerCredential.1=license_server.pfx`
* `#AsymmetricKeyRetrieval.ServerCredential.1.password=[password]`
