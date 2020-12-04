---
title: Opmerkingen bij de release DRM 5.3.1
seo-title: Opmerkingen bij de release DRM 5.3.1
description: In de Opmerkingen bij de release DRM 5.3.1 worden de nieuwe functies en de bekende problemen in DRM 5.3.1 beschreven.
seo-description: In de Opmerkingen bij de release DRM 5.3.1 worden de nieuwe functies en de bekende problemen in DRM 5.3.1 beschreven.
uuid: bb61b79f-a5b3-42ed-8016-495b1ac99ea6
contentOwner: dekalra
topic-tags: release-notes
products: SG_PRIMETIME
translation-type: tm+mt
source-git-commit: e644e8497e118e2d03e72bef727c4ce1455d68d6
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---


# Opmerkingen bij de release DRM 5.3.1 {#drm-release-notes}

In de Opmerkingen bij de release DRM 5.3.1 worden de nieuwe functies en de bekende problemen in DRM 5.3.1 beschreven.

## Nieuwe functies in versie 5.3 {#new-features}

* **Beveiligd stoppen -** U kunt opgeven of het afspelen wordt gestopt of voortgezet aan het einde van een afspeelvenster.
* **RBOP (Resolution Based Output Protection) -** U kunt de uitvoerbeperkingen opgeven op basis van pixelresoluties.
* **CDM Gating -** Om HTML5 te ondersteunen heeft Adobe de Reference Implementation-licentieserver bijgewerkt die is opgenomen in de Adobe Primetime DRM (voorheen Adobe Access DRM) Java SDK om alle DRM-protocolberichten te kunnen gebruiken op één URL-eindpunt. Deze consolidatie van HTTP URL-methoden is nodig om te voldoen aan de HTML5 EME-specificatie (Encrypted Media Extension) die op zijn beurt moet worden geïmplementeerd door DRM-leveranciers van CDM (Content Decryption Module). Eerder waren dit de enige URL-eindpunten die werden weergegeven door de licentieserver voor de implementatie van verwijzingen:

   * /flashaccess/i15n/v3 (Individualisatie)
   * /flashaccess/license/v5 (Licentieverzoek)
   * /flashaccess/licenseRet/v5 (Return licentie)
   * /flashaccess/getServerVersion/v5 (Serverversie ophalen)

Nu, kunnen alle verzoeken (afkomstig van HTML5 CDM) aan één enkel eindpunt worden gericht: /req

Deze wijziging is achterwaarts compatibel met niet-CDM-platforms, zoals Flash Player, Android en iOS.

* **RBOP downscaling -** Specifiek voor de HTML5-ruimte, bevat RBOP automatische downscaling. Als een bitsnelheid hoger is dan de toegestane bitsnelheid die in het DRM-beleid is opgegeven, wordt de inhoud verkleind tot de maximaal toegestane resolutie. Als bijvoorbeeld een 1080p-stream wordt gestreamd naar een client die de inhoud weergeeft op een monitor die niet HDCP-compatibel is, kan het DRM-beleid aangeven dat de maximale resolutie 720p moet zijn. Primetime DRM decodeert de 1080p-stream en verkleint deze vervolgens naar 720p voordat deze op het scherm wordt weergegeven. Als de browser die de video afspeelt, vervolgens naar een monitor wordt gesleept die HDCP ondersteunt, wordt met Primetime DRM gestopt met het downscalen van de inhoud en kan deze op 1080 worden afgespeeld.

## Bekende problemen in versie 5.3 {#known-issues}

* `Hasher.bat (flashaccess-hasher.jar)` output logboekberichten aan  `flashaccess-global.log.`U moet ervoor zorgen dat het  `flashaccess-global.log` dossier in de zelfde folder met Hasher.bat is.

* De output van sommige `toJSON()`vraag keert `Strings` terug die niet volledig JSON volgzaam of volledig volgzaam op een stand-alone manier (d.w.z., zonder samenstelling van structuren JSON) zijn.

* Xbox key-server accepteert belangrijke aanvragen met een versiewaarde die niet gelijk is aan 1.

De Xbox key-server moet alleen belangrijke aanvragen ondersteunen waarvoor de versie gelijk is aan 1, maar momenteel accepteert de server sleutelaanvragen waarvoor de versie niet 1 is.

* Xbox key-server valideert een beleid niet correct.

De Xbox-sleutelserver mag geen beleid accepteren dat zich buiten de geldigheidsdatum bevindt, maar momenteel accepteert de server deze regels ongeacht de geldigheidsdatum.

* De Xbox-sleutelserver moet een sleutelverzoek afwijzen dat een metagegevens bevat die met een verkeerde cert in het pakket zijn gemaakt.
* Geretourneerde waarde van sommige JSON-structuren wordt niet correct opgemaakt voor op resolutie gebaseerde aan Output Protection gerelateerde klassen.

Verschillende klassen implementeren een toJSON()-methode die een JSON-compatibele representatie van dat object als een String moet retourneren, maar momenteel voldoet de geretourneerde waarde niet volledig aan JSON.

## Nuttige bronnen {#helpful-resources}

* Zie de volledige Help-documentatie op de pagina [Adobe Primetime Learn &amp; Support](https://helpx.adobe.com/support/primetime.html).
