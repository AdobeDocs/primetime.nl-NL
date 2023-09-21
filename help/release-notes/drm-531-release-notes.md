---
title: Opmerkingen bij de release DRM 5.3.1
description: In de Opmerkingen bij de release DRM 5.3.1 worden de nieuwe functies en de bekende problemen in DRM 5.3.1 beschreven.
contentOwner: dekalra
topic-tags: release-notes
products: SG_PRIMETIME
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 0%

---

# Opmerkingen bij de release DRM 5.3.1 {#drm-release-notes}

In de Opmerkingen bij de release DRM 5.3.1 worden de nieuwe functies en de bekende problemen in DRM 5.3.1 beschreven.

## Nieuwe functies in versie 5.3 {#new-features}

* **Beveiligde stop -** U kunt opgeven of het afspelen wordt gestopt of voortgezet aan het einde van een afspeelvenster.
* **Op resolutie gebaseerde uitvoerbeveiliging (RBOP) -** U kunt de uitvoerbeperkingen opgeven op basis van pixelresoluties.
* **CDM-classificatie -** Ter ondersteuning van HTML5 heeft Adobe de referentietoepassingslicentieserver bijgewerkt die is opgenomen in de Adobe Primetime DRM (voorheen Adobe Access DRM) Java SDK, zodat alle DRM-protocolberichten op één URL-eindpunt kunnen worden geconsumeerd. Deze consolidatie van HTTP URL-methoden is nodig om te voldoen aan de HTML5 EME (Encrypted Media Extension)-specificatie die op zijn beurt moet worden geïmplementeerd door DRM-leveranciers van CDM (Content Decryption Module). Eerder waren dit de enige URL-eindpunten die werden weergegeven door de licentieserver voor de implementatie van verwijzingen:

   * /flashaccess/i15n/v3 (Individualisatie)
   * /flashaccess/license/v5 (Licentieverzoek)
   * /flashaccess/licenseRet/v5 (Return licentie)
   * /flashaccess/getServerVersion/v5 (Serverversie ophalen)

Nu, kunnen alle verzoeken (voortkomend uit een HTML5 CDM) aan één enkel eindpunt worden gericht: /req

Deze wijziging is achterwaarts compatibel met niet-CDM-platforms, zoals Flash Player, Android en iOS.

* **RBOP downscaling -** Specifiek voor de HTML5 ruimte, bevat RBOP automatisch het schrapen vermogen, waar als een bitsnelheid die de toelaatbare bitsnelheid overschrijdt die in het beleid DRM wordt gespecificeerd, de inhoud aan de maximum toelaatbare resolutie zal worden gedownschaald. Als bijvoorbeeld een 1080p-stream wordt gestreamd naar een client die de inhoud weergeeft op een monitor die niet HDCP-compatibel is, kan het DRM-beleid aangeven dat de maximale resolutie 720p moet zijn. Primetime DRM decodeert de 1080p-stream en verkleint deze vervolgens naar 720p voordat deze op het scherm wordt weergegeven. Als de browser die de video afspeelt vervolgens naar een monitor wordt gesleept die HDCP ondersteunt, wordt de downscaling van de inhoud door Primetime DRM gestopt en kan deze op 1080 worden afgespeeld.

## Bekende problemen in versie 5.3 {#known-issues}

* `Hasher.bat (flashaccess-hasher.jar)` output logboekberichten aan `flashaccess-global.log.`U moet ervoor zorgen dat de `flashaccess-global.log` bestand bevindt zich in dezelfde map met Hasher.bat.

* De uitvoer van sommige van de `toJSON()`call return `Strings` die niet volledig JSON-compatibel zijn of op zelfstandige wijze volledig voldoen (d.w.z. zonder samenstelling van JSON-structuren).

* Xbox key-server accepteert belangrijke aanvragen met een versiewaarde die niet gelijk is aan 1.

De Xbox key-server moet alleen belangrijke aanvragen ondersteunen waarvoor de versie gelijk is aan 1, maar momenteel accepteert de server sleutelaanvragen waarvoor de versie niet 1 is.

* Xbox key-server valideert een beleid niet correct.

De Xbox-sleutelserver mag geen beleid accepteren dat zich buiten de geldigheidsdatum bevindt, maar momenteel accepteert de server deze regels ongeacht de geldigheidsdatum.

* De Xbox-sleutelserver moet een sleutelverzoek afwijzen dat een metagegevens bevat die met een verkeerde cert in het pakket zijn gemaakt.
* Geretourneerde waarde van sommige JSON-structuren wordt niet correct opgemaakt voor op resolutie gebaseerde aan Output Protection gerelateerde klassen.

Verschillende klassen implementeren een toJSON()-methode die een JSON-compatibele representatie van dat object als een String moet retourneren, maar momenteel voldoet de geretourneerde waarde niet volledig aan JSON.

## Nuttige bronnen {#helpful-resources}

* Zie de volledige Help-documentatie op [Adobe Primetime - Meer informatie en ondersteuning](https://helpx.adobe.com/support/primetime.html) pagina.
