---
description: Adobe® Access™ is een geavanceerde oplossing voor digitaal rechtenbeheer en contentbescherming voor hoogwaardige audiovisuele inhoud. Met gereedschappen die u maakt met Java API's kunt u beleidsregels maken, beleidsregels toepassen op bestanden die audio- en video-inhoud bevatten en die bestanden versleutelen. De stappen op hoog niveau voor het uitvoeren van deze taken zijn als volgt
title: Overzicht
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# Overzicht {#overview}

Adobe® Access™ is een geavanceerde oplossing voor digitaal rechtenbeheer en contentbescherming voor hoogwaardige audiovisuele inhoud. Met gereedschappen die u maakt met Java API&#39;s kunt u beleidsregels maken, beleidsregels toepassen op bestanden die audio- en video-inhoud bevatten en die bestanden versleutelen. De stappen op hoog niveau voor het uitvoeren van deze taken zijn als volgt:

1. Gebruik de Java API&#39;s om de beleidseigenschappen en versleutelingsparameters in te stellen.
1. Maak een beleid waarin de gebruiksrollen voor de inhoud worden beschreven. (Zie [Werken met beleid](../../aaxs-protecting-content/content-working-with-policies/content-working-with-policies-overview.md)).

   U kunt een willekeurig aantal beleidsregels maken. De meeste gebruikers maken een klein aantal beleidsregels en passen deze toe op een groot aantal bestanden.

1. Een mediabestand verpakken.

   In dit verband *het verpakken van een bestand* middelen om het te coderen en er een beleid op toe te passen. (Zie [Mediabestanden verpakken](../../aaxs-protecting-content/content-packaging-media-files/content-packaging-media-files-overview.md).)

1. Voer de licentieserver uit om een licentie aan de gebruiker uit te geven.

De gecodeerde inhoud is nu gereed voor implementatie en de client kan de licentie aanvragen bij de server.

De SDK biedt een Java API om deze taken uit te voeren. De SDK bevat referentie-implementaties van de licentieserver en opdrachtregelprogramma&#39;s die zijn gebaseerd op de Java API&#39;s. Zie voor meer informatie *De implementatie van de Adobe Access Reference gebruiken*.

## Nieuw in Toegang 5.2 van de Adobe {#section_06220EDE36B54DCB9CA7963B76DA8167}

* **Externe CEK**: De mogelijkheid om een CKMS (Content Key Management System) te integreren in de workflows voor het serveren en verpakken van DRM-licenties in plaats van de CEK te coderen en te bundelen in de metagegevens van de inhoud. Zie [Adobe Access DRM External CEK Overview](../../aaxs-drm-xkey-mgmt/aaxs-drm-using-external-cek-overview.md).

* **Licentie (voucher) Return**: De mogelijkheid voor een client om een licentie die aan de client is uitgegeven, te retourneren (of te verwijderen).
* **Xbox Key-server**: De mogelijkheid om inhoud die naar de Xbox en Xbox 360 wordt verzonden, te beschermen. (Een Adobe Primetime-client is vereist.)

## Aangepaste gebruiksregels {#custom-usage-rules}

Geeft aangepaste gebruiksregels aan. U kunt aangepaste gegevens opnemen in licenties die door de licentieserver worden uitgegeven. De interpretatie/verwerking van deze gegevens is volledig tot de implementatie van de clienttoepassing en licentieserver.

Voorbeeld: laat uitbreidbaarheid van gebruiksregels toe door toe te staan dat andere bedrijfsregels veilig als deel van het beleid en/of inhoudsvergunning worden overgebracht. Om veiligheidsredenen, omdat deze gebruiksregels in de code van de douanecliënt worden afgedwongen, zou deze optie samen met de toepassing van AIR of de opties van de lijst van gewenste personen van de SWF van de Flash Player moeten worden gebruikt. Zie voor meer informatie [Beperkingen van runtime en toepassing](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-runtime-application-restrictions/content-allowlist-air.md).
