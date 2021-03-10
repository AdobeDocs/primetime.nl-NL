---
title: Bestaande DRM-inhoud bijwerken voor gebruik van Cloud DRM (optioneel)
description: Bestaande DRM-inhoud bijwerken voor gebruik van Cloud DRM (optioneel)
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---


# Bestaande DRM-inhoud bijwerken voor gebruik van Cloud DRM (optioneel) {#update-existing-drm-content-to-use-cloud-drm-optional}

Als u een bestaande bibliotheek met inhoud hebt die is beveiligd door Primetime DRM, is het mogelijk om de bestaande inhoud opnieuw aan te roepen om de Primetime Cloud DRM-service te gebruiken, in plaats van de oorspronkelijke bronbestanden opnieuw te verpakken/te coderen. Wanneer de inhoud opnieuw wordt geheaderd, worden de DRM-metagegevens van de inhoud in het HLS-manifest bijgewerkt. Het voert geen unencryption/re-encryptie van het oorspronkelijke middel uit. Dit kan handig zijn als de oorspronkelijke broninhoud niet beschikbaar is of als er bezorgdheid is over de hoeveelheid bronnen die nodig zijn om een grote bibliotheek opnieuw te verpakken.

Het is mogelijk de Primetime DRM Java SDK te gebruiken om de metagegevens via programmacode bij te werken. Bovendien kan het [!DNL OfflinePackager.jar] bevel-lijn hulpmiddel inbegrepen met deze Uitrusting van de Bescherming deze taak ook verwezenlijken gebruikend `-drm_refresh` optie.

## Details van nieuwe koptekst {#section_3F3980D8E775450588C64E02A8448189}

Als u CloudDRM wilt gebruiken, moet de volgende velden opnieuw worden weergegeven:

* Licentieserver-URL (naar [!DNL ht<span></span>tps://access.adobeprimetime.com/flashaccessserver/axs_prod])
* Certificaat van licentieserver (naar het certificaat van de CloudDRM-licentieserver)
* Transportcertificaat (naar het transportcertificaat van CloudDRM)
* Packager Credential (Voor de gegevens van de verpakker die u hebt geactiveerd voor gebruik met CloudDRM)

## DRM-metagegevens zoeken {#section_28721CB7966F40708AEC8637F2E9BB72}

Inhoud die gebruikmaakt van HTTP-technologie (zoals HDS of HLS), gebruikt een manifest dat verwijst naar de DRM-metagegevens van de Adobe Access. In HDS wordt naar de metagegevens verwezen door de tag `<drmmeta>` en in HLS wordt ernaar verwezen door de tag `#EXT-X-FAXS-CM`. In beide scenario&#39;s kunnen de metagegevens inline in het manifest worden opgenomen als een met basis 64 gecodeerde blob, of extern worden vermeld als een binair bestand. Als de meta-gegevens ingebed/gealigneerd in manifest zijn, kunt u base64 moeten eerst decoderen de meta-gegevens in binaire gegevens alvorens die gegevens te gebruiken om meta-gegevens te concretiseren DRM.

## De opgenomen OfflinePackager.jar {#section_37C2091856E44AA380D742C72B4DD1A7} gebruiken

Geef `-drm_refresh option` op de opdrachtregel. Er wordt een nieuw manifestbestand gemaakt met bijgewerkte DRM-metagegevens, terwijl de inhoud niet opnieuw wordt gecodeerd.

## De Primetime DRM Java SDK gebruiken om {#section_7EDBAC4C78DF4CD5BE8410EEAD8437A2} opnieuw te koppen

Het bijwerken van een bestaande DRM Meta-gegevens kan worden verwezenlijkt door Primetime DRM (vroeger genoemd geworden Adobe Toegang DRM) Java SDK voor een programmatic benadering te gebruiken. Raadpleeg het [!DNL RegenerateMetadata.java] codevoorbeeld in het [!DNL /Reference Implmentation/Command Line Tools/samples/]-pakket van de SDK voor meer informatie. De Adobe Access Java SDK maakt geen deel uit van deze CloudDRM-beveiligingskit en moet rechtstreeks bij Adobe worden aangeschaft. Neem voor meer informatie contact op met uw Adobe-zakelijke contactpersoon.