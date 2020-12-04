---
description: Als u Adobe Primetime DRM Professional gebruikt, kunt u licenties vooraf genereren en licenties insluiten in inhoud. Deze functie kan worden gecombineerd met 'Enhanced License Chaining', zodat een Leaf-licentie vooraf wordt gegenereerd en ingesloten in de inhoud, en de client kan een basislicentie (gebonden aan een computer of domein) aanvragen bij een licentieserver. Als alternatief kunnen clienttoepassingen een workflow implementeren waarbij het apparaat zich vooraf bij een server registreert, de server licenties vooraf genereert die aan dat apparaat zijn gebonden en de client de licenties ophaalt van een eenvoudige HTTP-webserver.
seo-description: Als u Adobe Primetime DRM Professional gebruikt, kunt u licenties vooraf genereren en licenties insluiten in inhoud. Deze functie kan worden gecombineerd met 'Enhanced License Chaining', zodat een Leaf-licentie vooraf wordt gegenereerd en ingesloten in de inhoud, en de client kan een basislicentie (gebonden aan een computer of domein) aanvragen bij een licentieserver. Als alternatief kunnen clienttoepassingen een workflow implementeren waarbij het apparaat zich vooraf bij een server registreert, de server licenties vooraf genereert die aan dat apparaat zijn gebonden en de client de licenties ophaalt van een eenvoudige HTTP-webserver.
seo-title: Vooraf gegenereerde licenties
title: Vooraf gegenereerde licenties
uuid: aa7d5038-5a9b-40a2-a240-266622158b43
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 0%

---


# Vooraf gegenereerde licenties {#pre-generating-licenses}

Als u Adobe Primetime DRM Professional gebruikt, kunt u licenties vooraf genereren en licenties insluiten in inhoud. Deze functie kan worden gecombineerd met &#39;Enhanced License Chaining&#39;, zodat een Leaf-licentie vooraf wordt gegenereerd en ingesloten in de inhoud, en de client kan een basislicentie (gebonden aan een computer of domein) aanvragen bij een licentieserver. Als alternatief kunnen clienttoepassingen een workflow implementeren waarbij het apparaat zich vooraf bij een server registreert, de server licenties vooraf genereert die aan dat apparaat zijn gebonden en de client de licenties ophaalt van een eenvoudige HTTP-webserver.

Als u licenties vooraf wilt genereren, moet u `com.adobe.flashaccess.sdk.license.pregen.LicenseFactory.getInstance()` gebruiken om een exemplaar van `LicenseFactory` te verkrijgen. U moet een licentieserverreferentie opgeven om de licenties die door deze fabriek worden gegenereerd, te ondertekenen. Deze klasse ondersteunt het genereren van Leaf-licenties zonder licentieketting en Leaf- en Root-licenties met de [Enhanced license chaining](../../protecting-content/implementing-the-license-server/license-chaining/gen-enhanced-license-chaining.md).

Wanneer u een Leaf-licentie genereert, moet u de metagegevens voor de inhoud opgeven die `initContentInfo()` van toepassing zijn. Als de metagegevens meerdere DRM-beleidsregels bevatten of als u een DRM-beleid wilt gebruiken dat niet is opgenomen in de metagegevens, moet u `setSelectedPolicy()` gebruiken om het DRM-beleid op te geven voor het genereren van een licentie. Als u een Lijst van de Update van het Beleid DRM gebruikt om updates aan beleid te volgen DRM, kunt u de Lijst van de Update van het Beleid DRM aan de Fabriek van de Vergunning verstrekken alvorens u de meta-gegevens met `setPolicyUpdateList()` initialiseert.

Wanneer u een basislicentie genereert, moet u de metagegevens van de inhoud opgeven zoals hierboven beschreven. U kunt ook een hoofdlicentie genereren door een DRM-beleid ( `setSelectedPolicy()`) en een URL van een licentieserver ( `setLicenseServerURL()`) toe te passen in plaats van metagegevens.

>[!NOTE]
>
>Een licentieserver-URL is vereist, zelfs als er geen Adobe Primetime DRM-licentieserver is waar de clients een licentie kunnen aanvragen. In dat geval moet de URL van de licentieserver een URL opgeven die de uitgever van de licentie identificeert.

Als het DRM-beleid gebruikmaakt van Enhanced License Chaining, moet u een licentieserverreferentie opgeven om de hoofdcoderingssleutel te decoderen in het DRM-beleid ( `setRootKeyRetrievalInfo()`).

Als voor het DRM-beleid een domeingebonden licentie vereist is, moet u `setDomainCAs()` gebruiken om de domeinuitgevers op te geven van waaruit de licentieserver domeintokens accepteert. Één of meerdere certificaten van CA van het Domein moeten worden verstrekt om de vergunningontvanger te bevestigen.

Als voor het DRM-beleid levering via externe sleutels voor iOS-apparaten is vereist, moet u het Key Server-certificaat opgeven door `setKeyServerCertificate()` toe te passen, tenzij een gekoppeld blad wordt gegenereerd.

Als u een licentie wilt genereren, moet u `generateLicense()` aanroepen en het licentietype (Leaf of Root) en een of meer ontvangende certificaten opgeven. Het ontvankelijke certificaat vertegenwoordigt of een machinecertificaat of domeincertificaat, afhankelijk van de vereisten die in het beleid DRM worden gespecificeerd. Als u een kettingblad genereert, is een ontvanger niet vereist. Nadat de licentie is gegenereerd, kunt u de gebruiksregels overschrijven die in het DRM-beleid zijn opgegeven. Tot slot moet u `signLicense()` aanroepen om de licentie te ondertekenen en een instantie van `PreGeneratedLicense` te verkrijgen. De licentie kan nu worden opgeslagen (gebruik `getBytes()` om de geserialiseerde licentie op te halen of om de licentie in gecodeerde inhoud in te sluiten.

Zie [Licenties insluiten](../../protecting-content/pre-generating-and-embedded-licenses/embedding-licenses.md).

Zie `com.adobe.flashaccess.samples.licensegen.GenerateLicense` in de map &quot;samples&quot; in de opdrachtregelprogramma&#39;s voor naslagimplementatie voor voorbeeldcode voor het demonstreren van vooraf gegenereerde licenties.
