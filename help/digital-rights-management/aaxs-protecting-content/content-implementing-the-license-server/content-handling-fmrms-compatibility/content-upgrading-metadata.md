---
title: Metagegevens bijwerken
description: Metagegevens bijwerken
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Metagegevens bijwerken{#upgrading-metadata}

Als een cliënt van de Toegang van de Adobe inhoud ontmoet die met de Server 1.x van het Rights Management van de Media van de Flash wordt verpakt, zal het de encryptiemetagegevens uit de inhoud halen en het verzenden naar de server. De server zet de FMRMS 1.x-metagegevens om in de indeling Adobe Access en stuurt deze terug naar de client. De cliënt verzendt dan de bijgewerkte meta-gegevens in een standaardvergunningsverzoek van de Toegang van de Adobe.

* De klasse request handler is `com.adobe.flashaccess.sdk.protocol.compatibility.FMRMSv1MetadataHandler`.
* De aanvraag-URL is &quot;*Basis-URL van 1.x-inhoud*&quot; +&quot;/flashaccess/headerconversion/v1&quot;.

De omzetting van metagegevens kan direct worden uitgevoerd wanneer de server de oude metagegevens van de client ontvangt. Als alternatief kan de server de oude inhoud vooraf verwerken en de omgezette metagegevens opslaan. Wanneer de client nieuwe metagegevens aanvraagt, moet de server gewoon de nieuwe metagegevens ophalen die overeenkomen met de licentie-id van de oude metagegevens.

Voor het omzetten van metagegevens moet de server de volgende stappen uitvoeren:

* Get `LiveCycleKeyMetaData`. De metagegevens vooraf omzetten `LiveCycleKeyMetaData` kan uit een 1.x verpakt dossier worden verkregen gebruikend `MediaEncrypter.examineEncryptedContent()`. De metagegevens zijn ook opgenomen in het verzoek om omzetting van metagegevens ( `FMRMSv1MetadataHandler.getOriginalMetadata()`).
* Haal de licentie-id op uit de oude metagegevens en zoek naar de coderingssleutel en het beleid (deze informatie stond oorspronkelijk in de Adobe LiveCycle ES-database). Het beleid van LiveCycle ES moet in de Toegang 2.0 van de Adobe beleid worden omgezet.) De implementatie van de Verwijzing omvat manuscripten en steekproefcode voor het omzetten van het beleid en het uitvoeren van vergunningsinformatie uit LiveCycle ES.
* Vul de `V2KeyParameters` object (dat u ophaalt door `MediaEncrypter.getKeyParameters()`).
* Laad de `SigningCredential`, de gegevens van de verpakker die door de Adobe worden uitgegeven en die worden gebruikt om versleutelingsmetagegevens te ondertekenen. Krijg de `SignatureParameters` object aanroepen `MediaEncrypter.getSignatureParameters()` en vul de ondertekeningsreferentie in.
* Bellen `MetaDataConverter.convertMetadata()` om de `V2ContentMetaData`.
* Bellen `V2ContentMetaData.getBytes()` en opslaan voor toekomstig gebruik, of bellen `FMRMSv1MetadataHandler.setUpdatedMetadata()`.
