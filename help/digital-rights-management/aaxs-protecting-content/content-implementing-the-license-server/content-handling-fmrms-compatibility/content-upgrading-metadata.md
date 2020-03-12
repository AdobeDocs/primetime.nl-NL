---
seo-title: Metagegevens bijwerken
title: Metagegevens bijwerken
uuid: cad0b23e-50ca-47ae-871f-be571cb00a26
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Metagegevens bijwerken{#upgrading-metadata}

Als een Adobe Access-client inhoud aantreft die is verpakt met Flash Media Rights Management Server 1.x, worden de versleutelingsmetagegevens uit de inhoud verwijderd en naar de server verzonden. De server converteert de FMRMS 1.x-metagegevens naar de Adobe Access-indeling en stuurt deze terug naar de client. De client verzendt de bijgewerkte metagegevens vervolgens in een standaard Adobe Access-licentieaanvraag.

* De klasse van de verzoekmanager is `com.adobe.flashaccess.sdk.protocol.compatibility.FMRMSv1MetadataHandler`.
* De aanvraag-URL is &quot;*Basis-URL van 1.x-inhoud*&quot; +&quot;/flashaccess/headerconversion/v1&quot;.

De omzetting van metagegevens kan direct worden uitgevoerd wanneer de server de oude metagegevens van de client ontvangt. De server kan de oude inhoud ook vooraf verwerken en de omgezette metagegevens opslaan. in dit geval hoeft de server alleen de nieuwe metagegevens op te halen die overeenkomen met de licentie-id van de oude metagegevens wanneer de client om nieuwe metagegevens vraagt.

Voor het omzetten van metagegevens moet de server de volgende stappen uitvoeren:

* Get `LiveCycleKeyMetaData`. Als u de metagegevens vooraf wilt converteren, kunt u deze verkrijgen via een 1.x-pakketbestand met `LiveCycleKeyMetaData` `MediaEncrypter.examineEncryptedContent()`. De metagegevens worden ook opgenomen in de aanvraag voor omzetting van metagegevens ( `FMRMSv1MetadataHandler.getOriginalMetadata()`).
* Haal de licentie-id op uit de oude metagegevens en zoek naar de coderingssleutel en het beleid (deze informatie stond oorspronkelijk in de Adobe LiveCycle ES-database). Het LiveCycle ES-beleid moet worden geconverteerd naar het Adobe Access 2.0-beleid.) De Reference Implementation bevat scripts en voorbeeldcode voor het converteren van het beleid en het exporteren van licentiegegevens uit LiveCycle ES.
* Vul het `V2KeyParameters` object in (dat u ophaalt door aan te roepen `MediaEncrypter.getKeyParameters()`).
* Laad de URL `SigningCredential`, de gegevens van de verpakker die door Adobe zijn uitgegeven voor het ondertekenen van versleutelingsmetagegevens. Haal het `SignatureParameters` object op door de ondertekeningsreferentie aan te roepen `MediaEncrypter.getSignatureParameters()` en in te vullen.
* Vraag `MetaDataConverter.convertMetadata()` om het `V2ContentMetaData`.
* Vraag `V2ContentMetaData.getBytes()` en bewaar voor toekomstig gebruik, of vraag `FMRMSv1MetadataHandler.setUpdatedMetadata()`.

