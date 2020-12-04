---
seo-title: Vooraf gegenereerde licenties
title: Vooraf gegenereerde licenties
uuid: 31430753-11f1-4ce5-b402-cf4279119a05
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---


# Vooraf gegenereerde licenties{#pre-generating-licenses}

Als u licenties vooraf wilt genereren, gebruikt u `com.adobe.flashaccess.sdk.license.pregen.LicenseFactory.getInstance()` om een exemplaar van `LicenseFactory` te verkrijgen. U moet een licentieserverreferentie opgeven om de licenties die door deze fabriek worden gegenereerd, te ondertekenen. Deze klasse ondersteunt het genereren van Leaf-licenties zonder licentieketting en Leaf- en Root-licenties met de [Enhanced license chaining](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-other-policy-options/content-enhanced-license-chaining.md).

Bij het genereren van een Leaf-licentie moeten de metagegevens voor de inhoud worden opgegeven met `initContentInfo()`. Als de meta-gegevens veelvoudige beleid omvat, of als u een beleid wilt gebruiken dat niet in de meta-gegevens was, gebruik `setSelectedPolicy()` om het beleid te specificeren om de vergunning te gebruiken te produceren. Als u een Lijst van de Update van het Beleid gebruikt om updates aan beleid te volgen, kunt u de Lijst van de Update van het Beleid aan de Fabriek van de Vergunning verstrekken alvorens de meta-gegevens te initialiseren gebruikend `setPolicyUpdateList()`.

Bij het genereren van een basislicentie kunnen de metagegevens van de inhoud worden opgegeven zoals hierboven beschreven. U kunt ook een hoofdlicentie genereren met een beleid ( `setSelectedPolicy()`) en een licentieserver-URL ( `setLicenseServerURL()`) in plaats van met de metagegevens.

>[!NOTE]
>
>Een licentieserver-URL is vereist, zelfs als er geen Adobe Access-licentieserver is waarvan de clients een licentie kunnen aanvragen. In dat geval moet de URL van de licentieserver een URL opgeven die de uitgever van de licentie identificeert.

Als het beleid Verbeterde Vergunning het Ketsen van de Vergunning gebruikt, moet een referentie van de Server van de Vergunning worden gespecificeerd om de Sleutel van de Encryptie van de Wortel in het beleid ( `setRootKeyRetrievalInfo()`) te decrypteren.

Als het beleid een domein gebonden vergunning vereist, gebruik `setDomainCAs()` om de uitgevende instanties van het Domein te specificeren waarvan de vergunningsserver domeintekenen zal goedkeuren. U moet een of meer Domain CA-certificaten opgeven om de licentieontvanger te valideren.

Als voor het beleid levering via externe sleutels is vereist voor iOS-apparaten, moet het Key Server-certificaat worden geleverd met `setKeyServerCertificate()`, tenzij een kettingblad wordt gegenereerd.

Als u een licentie wilt genereren, roept u `generateLicense()` aan en geeft u het licentietype (Leaf of Root) en een of meer ontvangers-certificaten op. Het ontvangende certificaat is een machinecertificaat of een domeincertificaat, afhankelijk van de vereisten die in het beleid zijn opgegeven. Als u een kettingblad genereert, is een ontvanger niet vereist. Nadat de licentie is gegenereerd, is het mogelijk de gebruiksregels te overschrijven die in het beleid zijn opgegeven. Ten slotte moet u `signLicense()` aanroepen om de licentie te ondertekenen en een instantie van `PreGeneratedLicense` te verkrijgen. De licentie kan nu worden opgeslagen in een bestand (gebruik `getBytes()` om de geserialiseerde licentie op te halen) of worden ingesloten in gecodeerde inhoud. Zie [Licenties insluiten](../../aaxs-protecting-content/content-pre-generating-and-embedded-licenses/content-embedding-licenses.md).

Zie `com.adobe.flashaccess.samples.licensegen.GenerateLicense` in de map &quot;samples&quot; van de opdrachtregelprogramma&#39;s voor naslagimplementatie voor voorbeeldcode die vooraf gegenereerde licenties aantoont.
