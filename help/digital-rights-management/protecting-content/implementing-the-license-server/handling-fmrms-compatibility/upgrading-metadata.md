---
title: Metagegevens bijwerken
description: Metagegevens bijwerken
copied-description: true
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---


# Metagegevens bijwerken{#upgrading-metadata}

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

