---
seo-title: Metagegevens bijwerken
title: Metagegevens bijwerken
uuid: 769483e6-a2d1-46cb-afcf-557aa807037c
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---


# Metagegevens bijwerken{#upgrading-metadata}

Als een Adobe Primetime DRM-client inhoud aantreft die is verpakt met Flash Media Rights Management Server 1.x, worden de coderingsmetagegevens uit de inhoud geëxtraheerd en naar de server verzonden. De server zet de FMRMS 1.x-metagegevens vervolgens om in de Primetime DRM-indeling en verzendt deze naar de client. De client verzendt de bijgewerkte metagegevens vervolgens in een standaard Primetime DRM-licentieaanvraag.

* De klasse van de verzoekmanager is `com.adobe.flashaccess.sdk.protocol.compatibility.FMRMSv1MetadataHandler`.
* De aanvraag-URL is &quot;*Basis-URL van 1.x-inhoud*&quot; +&quot; [!DNL /flashaccess/headerconversion/v1]&quot;.

De omzetting van metagegevens kan direct worden uitgevoerd wanneer de server de oude metagegevens van de client ontvangt. De server kan de oude inhoud ook vooraf verwerken en de omgezette metagegevens opslaan. in dit geval hoeft de server alleen de nieuwe metagegevens op te halen die overeenkomen met de licentie-id van de oude metagegevens wanneer de client om nieuwe metagegevens vraagt.

Voor het omzetten van metagegevens moet de server de volgende stappen uitvoeren:

* `LiveCycleKeyMetaData` ophalen. Als u de metagegevens vooraf wilt converteren, kunt u `LiveCycleKeyMetaData` uit een 1.x-pakketbestand verkrijgen met `MediaEncrypter.examineEncryptedContent()`. De metagegevens worden ook opgenomen in het verzoek om omzetting van metagegevens ( `FMRMSv1MetadataHandler.getOriginalMetadata()`).

* Haal de licentie-id op uit de oude metagegevens en zoek naar de coderingssleutel en het DRM-beleid (deze informatie stond oorspronkelijk in de Adobe LiveCycle ES-database. Het LiveCycle ES DRM-beleid moet worden omgezet in Primetime DRM 2.0 DRM-beleid.) De implementatie van de Verwijzing omvat manuscripten en steekproefcode voor het omzetten van het beleid DRM en het uitvoeren van vergunningsinformatie van LiveCycle ES.
* Vul het `V2KeyParameters` voorwerp in (dat u door `MediaEncrypter.getKeyParameters()`) te roepen terugwint.

* Laad de `SigningCredential`. Dit is de pakketreferentie die door Adobe is uitgegeven voor het ondertekenen van versleutelingsmetagegevens. Haal het `SignatureParameters`-object op door `MediaEncrypter.getSignatureParameters()` aan te roepen en vul de ondertekeningsreferentie in.

* Roep `MetaDataConverter.convertMetadata()` aan om `V2ContentMetaData` te verkrijgen.

* Roep `V2ContentMetaData.getBytes()` aan en sla deze op voor toekomstig gebruik of roep `FMRMSv1MetadataHandler.setUpdatedMetadata()`.

