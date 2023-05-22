---
title: Vooraf gegenereerde licenties
description: Vooraf gegenereerde licenties
copied-description: true
exl-id: 2be8674c-736f-4ed3-b952-f661bf3ff48f
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# Vooraf gegenereerde licenties{#pre-generating-licenses}

Gebruik voor het vooraf genereren van licenties `com.adobe.flashaccess.sdk.license.pregen.LicenseFactory.getInstance()` om een instantie te verkrijgen van `LicenseFactory`. U moet een licentieserverreferentie opgeven om de licenties die door deze fabriek worden gegenereerd, te ondertekenen. Deze klasse ondersteunt het genereren van Leaf-licenties zonder licentieketens en Leaf- en Root-licenties met de [Verbeterde licentietakken](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-other-policy-options/content-enhanced-license-chaining.md).

Bij het genereren van een Leaf-licentie moeten de metagegevens voor de inhoud worden opgegeven met `initContentInfo()`. Als de metagegevens meerdere beleidsregels bevatten of als u een beleid wilt gebruiken dat niet in de metagegevens voorkomt, gebruikt u `setSelectedPolicy()` om het beleid te specificeren dat moet worden gebruikt om de vergunning te produceren. Als u een Lijst van de Update van het Beleid gebruikt om updates aan beleid te volgen, kunt u de Lijst van de Update van het Beleid aan de Fabriek van de Vergunning verstrekken alvorens de meta-gegevens te initialiseren gebruikend `setPolicyUpdateList()`.

Bij het genereren van een basislicentie kunnen de metagegevens van de inhoud worden opgegeven zoals hierboven beschreven. Een basislicentie kan ook worden gegenereerd met behulp van een beleid ( `setSelectedPolicy()`) en de licentieserver-URL ( `setLicenseServerURL()`) in plaats van de metagegevens.

>[!NOTE]
>
>Een licentieserver-URL is vereist, zelfs als er geen Adobe Access-licentieserver is waarvan de clients een licentie kunnen aanvragen. In dat geval moet de URL van de licentieserver een URL opgeven die de uitgever van de licentie identificeert.

Als het beleid Verbeterde het Ketsen van de Vergunning gebruikt, moet een referentie van de Server van de Vergunning worden gespecificeerd om de Sleutel van de Encryptie van de Wortel in het beleid te decrypteren ( `setRootKeyRetrievalInfo()`).

Als het beleid een domein gebonden vergunning vereist, gebruik `setDomainCAs()` om de Uitgevers van het Domein te specificeren waarvan de vergunningsserver domeintokens zal goedkeuren. U moet een of meer Domain CA-certificaten opgeven om de licentieontvanger te valideren.

Als voor het beleid levering via externe sleutels is vereist voor iOS-apparaten, moet het Key Server Certificate worden geleverd met `setKeyServerCertificate()`, tenzij er een geketend blad wordt gegenereerd.

Als u een licentie wilt genereren, roept u `generateLicense()` en geeft u het type vergunning (Leaf of Root) en een of meer ontvangende certificaten op. Het ontvangende certificaat is een machinecertificaat of een domeincertificaat, afhankelijk van de vereisten die in het beleid zijn opgegeven. Als u een kettingblad genereert, is een ontvanger niet vereist. Nadat de licentie is gegenereerd, is het mogelijk de gebruiksregels te overschrijven die in het beleid zijn opgegeven. Tot slot roepen `signLicense()` om de licentie te ondertekenen en een instantie te verkrijgen van `PreGeneratedLicense`. De licentie kan nu worden opgeslagen in een bestand (gebruik `getBytes()` om de geserialiseerde licentie op te halen) of ingesloten in gecodeerde inhoud. Zie, [Licenties insluiten](../../aaxs-protecting-content/content-pre-generating-and-embedded-licenses/content-embedding-licenses.md).

Voor voorbeeldcode die vooraf gegenereerde licenties aantoont, raadpleegt u `com.adobe.flashaccess.samples.licensegen.GenerateLicense` in de map &quot;samples&quot; van de opdrachtregelprogramma&#39;s van de naslagimplementatie.
