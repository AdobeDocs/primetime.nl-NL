---
description: Doorgaans zijn alle Primetime DRM-licenties tijdens het maken gebonden aan een uniek apparaat. Deze binding voorkomt dat gebruikers licenties zonder toestemming op verschillende apparaten kunnen delen. Naast de binding per apparaat, biedt Primetime DRM de mogelijkheid om licenties te binden aan een apparaatdomein of groep apparaten.
title: Gecodeerde inhoud afspelen met domeinondersteuning
exl-id: 3c9badfc-046b-4c56-bde1-7b3b708bfaa2
source-git-commit: 59f7f8aa82be59c4012ee80648032600590bc4e1
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# Ondersteuning van apparaatdomeinen {#device-domain-support}

Doorgaans zijn alle Primetime DRM-licenties tijdens het maken gebonden aan een uniek apparaat. Deze binding voorkomt dat gebruikers licenties zonder toestemming op verschillende apparaten kunnen delen. Naast de binding per apparaat, biedt Primetime DRM de mogelijkheid om licenties te binden aan een apparaatdomein of groep apparaten.

Als de metagegevens voor de inhoud aangeven dat apparaatdomeinregistratie is vereist, kan de toepassing een API aanroepen om deel te nemen aan een apparaatgroep. Deze handeling leidt ertoe dat een domeinregistratieverzoek naar de domeinserver wordt verzonden. Zodra een vergunning aan een apparatengroep wordt uitgegeven, kan de vergunning worden uitgevoerd en met andere apparaten worden gedeeld die zich bij de apparatengroep hebben aangesloten.

De informatie van de apparatengroep wordt dan gebruikt in `DRMContentData` `VoucherAccessInfo` -object, dat vervolgens wordt gebruikt om de informatie weer te geven die nodig is om een licentie op te halen en te gebruiken.

## Gecodeerde inhoud afspelen met domeinondersteuning {#play-encrypted-content-using-domain-support}

Voer de volgende stappen uit om gecodeerde inhoud af te spelen met Primetime DRM:

1. Gebruiken `VoucherAccessInfo.deviceGroup`, controleert u of apparaatgroepregistratie is vereist.
1. Indien verificatie vereist is:
   1. Gebruik de `DeviceGroupInfo.authenticationMethod` te weten komen het bezit als de authentificatie wordt vereist.
   1. Als verificatie vereist is, verifieert u de gebruiker door EEN van de volgende stappen uit te voeren:

      * Haal de gebruikersnaam en het wachtwoord van de gebruiker op en activeer `DRMManager.authenticate(deviceGroup.serverURL, deviceGroup.domain, username, password)`.
      * Verkrijg een caching/pre-geproduceerde authentificatietoken en haal aan `DRMManager.setAuthenticationToken()`.
   1. Invoeden `DRMManager.addToDeviceGroup()`
1. Haal de licentie voor de inhoud op door een van de volgende taken uit te voeren:
   1. Gebruik de `DRMManager.loadVoucher()` methode.
   1. Verkrijg de vergunning van een verschillend apparaat dat in de zelfde apparatengroep wordt geregistreerd en verstrek de vergunning aan `DRMManager` via de `DRMManager.storeVoucher()` methode.
1. Gecodeerde inhoud afspelen met de opdracht `Primetime.play()` methode.
Als u de licentie voor de inhoud wilt exporteren, kunnen alle apparaten de onbewerkte bytes van de licentie verschaffen via de `DRMVoucher.toByteArray()` na het verkrijgen van de licentie van de Primetime DRM-licentieserver. Inhoudsproviders beperken doorgaans het aantal apparaten in een apparaatgroep. Als de limiet is bereikt, moet u mogelijk de knop `DRMManager.removeFromDeviceGroup()` op een ongebruikt apparaat voordat het huidige apparaat wordt geregistreerd.
