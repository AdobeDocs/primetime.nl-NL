---
description: Voor degenen die bekend zijn met de Primetime Access DRM-oplossing van Adobe, zijn er enkele fundamentele architectonische verschillen tussen Access en de Primetime Cloud DRM, aangedreven door de ExpressPlay-oplossing.
seo-description: Voor degenen die bekend zijn met de Primetime Access DRM-oplossing van Adobe, zijn er enkele fundamentele architectonische verschillen tussen Access en de Primetime Cloud DRM, aangedreven door de ExpressPlay-oplossing.
seo-title: Migreren van toegang naar multi-DRM
title: Migreren van toegang naar multi-DRM
uuid: 3e33ca9a-867e-46b8-bf88-8dbfe14ff786
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c

---


# Migreren van toegang naar multi-DRM {#migrating-from-access-to-multi-drm}

Voor degenen die bekend zijn met de Primetime Access DRM-oplossing van Adobe, zijn er enkele fundamentele architectonische verschillen tussen Access en de Primetime Cloud DRM, aangedreven door de ExpressPlay-oplossing.

## Architectuurverschillen tussen toegang en multi-DRM

|  | Toegang | Multi-DRM |
|---|---|---|
| **Verpakken** | Packager is gebonden aan een licentieserver. Packager moet de openbare sleutel van de licentieserver kennen wanneer inhoud wordt verpakt. | Packager is niet gebonden aan één licentieserver. |
|  | Als de inhoud eenmaal is verpakt, wordt deze gebonden aan een bepaalde licentieserver. | Inhoud is niet gebonden aan een specifieke licentieserver. Een van de gevolgen hiervan is dat u alle inhoud kunt verpakken voordat u uw productielicentie aanschaft. |
|  | Packager hoeft niet te communiceren met enige vorm van sleutelopslag, omdat de toetsen veilig in de inhoud zelf (in metagegevens) zijn ingesloten nadat ze zijn gecodeerd. Alleen de bijbehorende licentieserver kan deze lezen. | De sleutels moeten *naar* de Plaatsen van een zeer belangrijk opslagsysteem worden verzonden, of *van* een Packager naar een zeer belangrijk opslagsysteem worden verzonden. Een sleutelopslagsysteem kan het eigen systeem van een klant zijn of het kan de Belangrijkste Opslag van ExpressPlay zijn. |
| **Entitlement** | De client vraagt om inhoud naar de Access Cloud-service. De Access-cloudservice vraagt dan het machtigingssysteem van de klant aan. Het machtigingssysteem van de klant reageert op de rechten van de klant. (De client heeft waarschijnlijk een cookie voor aanmelding bij de servers van de klant gekregen voordat de licentieaanvraag werd ingediend.) | De client vraagt om een token van de winkel van de klant (dit is waarschijnlijk dezelfde workflow waarin de klant eerder een verificatiecookie kreeg). Op dit moment voert de klant een machtigingencontrole uit. Als de machtigingencontrole overgaat, verzendt de klant een verzoek naar de servers ExpressPlay om een token voor de klant te genereren. Dit token is altijd gebonden aan een bepaald stuk inhoud en *kan* zijn gebonden aan een specifiek apparaat. De storefront van de klant stuurt het token terug naar de client. Wanneer de cliënt een DRM spelverzoek indient, is het teken inbegrepen in het verzoek (de methode voor dit is apparaat-specifiek), en de server DRM van ExpressPlay bevestigt het teken zonder uit te roepen aan de server van de klant. |