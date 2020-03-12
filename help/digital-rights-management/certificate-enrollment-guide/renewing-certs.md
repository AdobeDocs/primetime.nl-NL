---
seo-title: Certificaten vernieuwen
title: Certificaten vernieuwen
uuid: 12a560b0-966b-424e-bfe5-22e9c10d8667
translation-type: tm+mt
source-git-commit: b4b50471ab0ba98329862322a61bf73aa9e471d5

---


# Certificaten vernieuwen{#renew-certificates}

Houd rekening met de volgende beperkingen voor certificaatvernieuwing die zijn gebaseerd op uw configuratie van Adobe Primetime DRM SDK:

* Primetime DRM Production SDK

   Adobe biedt de eerste set gratis certificaten voor de Primetime DRM Production SDK wanneer u een ondersteuningscontract aanschaft. Als u geen supportcontract hebt, kunt u een reeks vernieuwingscertificaten kopen die twee jaar geldig zijn.
* Primetime DRM Evaluation SDK

   Het certificaat dat voor deze SDK is ingesteld, is één jaar geldig en kan niet worden verlengd.
* Primetime DRM-proefversie van SDK

   De proefversie van Primetime DRM SDK is drie maanden geldig en Adobe biedt één set gratis vernieuwingscertificaten.

## Nieuwe certificaten implementeren en oude certificaten gebruiken voor bestaande inhoud {#section_345C92D1C9794B0BBB9A9B0702EC95FF}

In Primetime DRM kunt u toestaan dat een licentieserver een licentie geeft voor inhoud die is verpakt met vorige (of zelfs verlopen) pakketcertificaten. Als u uw server wilt configureren voor het accepteren van licentieaanvragen van eerder verpakte inhoud, geeft u uw oude certificaat op aan uw server en werkt u het configuratiebestand van uw server bij, zodat de server weet waar de oude certificaten moeten worden gevonden. Zie Certificaatupdates *afhandelen wanneer door Adobe uitgegeven certificaten verlopen* in de Adobe Primetime DRM SDK *gebruiken voor het beschermen van inhoud*.

Als uw servertoepassing is gebaseerd op de Primetime DRM-naslagimplementatie, hoeft u uw serverprogramma niet bij te werken. In het `flashaccess-refimpl.properties` dossier, zijn er gebieden waarin u extra certificaten van de Server van het Vervoer en van de Vergunning kunt specificeren. Als u slechts één certificaat hebt, hoeft u deze eigenschappen niet in te vullen. Als u certificaten hebt verlopen en deze certificaten wilt gebruiken wanneer u licentiereacties uitgeeft, moet u deze certificaten aan het configuratiebestand verstrekken en de server opnieuw starten.

Gebruik de volgende eigenschappen om oude certificaten op te geven:

* `#HandlerConfiguration.AdditionalServerTransportCredential.1=transport.pfx`
* `#HandlerConfiguration.AdditionalServerTransportCredential.1.password=[password]`
* `#AsymmetricKeyRetrieval.ServerCredential.1=license_server.pfx`
* `#AsymmetricKeyRetrieval.ServerCredential.1.password=[password]`

