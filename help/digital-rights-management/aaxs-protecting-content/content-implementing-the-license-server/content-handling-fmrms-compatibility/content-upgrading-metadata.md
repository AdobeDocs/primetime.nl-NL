---
seo-title: Metagegevens bijwerken
title: Metagegevens bijwerken
uuid: cad0b23e-50ca-47ae-871f-be571cb00a26
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---


# Metagegevens bijwerken{#upgrading-metadata}

Als een Adobe Access-client inhoud aantreft die is verpakt met Flash Media Rights Management Server 1.x, worden de coderingsmetagegevens uit de inhoud opgehaald en naar de server verzonden. De server converteert de FMRMS 1.x-metagegevens naar de indeling Adobe Access en stuurt deze terug naar de client. De client verzendt de bijgewerkte metagegevens vervolgens in een standaard Adobe Access-licentieaanvraag.

* De klasse van de verzoekmanager is `com.adobe.flashaccess.sdk.protocol.compatibility.FMRMSv1MetadataHandler`.
* De aanvraag-URL is &quot;*Basis-URL van 1.x-inhoud*&quot; +&quot;/flashaccess/headerconversion/v1&quot;.

De omzetting van metagegevens kan direct worden uitgevoerd wanneer de server de oude metagegevens van de client ontvangt. De server kan de oude inhoud ook vooraf verwerken en de omgezette metagegevens opslaan. in dit geval hoeft de server alleen de nieuwe metagegevens op te halen die overeenkomen met de licentie-id van de oude metagegevens wanneer de client om nieuwe metagegevens vraagt.

Voor het omzetten van metagegevens moet de server de volgende stappen uitvoeren:

* `LiveCycleKeyMetaData` ophalen. Als u de metagegevens vooraf wilt converteren, kunt u `LiveCycleKeyMetaData` uit een 1.x-pakketbestand verkrijgen met `MediaEncrypter.examineEncryptedContent()`. De metagegevens worden ook opgenomen in het verzoek om omzetting van metagegevens ( `FMRMSv1MetadataHandler.getOriginalMetadata()`).
* Haal de licentie-id op uit de oude metagegevens en zoek naar de coderingssleutel en het beleid (deze informatie stond oorspronkelijk in de Adobe LiveCycle ES-database). Het beleid van LiveCycle ES moet in het beleid van de Toegang 2.0 van Adobe worden omgezet.) De implementatie van de Verwijzing omvat manuscripten en steekproefcode voor het omzetten van het beleid en het uitvoeren van vergunningsinformatie van LiveCycle ES.
* Vul het `V2KeyParameters` voorwerp in (dat u door `MediaEncrypter.getKeyParameters()`) te roepen terugwint.
* Laad de `SigningCredential`. Dit is de pakketreferentie die door Adobe is uitgegeven voor het ondertekenen van versleutelingsmetagegevens. Haal het `SignatureParameters`-object op door `MediaEncrypter.getSignatureParameters()` aan te roepen en vul de ondertekeningsreferentie in.
* Roep `MetaDataConverter.convertMetadata()` aan om `V2ContentMetaData` te verkrijgen.
* Roep `V2ContentMetaData.getBytes()` aan en sla deze op voor toekomstig gebruik of roep `FMRMSv1MetadataHandler.setUpdatedMetadata()`.

