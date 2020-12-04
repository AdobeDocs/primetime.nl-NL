---
seo-title: Overzicht van out-of-band licenties
title: Overzicht van out-of-band licenties
uuid: 82e4529a-ee1b-4c0c-8885-e0e68319d1a0
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---


# Out-of-band licenties {#out-of-band-licenses}

Licenties kunnen ook offline worden verkregen (zonder contact op te nemen met een Primetime DRM-licentieserver) door de licentie op schijf en in het geheugen op te slaan met de methode `storeVoucher()`.

Als u gecodeerde video&#39;s wilt afspelen in Primetime, moet de respectievelijke runtime de licentie voor die video verkrijgen. De licentie bevat de coderingssleutel van de video en wordt gegenereerd door de Primetime DRM-licentieserver die de klant heeft geïmplementeerd.

De runtime verkrijgt deze licentie over het algemeen door een licentieaanvraag te verzenden naar de Primetime DRM-licentieserver die wordt aangegeven in de DRM-metagegevens van de video ( `DRMContentData`-klasse). De toepassing kan dit licentieverzoek activeren door de methode `DRMManager.loadVoucher()` aan te roepen.

`DRMManager.storeVoucher()` kan de aanvraag licenties die hij offline heeft verkregen, verzenden. De runtime kan het licentieaanvraagproces dan overslaan en de doorgestuurde licenties gebruiken voor het afspelen van gecodeerde video&#39;s. De licentie moet nog steeds worden gegenereerd door de Primetime DRM-licentieserver voordat deze offline kan worden verkregen. U kunt de licenties echter wel hosten op elke HTTP-server in plaats van op een Primetime DRM-licentieserver.

`DRMManager.storeVoucher()` wordt ook gebruikt ter ondersteuning van het delen van licenties tussen meerdere apparaten. Na Primetime DRM 3.0 wordt deze functie &#39;&#39;Device Domain Support&#39;&#39; genoemd. Als uw plaatsing dit gebruiksgeval steunt, kunt u veelvoudige machines aan een apparatengroep registreren gebruikend de `DRMManager.addToDeviceGroup()` methode. Als er een computer met een geldige domeingebonden vergunning voor een bepaalde inhoud is, kan de toepassing de geserialiseerde vergunning dan halen gebruikend de `DRMVoucher.toByteArray()` methode en op uw andere machines kunt u de vergunningen invoeren gebruikend de `DRMManager.storeVoucher()` methode.

## Over apparaatregistratie {#about-device-registration}

Alle Primetime DRM-licenties moeten tijdens het maken aan een eindgebruiker worden gebonden. Binding is het cryptografische proces waarbij een specifieke entiteit alleen de mogelijkheid krijgt om de licentie te gebruiken. Dit is nodig om te voorkomen dat &quot;drijvende licenties&quot; worden gebruikt door willekeurige apparatuur. Voor Primetime DRM-licenties ‘pre-generate’-licenties betekent dit dat de &quot;target&quot; van deze vooraf gegenereerde licenties van tevoren bekend moet zijn. Primetime DRM verwijst naar dit als &quot;Apparaatregistratie&quot;.

## Een apparaat {#register-a-device} registreren

Laten we ervan uitgaan dat u de volgende taken hebt uitgevoerd:

* U hebt de Primetime DRM Server SDK ingesteld.
* U hebt een HTTP-server ingesteld voor het uitgeven van vooraf gegenereerde licenties.
* U hebt een Primetime-toepassing gemaakt om de beveiligde inhoud weer te geven.

 De registratiefase van het apparaat omvat de volgende acties:

1. De toepassing maakt een willekeurig gegenereerde id.
1. De toepassing roept de methode `DRMManager.authenticate()` aan. De toepassing moet de willekeurig gegenereerde id opnemen in het verificatieverzoek. Neem bijvoorbeeld de id op in het veld Gebruikersnaam.
1. De in Stap 2 vermelde actie zal in Primetime DRM resulteren die een authentificatieverzoek naar de server van de klant verzenden. Dit verzoek omvat het apparatencertificaat:
   1. De server extraheert het apparaatcertificaat en de gegenereerde id uit de aanvraag en slaat deze op.
   1. Het subsysteem van de klant genereert vooraf licenties voor dit apparaatcertificaat, slaat deze op en verleent toegang tot deze licenties op een manier die ze aan de gegenereerde id koppelt. .
1. De server reageert op het verzoek met een &quot;succesbericht&quot;.
1. De toepassing slaat de gegenereerde id op.

Na de apparaatregistratie gebruikt de toepassing de gegenereerde id op dezelfde manier als de apparaat-id in het vorige schema zou zijn gebruikt:
1. De toepassing probeert de gegenereerde id te vinden.
1. Als de gegenereerde id wordt gevonden, gebruikt de toepassing de gegenereerde id terwijl de vooraf gegenereerde licenties worden gedownload. De toepassing verzendt de licenties naar de Primetime DRM-client voor gebruik met de methode `DRMManager.storeVoucher()`. .
1. Als de gegenereerde id niet wordt gevonden, doorloopt de toepassing de registratieprocedure voor het apparaat.

## DRM-fabrieksinstellingen {#drm-factory-reset}

Wanneer de gebruiker van het apparaat de optie voor het opnieuw instellen van de DRM-fabriek aanroept, wordt het apparaatcertificaat gewist. Als u de beveiligde inhoud wilt blijven afspelen, moet de toepassing de registratieprocedure voor het apparaat opnieuw doorlopen. Als de toepassing een verouderde, vooraf gegenereerde licentie verzendt, zal de Primetime DRM-client deze afwijzen, aangezien de licentie voor een oudere apparaat-id was gecodeerd.

* Flash-API: [DRMManager.resetDRMVouchers()](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/drm/DRMManager.html#resetDRMVouchers()) - (Kan alleen worden aangeroepen als reactie op bepaalde niet-herstelbare DRM-foutcodes.)
* iOS API: [DRMManager resetDRM](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a0dd6c9662428583196e0419d3ea69446)
* Android-API: [DRMManager.resetDRM()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#resetDRM(com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMOperationCompleteCallback))