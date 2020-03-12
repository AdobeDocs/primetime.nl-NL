---
seo-title: Overzicht
title: Overzicht
uuid: 11cf1f1f-a4b2-4ac2-aae7-e925d96729d2
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Overzicht {#overview}

*Verpakken* verwijst naar het coderen en toepassen van een beleid op FLV- of F4V-bestanden. Gebruik de API&#39;s voor het verpakken van media om bestanden te verpakken. De Adobe Access Java SDK kan alleen Flash- en AIR-inhoud met progressieve download, zoals FLV, F4V en MP4, in een pakket plaatsen. Als u inhoud met Adobe Access DRM wilt verpakken voor andere inhoudsindelingen, zoals Adobe HTTP Dynamic Streaming (HDS) of Apple HTTP Live Streaming (HLS), moet u andere gereedschappen gebruiken, zoals Adobe Media Server ( [https://www.adobe.com/products/adobe-media-server-family.html](https://www.adobe.com/products/adobe-media-server-family.html)) of een codeermodule die de Adobe Broadcast SDK ( [https://help.adobe.com/en_US/primetime/packagers/hdkb_api_overview_3.5.pdf](https://help.adobe.com/en_US/primetime/packagers/hdkb_api_overview_3.5.pdf)) implementeert. Klanten kunnen ook de Java Primetime Packager-toolset van Adobe gebruiken, waarmee inhoud kan worden verpakt voor verschillende doelindelingen, zoals HDS, HLS en DASH.

Het verpakken wordt losgekoppeld van de licentieserver. Het is niet nodig dat de pakketsoftware verbinding maakt met de licentieserver om informatie over de inhoud uit te wisselen. Alles wat de licentieserver moet weten om de licentie uit te geven, is opgenomen in de metagegevens van de inhoud.

Wanneer een bestand is versleuteld, kan de inhoud ervan niet worden geparseerd zonder de juiste licentie. Met Adobe Access kunt u selecteren welke delen van het bestand u wilt versleutelen. Omdat Adobe® Access™ de bestandsindeling van de FLV- en F4V-inhoud kan parseren, kan hiermee op intelligente wijze selectieve delen van het bestand worden gecodeerd in plaats van het gehele bestand. Gegevens zoals metagegevens en actiepunten kunnen niet gecodeerd blijven, zodat zoekfuncties het bestand nog steeds kunnen doorzoeken.

Het is mogelijk dat een bepaalde inhoud meerdere beleidsvormen heeft. Dit kan bijvoorbeeld handig zijn als u inhoud wilt licentiëren in verschillende bedrijfsmodellen zonder dat u de inhoud meerdere keren moet verpakken. U kunt bijvoorbeeld anonieme toegang voor een korte periode toestaan en daarna de klant toestaan de inhoud te kopen en onbeperkte toegang te hebben. Als de inhoud wordt verpakt gebruikend veelvoudige beleid, moet de Server van de Vergunning logica voor het selecteren van welk beleid uitvoeren om een vergunning uit te geven.

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>De architectuur staat voor gebruiksbeleid toe om aan inhoud worden gespecificeerd en worden gebonden wanneer de inhoud wordt verpakt. Voordat een client inhoud kan afspelen, moet de client een licentie voor die computer aanschaffen. De vergunning specificeert de gebruiksregels die worden afgedwongen en verstrekt de sleutel die wordt gebruikt om de inhoud te decrypteren. Het beleid is een sjabloon voor het genereren van de licentie, maar de licentieserver kan ervoor kiezen de gebruiksregels te overschrijven bij het uitgeven van de licentie. Merk op dat de licentie ongeldig kan worden gemaakt door beperkingen zoals vervaltijden of afspeelvensters.

Er zijn talrijke opties beschikbaar voor het verpakken van inhoud. Deze worden gespecificeerd in de `DRMParameters` interface en de klassen die die interface uitvoeren, die `F4VDRMParameters` en `FLVDRMParameters`zijn. Met deze klassen kunt u parameters voor handtekening en sleutel instellen en aangeven of audio-inhoud, video-inhoud of scriptgegevens moeten worden gecodeerd. Zie de beschrijvingen van de opties voor de opdrachtregel van Media Packager die zijn besproken in *Werken met de Adobe Access-naslagimplementaties* voor informatie over hoe deze in de voorbeeldimplementatie worden geïmplementeerd. Deze opties zijn gebaseerd op de Java API en zijn daarom beschikbaar voor programmatisch gebruik.

De volgende verpakkingsopties zijn beschikbaar:

* Coderingsopties (audio, video, gedeeltelijke codering).
* De server-URL van de vergunning (de cliënt gebruikt dit als basis URL voor alle verzoeken die naar de vergunningsserver worden verzonden)
* Certificaat van licentieservertransport
* Certificaat van licentieserver, gebruikt om de CEK te coderen.
* Packager-referentie voor het ondertekenen van metagegevens

Adobe Access biedt een API voor het doorgeven in de CEK. Als er geen CEK is opgegeven, genereert de SDK deze willekeurig. Doorgaans hebt u voor elk stuk inhoud een andere CEK nodig. In Dynamic Streaming zou u echter waarschijnlijk dezelfde CEK gebruiken voor alle bestanden voor die inhoud. De gebruiker heeft dus slechts één licentie nodig en kan naadloos overschakelen van de ene bitsnelheid naar de andere. Als u dezelfde sleutel en licentie voor meerdere inhoud wilt gebruiken, geeft u hetzelfde `DRMParameters` object door aan `MediaEncrypter.encryptContent()`of geeft u de CEK door met `V2KeyParameters.setContentEncryptionKey()`. Als u voor elk stuk inhoud een andere sleutel en licentie wilt gebruiken, maakt u voor elk bestand een nieuwe `DRMParameters` instantie.

Wanneer u inhoud verpakt met behulp van toetsrotatie, kunt u bepalen welke rotatietoetsen worden gebruikt en hoe vaak de toetsen veranderen. `F4VDRMParameters` en `FLVDRMParameters` implementeert de `KeyRotationParameters` interface. Via deze interface kunt u sleutelrotatie inschakelen. U moet ook een `RotatingContentEncryptionKeyProvider`bestand opgeven. Voor elke gecodeerde steekproef, bepaalt deze klasse de Sleutel van de Omwenteling aan gebruik. U kunt uw eigen provider implementeren of de `TimeBasedKeyProvider` bij de SDK geleverde software gebruiken. Deze implementatie genereert op willekeurige wijze een nieuwe sleutel na een opgegeven aantal seconden.

In sommige gevallen moet u de metagegevens van de inhoud mogelijk als een afzonderlijk bestand opslaan en beschikbaar maken voor de client, apart van de inhoud. Hiervoor activeert u `MediaEncrypter.encryptContent()`de methode, die een `MediaEncrypterResult` object retourneert. Roep het resultaat aan `MediaEncrypterResult.getKeyInfo()` en giet het resultaat aan `V2KeyStatus`. Vervolgens haalt u de metagegevens van de inhoud op en slaat u deze op in een bestand.

Al deze taken kunnen worden uitgevoerd met de Java API. Zie *Adobe Access API Reference* voor meer informatie over de Java API die in dit hoofdstuk wordt besproken.

Voor informatie over de de verwijzingsimplementatie van Media Packager, zie het *Gebruiken van de Implementaties* van de Verwijzing van de Toegang van Adobe.
