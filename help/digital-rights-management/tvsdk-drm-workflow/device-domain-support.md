---
description: Doorgaans zijn alle Primetime DRM-licenties tijdens het maken gebonden aan een uniek apparaat. Deze binding voorkomt dat gebruikers licenties zonder toestemming op verschillende apparaten kunnen delen. Naast de binding per apparaat, biedt Primetime DRM de mogelijkheid om licenties te binden aan een apparaatdomein of groep apparaten.
title: Gecodeerde inhoud afspelen met domeinondersteuning
exl-id: 3c9badfc-046b-4c56-bde1-7b3b708bfaa2
source-git-commit: 59f7f8aa82be59c4012ee80648032600590bc4e1
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# Ondersteuning voor apparaatdomein {#device-domain-support}

Doorgaans zijn alle Primetime DRM-licenties tijdens het maken gebonden aan een uniek apparaat. Deze binding voorkomt dat gebruikers licenties zonder toestemming op verschillende apparaten kunnen delen. Naast de binding per apparaat, biedt Primetime DRM de mogelijkheid om licenties te binden aan een apparaatdomein of groep apparaten.

Als de metagegevens voor de inhoud aangeven dat apparaatdomeinregistratie is vereist, kan de toepassing een API aanroepen om deel te nemen aan een apparaatgroep. Deze handeling leidt ertoe dat een domeinregistratieverzoek naar de domeinserver wordt verzonden. Zodra een vergunning aan een apparatengroep wordt uitgegeven, kan de vergunning worden uitgevoerd en met andere apparaten worden gedeeld die zich bij de apparatengroep hebben aangesloten.

De informatie van de apparatengroep wordt dan gebruikt in `DRMContentData` `VoucherAccessInfo` voorwerp, dat dan zal worden gebruikt om de informatie te presenteren die wordt vereist om een vergunning met succes terug te winnen en te verbruiken.

## Gecodeerde inhoud afspelen met domeinondersteuning {#play-encrypted-content-using-domain-support}

Voer de volgende stappen uit om gecodeerde inhoud af te spelen met Primetime DRM:

1. Controleer met `VoucherAccessInfo.deviceGroup` of apparaatgroepregistratie verplicht is.
1. Indien verificatie vereist is:
   1. Gebruik de eigenschap `DeviceGroupInfo.authenticationMethod` om uit te zoeken of verificatie is vereist.
   1. Als verificatie vereist is, verifieert u de gebruiker door EEN van de volgende stappen uit te voeren:

      * Haal de gebruikersnaam en het wachtwoord van de gebruiker op en activeer `DRMManager.authenticate(deviceGroup.serverURL, deviceGroup.domain, username, password)`.
      * Haal een in de cache opgeslagen/vooraf gegenereerde verificatietoken op en activeer `DRMManager.setAuthenticationToken()`.
   1. `DRMManager.addToDeviceGroup()` aanroepen
1. Haal de licentie voor de inhoud op door een van de volgende taken uit te voeren:
   1. Gebruik de methode `DRMManager.loadVoucher()`.
   1. Haal de licentie op van een ander apparaat dat in dezelfde apparaatgroep is geregistreerd en geef de licentie via de methode `DRMManager.storeVoucher()` aan de `DRMManager`.
1. Speel de gecodeerde inhoud gebruikend de `Primetime.play()` methode.
Als u de licentie voor de inhoud wilt exporteren, kunnen alle apparaten de onbewerkte bytes van de licentie verschaffen via de methode `DRMVoucher.toByteArray()` nadat u de licentie van de Primetime DRM-licentieserver hebt verkregen. Inhoudsproviders beperken doorgaans het aantal apparaten in een apparaatgroep. Als de limiet is bereikt, moet u mogelijk de `DRMManager.removeFromDeviceGroup()`-methode op een ongebruikt apparaat aanroepen voordat u het huidige apparaat registreert.
