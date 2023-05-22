---
description: Er zijn twee soorten verzoeken met betrekking tot de verenigbaarheid van de Server 1.x van het Rights Management van de Media van Flash. Eén type aanvraag wordt gebruikt om 1.x-clients te vragen een upgrade uit te voeren naar een runtime die Adobe Primetime DRM 2.0 of hoger ondersteunt. Een andere methode wordt gebruikt om 1.x-metagegevens bij te werken naar de Primetime DRM-indeling voordat een licentie kan worden aangevraagd. Ondersteuning voor deze aanvragen is alleen nodig als u eerder inhoud hebt geïmplementeerd waarvoor FMRMS 1.0 of 1.5 wordt gebruikt.
title: FMRMS-compatibiliteit afhandelen
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---


# FMRMS-compatibiliteit afhandelen {#handling-fmrms-compatibility}

Er zijn twee soorten verzoeken met betrekking tot de verenigbaarheid van de Server 1.x van het Rights Management van de Media van Flash. Eén type aanvraag wordt gebruikt om 1.x-clients te vragen een upgrade uit te voeren naar een runtime die Adobe Primetime DRM 2.0 of hoger ondersteunt. Een andere methode wordt gebruikt om 1.x-metagegevens bij te werken naar de Primetime DRM-indeling voordat een licentie kan worden aangevraagd. Ondersteuning voor deze aanvragen is alleen nodig als u eerder inhoud hebt geïmplementeerd waarvoor FMRMS 1.0 of 1.5 wordt gebruikt.

## Clients upgraden {#upgrading-clients}

Als een FMRMS 1.x-client contact opneemt met een Adobe Primetime DRM-server, moet de server de client vragen een upgrade uit te voeren.

* De klasse request handler is `com.adobe.flashaccess.sdk.protocol.compatibility.FMRMSv1RequestHandler`.
* De aanvraag-URL is &quot;*Basis-URL van 1.x-inhoud*&quot; + &quot; [!DNL /edcws/services/urn:EDCLicenseService]&quot;

   In tegenstelling tot andere Adobe Primetime-aanvraaghandlers, biedt deze handler geen toegang tot informatie over een verzoek of moet er reactiegegevens worden ingesteld. Maak een instantie van het dialoogvenster `FMRMSv1RequestHandler`en vervolgens `close()`

## Metagegevens bijwerken {#upgrading-metadata}

Als een Adobe Primetime DRM-client inhoud aantreft die is verpakt met Flash Media Rights Management Server 1.x, worden de coderingsmetagegevens uit de inhoud geëxtraheerd en naar de server verzonden. De server zet de FMRMS 1.x-metagegevens vervolgens om in de Primetime DRM-indeling en verzendt deze naar de client. De client verzendt de bijgewerkte metagegevens vervolgens in een standaard Primetime DRM-licentieaanvraag.

* De klasse request handler is `com.adobe.flashaccess.sdk.protocol.compatibility.FMRMSv1MetadataHandler`.
* De aanvraag-URL is &quot;*Basis-URL van 1.x-inhoud*&quot; +&quot; [!DNL /flashaccess/headerconversion/v1]&quot;.

De omzetting van metagegevens kan direct worden uitgevoerd wanneer de server de oude metagegevens van de client ontvangt. De server kan de oude inhoud ook vooraf verwerken en de omgezette metagegevens opslaan. in dit geval hoeft de server alleen de nieuwe metagegevens op te halen die overeenkomen met de licentie-id van de oude metagegevens wanneer de client om nieuwe metagegevens vraagt.

Voor het omzetten van metagegevens moet de server de volgende stappen uitvoeren:

* Get `LiveCycleKeyMetaData`. De metagegevens vooraf omzetten `LiveCycleKeyMetaData` kan uit een 1.x verpakt dossier worden verkregen gebruikend `MediaEncrypter.examineEncryptedContent()`. De metagegevens zijn ook opgenomen in het verzoek om omzetting van metagegevens ( `FMRMSv1MetadataHandler.getOriginalMetadata()`).

* Haal de licentie-id op uit de oude metagegevens en zoek naar de coderingssleutel en het DRM-beleid (deze informatie stond oorspronkelijk in de Adobe LiveCycle ES-database. Het LiveCycle ES DRM-beleid moet worden omgezet in Primetime DRM 2.0 DRM-beleid.) De implementatie van de Verwijzing omvat manuscripten en steekproefcode voor het omzetten van het beleid DRM en het uitvoeren van vergunningsinformatie van LiveCycle ES.
* Vul de `V2KeyParameters` object (dat u ophaalt door `MediaEncrypter.getKeyParameters()`).

* Laad de `SigningCredential`, de gegevens van de verpakker die door Adobe zijn uitgegeven en die worden gebruikt voor het ondertekenen van versleutelingsmetagegevens. Krijg de `SignatureParameters` object aanroepen `MediaEncrypter.getSignatureParameters()` en vul de ondertekeningsreferentie in.

* Bellen `MetaDataConverter.convertMetadata()` om `V2ContentMetaData`.

* Bellen `V2ContentMetaData.getBytes()` en opslaan voor toekomstig gebruik, of bellen `FMRMSv1MetadataHandler.setUpdatedMetadata()`.