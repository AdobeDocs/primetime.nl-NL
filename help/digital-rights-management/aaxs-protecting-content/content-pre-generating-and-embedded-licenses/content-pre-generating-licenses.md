---
seo-title: Vooraf gegenereerde licenties
title: Vooraf gegenereerde licenties
uuid: 31430753-11f1-4ce5-b402-cf4279119a05
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Vooraf gegenereerde licenties{#pre-generating-licenses}

Als u licenties vooraf wilt genereren, moet u `com.adobe.flashaccess.sdk.license.pregen.LicenseFactory.getInstance()` een exemplaar van `LicenseFactory`. U moet een licentieserverreferentie opgeven om de licenties die door deze fabriek worden gegenereerd, te ondertekenen. Deze klasse ondersteunt het genereren van Leaf-licenties zonder licentieketting en Leaf- en Root-licenties met de [Enhanced license chaining](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-other-policy-options/content-enhanced-license-chaining.md).

Wanneer u een Leaf-licentie genereert, moeten de metagegevens voor de inhoud worden opgegeven met behulp van `initContentInfo()`. Als de meta-gegevens veelvoudige beleid omvat, of als u een beleid wilt gebruiken dat niet in de meta-gegevens was, gebruik `setSelectedPolicy()` om het beleid te specificeren om de vergunning te produceren. Als u een Lijst van de Update van het Beleid gebruikt om updates aan beleid te volgen, kunt u de Lijst van de Update van het Beleid aan de Fabriek van de Vergunning verstrekken alvorens de meta-gegevens te initialiseren gebruikend `setPolicyUpdateList()`.

Bij het genereren van een basislicentie kunnen de metagegevens van de inhoud worden opgegeven zoals hierboven beschreven. U kunt ook een hoofdlicentie genereren met een beleid- ( `setSelectedPolicy()`) en licentieserver-URL ( `setLicenseServerURL()`) in plaats van met de metagegevens.

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>Een licentieserver-URL is vereist, zelfs als er geen Adobe Access-licentieserver is waarvan de clients een licentie kunnen aanvragen. In dat geval moet de URL van de licentieserver een URL opgeven die de uitgever van de licentie identificeert.

Als het beleid Verbeterde Vergunning het Ketsen van de Vergunning gebruikt, moet een referentie van de Server van de Vergunning worden gespecificeerd om de Sleutel van de Encryptie van de Wortel in het beleid ( `setRootKeyRetrievalInfo()`) te decrypteren.

Als het beleid een domein gebonden vergunning vereist, gebruik `setDomainCAs()` om de uitgevende instanties van het Domein te specificeren waarvan de vergunningsserver domeintekenen zal goedkeuren. U moet een of meer Domain CA-certificaten opgeven om de licentieontvanger te valideren.

Als voor het beleid levering via externe sleutels voor iOS-apparaten is vereist, moet het Key Server-certificaat worden opgegeven met behulp van `setKeyServerCertificate()`, tenzij een gekoppeld blad wordt gegenereerd.

Als u een licentie wilt genereren, roept u het licentietype (Leaf of Root) en een of meer ontvangers-certificaten op `generateLicense()` en geeft u dit op. Het ontvangende certificaat is een machinecertificaat of een domeincertificaat, afhankelijk van de vereisten die in het beleid zijn opgegeven. Als u een kettingblad genereert, is een ontvanger niet vereist. Nadat de licentie is gegenereerd, is het mogelijk de gebruiksregels te overschrijven die in het beleid zijn opgegeven. Ten slotte roept u `signLicense()` op om de licentie te ondertekenen en een exemplaar van `PreGeneratedLicense`. De licentie kan nu worden opgeslagen in een bestand (gebruiken `getBytes()` om de geserialiseerde licentie op te halen) of in gecodeerde inhoud worden ingesloten. Zie Licenties [insluiten](../../aaxs-protecting-content/content-pre-generating-and-embedded-licenses/content-embedding-licenses.md).

Zie `com.adobe.flashaccess.samples.licensegen.GenerateLicense` in de map &quot;samples&quot; van de opdrachtregelprogramma&#39;s voor naslagimplementatie de voorbeeldcode die vooraf gegenereerde licenties aantoont.
