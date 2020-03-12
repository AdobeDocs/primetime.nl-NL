---
description: 'Adobe® Access™ is een geavanceerde oplossing voor het beheer van digitale rechten en de bescherming van inhoud voor hoogwaardige audiovisuele inhoud. Met gereedschappen die u maakt met Java API''s kunt u beleidsregels maken, beleidsregels toepassen op bestanden die audio- en video-inhoud bevatten en die bestanden versleutelen. De stappen op hoog niveau voor het uitvoeren van deze taken zijn als volgt '
seo-description: 'Adobe® Access™ is een geavanceerde oplossing voor het beheer van digitale rechten en de bescherming van inhoud voor hoogwaardige audiovisuele inhoud. Met gereedschappen die u maakt met Java API''s kunt u beleidsregels maken, beleidsregels toepassen op bestanden die audio- en video-inhoud bevatten en die bestanden versleutelen. De stappen op hoog niveau voor het uitvoeren van deze taken zijn als volgt '
seo-title: Overzicht
title: Overzicht
uuid: 874c175b-8207-49fa-aad4-204ccbee9c2c
translation-type: tm+mt
source-git-commit: 53654b740b03c6a79394d30704a41186d4655237

---


# Overzicht {#overview}

Adobe® Access™ is een geavanceerde oplossing voor het beheer van digitale rechten en de bescherming van inhoud voor hoogwaardige audiovisuele inhoud. Met gereedschappen die u maakt met Java API&#39;s kunt u beleidsregels maken, beleidsregels toepassen op bestanden die audio- en video-inhoud bevatten en die bestanden versleutelen. De stappen op hoog niveau voor het uitvoeren van deze taken zijn als volgt:

1. Gebruik de Java API&#39;s om de beleidseigenschappen en versleutelingsparameters in te stellen.
1. Maak een beleid waarin de gebruiksrollen voor de inhoud worden beschreven. (Zie [Werken met beleid](../../aaxs-protecting-content/content-working-with-policies/content-working-with-policies-overview.md)).

   U kunt een willekeurig aantal beleidsregels maken. De meeste gebruikers maken een klein aantal beleidsregels en passen deze toe op een groot aantal bestanden.

1. Een mediabestand verpakken.

   In dit verband betekent het *verpakken van een bestand* dat het wordt versleuteld en dat er een beleid op wordt toegepast. (Zie [Mediabestanden](../../aaxs-protecting-content/content-packaging-media-files/content-packaging-media-files-overview.md)verpakken.)

1. Voer de licentieserver uit om een licentie aan de gebruiker uit te geven.

De gecodeerde inhoud is nu gereed voor implementatie en de client kan de licentie aanvragen bij de server.

De SDK biedt een Java API om deze taken uit te voeren. De SDK bevat referentie-implementaties van de licentieserver en opdrachtregelprogramma&#39;s die zijn gebaseerd op de Java API&#39;s. Zie *Werken met de Adobe Access Reference Implementations* voor meer informatie.

## Nieuw in Adobe Access 5.2 {#section_06220EDE36B54DCB9CA7963B76DA8167}

* **Externe CEK**: De mogelijkheid om een CKMS (Content Key Management System) te integreren in de workflows voor het verzenden en verpakken van DRM-licenties in plaats van de CEK te coderen en te bundelen in de metagegevens van de inhoud. Zie [Overzicht](../../aaxs-drm-xkey-mgmt/aaxs-drm-using-external-cek-overview.md)van externe CEK van Adobe Access DRM.

* **Licentie (voucher) Return**: De mogelijkheid voor een client om een licentie die aan de client is uitgegeven, te retourneren (of te verwijderen).
* **Xbox Key Server**: De mogelijkheid om inhoud die naar de Xbox en Xbox 360 wordt verzonden, te beschermen. (Een Adobe Primetime-client is vereist.)

## Aangepaste gebruiksregels {#custom-usage-rules}

Geeft aangepaste gebruiksregels aan. U kunt aangepaste gegevens opnemen in licenties die door de licentieserver worden uitgegeven. De interpretatie/verwerking van deze gegevens is volledig tot aan de implementatie van de clienttoepassing en licentieserver.

Voorbeeld van gebruik: Laat rekbaarheid van gebruiksregels toe door andere bedrijfsregels toe te staan om veilig als deel van het beleid en/of inhoudsvergunning worden vervoerd. Om veiligheidsredenen, omdat deze gebruiksregels worden afgedwongen in aangepaste code voor clienttoepassingen, moet deze optie worden gebruikt in combinatie met de opties voor de witte lijst van AIR-toepassingen of Flash Player SWF. Zie &quot;Beperkingen voor[runtime en toepassingen](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-runtime-application-restrictions/content-whitelist-air.md)&quot; voor meer informatie.