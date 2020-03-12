---
description: Doorgaans zijn alle Primetime DRM-licenties tijdens het maken gebonden aan een uniek apparaat. Deze binding voorkomt dat gebruikers licenties zonder toestemming op verschillende apparaten kunnen delen. Naast de binding per apparaat, biedt Primetime DRM de mogelijkheid om licenties te binden aan een apparaatdomein of groep apparaten.
seo-description: Doorgaans zijn alle Primetime DRM-licenties tijdens het maken gebonden aan een uniek apparaat. Deze binding voorkomt dat gebruikers licenties zonder toestemming op verschillende apparaten kunnen delen. Naast de binding per apparaat, biedt Primetime DRM de mogelijkheid om licenties te binden aan een apparaatdomein of groep apparaten.
seo-title: Gecodeerde inhoud afspelen met domeinondersteuning
title: Gecodeerde inhoud afspelen met domeinondersteuning
uuid: 8854cc0f-9bfc-4833-82d7-a3f46ac88e06
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# Ondersteuning van apparaatdomeinen {#device-domain-support}

Doorgaans zijn alle Primetime DRM-licenties tijdens het maken gebonden aan een uniek apparaat. Deze binding voorkomt dat gebruikers licenties zonder toestemming op verschillende apparaten kunnen delen. Naast de binding per apparaat, biedt Primetime DRM de mogelijkheid om licenties te binden aan een apparaatdomein of groep apparaten.

Als de metagegevens voor de inhoud aangeven dat apparaatdomeinregistratie is vereist, kan de toepassing een API aanroepen om deel te nemen aan een apparaatgroep. Deze handeling leidt ertoe dat een domeinregistratieverzoek naar de domeinserver wordt verzonden. Zodra een vergunning aan een apparatengroep wordt uitgegeven, kan de vergunning worden uitgevoerd en met andere apparaten worden gedeeld die zich bij de apparatengroep hebben aangesloten.

De apparaatgroepinformatie wordt vervolgens gebruikt in het `DRMContentData` `VoucherAccessInfo` object, dat vervolgens wordt gebruikt om de informatie te presenteren die nodig is om een licentie op te halen en te gebruiken.

## Gecodeerde inhoud afspelen met domeinondersteuning {#play-encrypted-content-using-domain-support}

Voer de volgende stappen uit om gecodeerde inhoud af te spelen met Primetime DRM:

1. Controleer `VoucherAccessInfo.deviceGroup`met deze optie of apparaatgroepregistratie verplicht is.
1. Indien verificatie vereist is:
   1. Gebruik het `DeviceGroupInfo.authenticationMethod` bezit te weten komt als de authentificatie wordt vereist.
   1. Als verificatie vereist is, verifieert u de gebruiker door EEN van de volgende stappen uit te voeren:

      * Haal de gebruikersnaam en het wachtwoord van de gebruiker op en activeer `DRMManager.authenticate(deviceGroup.serverURL, deviceGroup.domain, username, password)`.
      * Haal een in de cache opgeslagen/vooraf gegenereerde verificatietoken op en activeer `DRMManager.setAuthenticationToken()`.
   1. Invoeden `DRMManager.addToDeviceGroup()`
1. Haal de licentie voor de inhoud op door een van de volgende taken uit te voeren:
   1. Gebruik de `DRMManager.loadVoucher()` methode.
   1. Haal de licentie op van een ander apparaat dat in dezelfde apparaatgroep is geregistreerd en geef de licentie aan de ` DRMManager` hand van de `DRMManager.storeVoucher()` methode.
1. Speel de gecodeerde inhoud af met de `Primetime.play()` methode.
Als u de licentie voor de inhoud wilt exporteren, kunnen alle apparaten de onbewerkte bytes van de licentie via de `DRMVoucher.toByteArray()` methode verschaffen nadat u de licentie hebt verkregen van de Primetime DRM-licentieserver. Inhoudsproviders beperken doorgaans het aantal apparaten in een apparaatgroep. Als de limiet is bereikt, moet u mogelijk de `DRMManager.removeFromDeviceGroup()` methode op een ongebruikt apparaat aanroepen voordat u het huidige apparaat registreert.