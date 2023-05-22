---
description: Als u Adobe Primetime DRM Professional gebruikt, kunt u licenties vooraf genereren en licenties insluiten in inhoud. Deze functie kan worden gecombineerd met 'Enhanced License Chaining', zodat een Leaf-licentie vooraf wordt gegenereerd en ingesloten in de inhoud, en de client kan een basislicentie (gebonden aan een computer of domein) aanvragen bij een licentieserver. Als alternatief kunnen clienttoepassingen een workflow implementeren waarbij het apparaat zich vooraf bij een server registreert, de server licenties vooraf genereert die aan dat apparaat zijn gebonden en de client de licenties ophaalt van een eenvoudige HTTP-webserver.
title: Vooraf gegenereerde licenties
exl-id: 6ced7dde-b4bb-470d-bdae-3042f5577b67
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '611'
ht-degree: 0%

---

# Vooraf gegenereerde licenties {#pre-generating-licenses}

Als u Adobe Primetime DRM Professional gebruikt, kunt u licenties vooraf genereren en licenties insluiten in inhoud. Deze functie kan worden gecombineerd met &#39;Enhanced License Chaining&#39;, zodat een Leaf-licentie vooraf wordt gegenereerd en ingesloten in de inhoud, en de client kan een basislicentie (gebonden aan een computer of domein) aanvragen bij een licentieserver. Als alternatief kunnen clienttoepassingen een workflow implementeren waarbij het apparaat zich vooraf bij een server registreert, de server licenties vooraf genereert die aan dat apparaat zijn gebonden en de client de licenties ophaalt van een eenvoudige HTTP-webserver.

Als u licenties vooraf wilt genereren, moet u `com.adobe.flashaccess.sdk.license.pregen.LicenseFactory.getInstance()` om een instantie te verkrijgen van `LicenseFactory`. U moet een licentieserverreferentie opgeven om de licenties die door deze fabriek worden gegenereerd, te ondertekenen. Deze klasse ondersteunt het genereren van Leaf-licenties zonder licentieketens en Leaf- en Root-licenties met de [Verbeterde licentietakken](../../protecting-content/implementing-the-license-server/license-chaining/gen-enhanced-license-chaining.md).

Wanneer u een Leaf-licentie genereert, moet u de metagegevens voor de inhoud opgeven die van toepassing zijn `initContentInfo()`. Als de metagegevens meerdere DRM-beleidsregels bevatten of als u een DRM-beleid wilt gebruiken dat niet is opgenomen in de metagegevens, moet u `setSelectedPolicy()` om het DRM-beleid voor het genereren van een licentie op te geven. Als u een lijst van de Update van het Beleid DRM gebruikt om updates aan beleid te volgen DRM, kunt u de Lijst van de Update van het Beleid DRM aan de Fabriek van de Vergunning verstrekken alvorens u de meta-gegevens met initialiseert `setPolicyUpdateList()`.

Wanneer u een basislicentie genereert, moet u de metagegevens van de inhoud opgeven zoals hierboven beschreven. U kunt ook een basislicentie genereren door een DRM-beleid toe te passen ( `setSelectedPolicy()`) en een licentieserver-URL ( `setLicenseServerURL()`) in plaats van metagegevens.

>[!NOTE]
>
>Een licentieserver-URL is vereist, zelfs als er geen Adobe Primetime DRM-licentieserver is waar de clients een licentie kunnen aanvragen. In dat geval moet de URL van de licentieserver een URL opgeven die de uitgever van de licentie identificeert.

Als het DRM-beleid gebruikmaakt van Enhanced License Chaining, moet u een licentieserverreferentie opgeven om de hoofdcoderingssleutel te decoderen in het DRM-beleid ( `setRootKeyRetrievalInfo()`).

Als het DRM-beleid een domeingebonden licentie vereist, moet u `setDomainCAs()` om de Uitgevers van het Domein te specificeren waarvan de vergunningsserver domeintokens goedkeurt. Één of meerdere certificaten van CA van het Domein moeten worden verstrekt om de vergunningontvanger te bevestigen.

Als voor het DRM-beleid levering via een externe sleutel is vereist voor iOS-apparaten, moet u het Key Server-certificaat opgeven door het toepassen `setKeyServerCertificate()` tenzij een geketend blad wordt gegenereerd.

Als u een licentie wilt genereren, moet u deze aanroepen `generateLicense()` en geeft u het type vergunning (Leaf of Root) en een of meer ontvangende certificaten op. Het ontvankelijke certificaat vertegenwoordigt of een machinecertificaat of domeincertificaat, afhankelijk van de vereisten die in het beleid DRM worden gespecificeerd. Als u een kettingblad genereert, is een ontvanger niet vereist. Nadat de licentie is gegenereerd, kunt u de gebruiksregels overschrijven die in het DRM-beleid zijn opgegeven. Tot slot moet u roepen `signLicense()` om de licentie te ondertekenen en een instantie te verkrijgen van `PreGeneratedLicense`. De licentie kan nu worden opgeslagen (gebruik `getBytes()` om de geserialiseerde licentie op te halen of in gecodeerde inhoud in te sluiten.

Zie [Licenties insluiten](../../protecting-content/pre-generating-and-embedded-licenses/embedding-licenses.md).

Zie `com.adobe.flashaccess.samples.licensegen.GenerateLicense` in de map &quot;samples&quot; van de opdrachtregelprogramma&#39;s van de naslagimplementatie voor voorbeeldcode voor het demonstreren van vooraf gegenereerde licenties.
