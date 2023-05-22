---
title: Metagegevens bijwerken
description: Metagegevens bijwerken
copied-description: true
exl-id: 04b3fb22-489e-41bb-95d0-99375f92fbae
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Metagegevens bijwerken{#upgrading-metadata}

Als een Adobe Access-client inhoud aantreft die is verpakt met Flash Media Rights Management Server 1.x, worden de coderingsmetagegevens uit de inhoud opgehaald en naar de server verzonden. De server converteert de FMRMS 1.x-metagegevens naar de indeling Adobe Access en stuurt deze terug naar de client. De client verzendt de bijgewerkte metagegevens vervolgens in een standaard Adobe Access-licentieaanvraag.

* De klasse request handler is `com.adobe.flashaccess.sdk.protocol.compatibility.FMRMSv1MetadataHandler`.
* De aanvraag-URL is &quot;*Basis-URL van 1.x-inhoud*&quot; +&quot;/flashaccess/headerconversion/v1&quot;.

De omzetting van metagegevens kan direct worden uitgevoerd wanneer de server de oude metagegevens van de client ontvangt. De server kan de oude inhoud ook vooraf verwerken en de omgezette metagegevens opslaan. in dit geval hoeft de server alleen de nieuwe metagegevens op te halen die overeenkomen met de licentie-id van de oude metagegevens wanneer de client om nieuwe metagegevens vraagt.

Voor het omzetten van metagegevens moet de server de volgende stappen uitvoeren:

* Get `LiveCycleKeyMetaData`. De metagegevens vooraf omzetten `LiveCycleKeyMetaData` kan uit een 1.x verpakt dossier worden verkregen gebruikend `MediaEncrypter.examineEncryptedContent()`. De metagegevens zijn ook opgenomen in het verzoek om omzetting van metagegevens ( `FMRMSv1MetadataHandler.getOriginalMetadata()`).
* Haal de licentie-id op uit de oude metagegevens en zoek naar de coderingssleutel en het beleid (deze informatie stond oorspronkelijk in de Adobe LiveCycle ES-database). Het beleid van LiveCycle ES moet in het beleid van de Toegang 2.0 van Adobe worden omgezet.) De implementatie van de Verwijzing omvat manuscripten en steekproefcode voor het omzetten van het beleid en het uitvoeren van vergunningsinformatie van LiveCycle ES.
* Vul de `V2KeyParameters` object (dat u ophaalt door `MediaEncrypter.getKeyParameters()`).
* Laad de `SigningCredential`, de gegevens van de verpakker die door Adobe zijn uitgegeven en die worden gebruikt voor het ondertekenen van versleutelingsmetagegevens. Krijg de `SignatureParameters` object aanroepen `MediaEncrypter.getSignatureParameters()` en vul de ondertekeningsreferentie in.
* Bellen `MetaDataConverter.convertMetadata()` om `V2ContentMetaData`.
* Bellen `V2ContentMetaData.getBytes()` en opslaan voor toekomstig gebruik, of bellen `FMRMSv1MetadataHandler.setUpdatedMetadata()`.
