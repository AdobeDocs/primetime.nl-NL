---
title: Overzicht
description: Overzicht
copied-description: true
exl-id: 67c3d98f-8c17-4b5a-8abb-00f6f0f1e823
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '867'
ht-degree: 0%

---

# Overzicht {#overview}

*Verpakken* verwijst naar het coderen en toepassen van een beleid op FLV- of F4V-bestanden. Gebruik de API&#39;s voor het verpakken van media om bestanden te verpakken. De Adobe Access Java SDK kan alleen Flash- en AIR-inhoud van progressieve download, zoals FLV, F4V en MP4, in een pakket plaatsen. Als u inhoud wilt verpakken met Adobe Access DRM voor andere inhoudsindelingen, zoals Adobe HTTP Dynamic Streaming (HDS) of Apple HTTP Live Streaming (HLS), moet u andere gereedschappen gebruiken, zoals Adobe Media Server ( [https://www.adobe.com/products/adobe-media-server-family.html](https://www.adobe.com/products/adobe-media-server-family.html)) of een codeerprogramma dat de Adobe Broadcast-SDK implementeert ( [https://help.adobe.com/en_US/primetime/packagers/hdkb_api_overview_3.5.pdf](https://help.adobe.com/en_US/primetime/packagers/hdkb_api_overview_3.5.pdf)). Alternatief, hebben de klanten de keus om toolset van Java Primetime Packager te gebruiken, die inhoud voor een verscheidenheid van doelformaten zoals HDS, HLS, en DASH kan verpakken.

Het verpakken wordt losgekoppeld van de licentieserver. Het is niet nodig dat de pakketsoftware verbinding maakt met de licentieserver om informatie over de inhoud uit te wisselen. Alles wat de licentieserver moet weten om de licentie uit te geven, is opgenomen in de metagegevens van de inhoud.

Wanneer een bestand is versleuteld, kan de inhoud ervan niet worden geparseerd zonder de juiste licentie. Met Adobe Access kunt u selecteren welke delen van het bestand u wilt versleutelen. Omdat Adobe® Access™ de bestandsindeling van de FLV- en F4V-inhoud kan parseren, kan hiermee op intelligente wijze selectieve delen van het bestand worden gecodeerd in plaats van het gehele bestand. Gegevens zoals metagegevens en actiepunten kunnen niet gecodeerd blijven, zodat zoekfuncties het bestand nog steeds kunnen doorzoeken.

Het is mogelijk dat een bepaalde inhoud meerdere beleidsvormen heeft. Dit kan bijvoorbeeld handig zijn als u inhoud wilt licentiëren in verschillende bedrijfsmodellen zonder dat u de inhoud meerdere keren moet verpakken. U kunt bijvoorbeeld anonieme toegang voor een korte periode toestaan en daarna de klant toestaan de inhoud te kopen en onbeperkte toegang te hebben. Als de inhoud wordt verpakt gebruikend veelvoudige beleid, moet de Server van de Vergunning logica voor het selecteren van welk beleid uitvoeren om een vergunning uit te geven.

>[!NOTE]
>
>De architectuur staat voor gebruiksbeleid toe om aan inhoud worden gespecificeerd en worden gebonden wanneer de inhoud wordt verpakt. Voordat een client inhoud kan afspelen, moet de client een licentie voor die computer aanschaffen. De vergunning specificeert de gebruiksregels die worden afgedwongen en verstrekt de sleutel die wordt gebruikt om de inhoud te decrypteren. Het beleid is een sjabloon voor het genereren van de licentie, maar de licentieserver kan ervoor kiezen de gebruiksregels te overschrijven bij het uitgeven van de licentie. Merk op dat de licentie ongeldig kan worden gemaakt door beperkingen zoals vervaltijden of afspeelvensters.

Er zijn talrijke opties beschikbaar voor het verpakken van inhoud. Deze worden gespecificeerd in `DRMParameters` interface en de klassen die die interface uitvoeren, die zijn `F4VDRMParameters` en `FLVDRMParameters`. Met deze klassen kunt u parameters voor handtekening en sleutel instellen en aangeven of audio-inhoud, video-inhoud of scriptgegevens moeten worden gecodeerd. Om te zien hoe deze in de verwijzingsimplementatie worden uitgevoerd, zie de beschrijvingen van de opties van de het bevellijn van Media Packager in *Implementaties van de Adobe Access-naslaggids gebruiken*. Deze opties zijn gebaseerd op de Java API en zijn daarom beschikbaar voor programmatisch gebruik.

De volgende verpakkingsopties zijn beschikbaar:

* Coderingsopties (audio, video, gedeeltelijke codering).
* De server-URL van de vergunning (de cliënt gebruikt dit als basis URL voor alle verzoeken die naar de vergunningsserver worden verzonden)
* Certificaat van licentieservertransport
* Certificaat van licentieserver, gebruikt om de CEK te coderen.
* Packager-referentie voor het ondertekenen van metagegevens

Adobe Access biedt een API voor het doorgeven in de CEK. Als er geen CEK is opgegeven, genereert de SDK deze willekeurig. Doorgaans hebt u voor elk stuk inhoud een andere CEK nodig. In Dynamic Streaming zou u echter waarschijnlijk dezelfde CEK gebruiken voor alle bestanden voor die inhoud. De gebruiker heeft dus slechts één licentie nodig en kan naadloos overschakelen van de ene bitsnelheid naar de andere. Als u dezelfde sleutel en licentie voor meerdere inhoud wilt gebruiken, geeft u hetzelfde door `DRMParameters` object naar `MediaEncrypter.encryptContent()`, of pas de CEK in gebruikend `V2KeyParameters.setContentEncryptionKey()`. Als u voor elk stuk inhoud een andere sleutel en licentie wilt gebruiken, maakt u een nieuwe `DRMParameters` -instantie voor elk bestand.

Wanneer u inhoud verpakt met behulp van toetsrotatie, kunt u bepalen welke rotatietoetsen worden gebruikt en hoe vaak de toetsen veranderen. `F4VDRMParameters` en `FLVDRMParameters` de `KeyRotationParameters` interface. Via deze interface kunt u sleutelrotatie inschakelen. U moet ook een `RotatingContentEncryptionKeyProvider`. Voor elke gecodeerde steekproef, bepaalt deze klasse de Sleutel van de Omwenteling te gebruiken. U kunt uw eigen provider implementeren of de `TimeBasedKeyProvider` opgenomen in de SDK. Deze implementatie genereert op willekeurige wijze een nieuwe sleutel na een opgegeven aantal seconden.

In sommige gevallen moet u de metagegevens van de inhoud mogelijk opslaan als een afzonderlijk bestand en deze afzonderlijk van de inhoud beschikbaar stellen aan de client. Om dit te doen, roep `MediaEncrypter.encryptContent()`, die een `MediaEncrypterResult` object. Bellen `MediaEncrypterResult.getKeyInfo()` en het resultaat naar `V2KeyStatus`. Vervolgens haalt u de metagegevens van de inhoud op en slaat u deze op in een bestand.

Al deze taken kunnen worden uitgevoerd met de Java API. Zie voor meer informatie over de Java API die in dit hoofdstuk wordt besproken *Referentie voor Adobe Access API*.

Voor informatie over de de verwijzingsimplementatie van Media Packager, zie *Implementaties van de Adobe Access-naslaggids gebruiken*.
