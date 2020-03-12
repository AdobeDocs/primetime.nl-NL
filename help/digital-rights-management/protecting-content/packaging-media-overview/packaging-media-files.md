---
seo-title: Overzicht van mediabestanden verpakken
title: Overzicht van mediabestanden verpakken
uuid: 9509bcdc-ee4d-4025-9bb6-9b8ac439b926
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# Overzicht {#packaging-media-files-overview}

Het verpakken verwijst naar het proces om een beleid DRM op videoinhoud te coderen en toe te passen. U kunt de API&#39;s voor het verpakken van media gebruiken om bestanden te verpakken. De Primetime DRM Java SDK kan alleen inhoud die progressief kan worden gedownload, zoals MP4, in een pakket opnemen.

>[!NOTE]
>
>Neem contact op met uw vertegenwoordiger van Primetime DRM voor informatie over de manier waarop u de meest geschikte verpakkingsoptie voor uw media-indeling en gebruiksscenario&#39;s kunt selecteren.

Het verpakken wordt losgekoppeld van de licentieserver. Het is niet nodig dat de pakketsoftware verbinding maakt met de licentieserver om informatie over de inhoud uit te wisselen. Alles wat de licentieserver moet weten om een licentie uit te geven, is opgenomen in de metagegevens van de inhoud.

Wanneer een bestand is versleuteld, kan de inhoud ervan niet worden geparseerd zonder de juiste licentie. U kunt Primetime DRM gebruiken om de delen van het dossier te selecteren die u wilt coderen. Omdat Primetime DRM de bestandsindeling van de video-inhoud kan parseren, kan hiermee op intelligente wijze selectieve delen van een bestand worden gecodeerd in plaats van een volledig bestand. Gegevens, zoals metagegevens en actiepunten, kunnen niet gecodeerd blijven, zodat zoekmachines nog steeds in het bestand kunnen zoeken.

Een bepaald stuk inhoud kan meerdere DRM-beleidsregels hebben. U kunt bijvoorbeeld inhoud in licentie geven onder verschillende bedrijfsmodellen zonder dat u de inhoud meerdere keren in een pakket hoeft te plaatsen. Bovendien kunt u anonieme toegang voor een korte periode toestaan en de klant toestaan de inhoud te kopen om onbeperkte toegang te hebben. Als de inhoud wordt verpakt door veelvoudige beleid te gebruiken DRM, moet de Server van de Vergunning logica uitvoeren voor het selecteren van welk beleid DRM moet worden gebruikt om een vergunning uit te geven.

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>De architectuur staat voor gebruikDRM beleid toe om aan inhoud worden gespecificeerd en worden gebonden wanneer de inhoud wordt verpakt. Voordat een client inhoud kan afspelen, moet de client een licentie voor een opgegeven computer aanschaffen. De vergunning specificeert de gebruiksregels die worden afgedwongen en verstrekt de sleutel die moet worden gebruikt om inhoud te decrypteren. Het DRM-beleid vertegenwoordigt een sjabloon voor het genereren van een licentie. De licentieserver kan echter de gebruiksregels overschrijven wanneer deze een licentie uitgeeft. De licentie kan door dergelijke beperkingen, zoals vervaltijden of afspeelvensters, ongeldig worden gemaakt.

Primetime DRM biedt een API voor het doorgeven in de CEK. Als er geen CEK is opgegeven, genereert de SDK deze willekeurig. Gewoonlijk hebt u voor elke sectie van inhoud een andere CEK nodig. In Dynamic Streaming zult u echter waarschijnlijk dezelfde CEK gebruiken voor alle bestanden waaruit die inhoud bestaat. Daarom heeft een gebruiker slechts één licentie nodig om naadloos over te schakelen van de ene bitsnelheid naar de andere. Als u dezelfde sleutel en licentie voor meerdere inhoud wilt gebruiken, moet u hetzelfde `DRMParameters` object doorgeven aan `MediaEncrypter.encryptContent()`of de CEK doorgeven met `V2KeyParameters.setContentEncryptionKey()`. Als u voor elke sectie van inhoud een andere sleutel en licentie wilt gebruiken, moet u voor elk bestand een nieuwe `DRMParameters` instantie maken.

Wanneer u inhoud verpakt met behulp van toetsrotatie, kunt u de gebruikte rotatietoetsen en de frequentie waarmee de toetsen worden gewijzigd instellen. `F4VDRMParameters` en `FLVDRMParameters` implementeert de `KeyRotationParameters` interface. Via deze interface kunt u sleutelrotatie inschakelen. U moet ook een `RotatingContentEncryptionKeyProvider`bestand opgeven. Voor elke gecodeerde steekproef, bepaalt deze klasse de Sleutel van de Omwenteling aan gebruik. U kunt uw eigen provider implementeren of de `TimeBasedKeyProvider` bij de SDK geleverde software gebruiken. Deze implementatie genereert op willekeurige wijze een nieuwe sleutel na een opgegeven aantal seconden.

In sommige gevallen moet u de metagegevens van de inhoud mogelijk als een afzonderlijk bestand opslaan en beschikbaar maken voor de client, apart van de inhoud. In dat geval moet u een aanroep uitvoeren `MediaEncrypter.encryptContent()`, die een `MediaEncrypterResult` object retourneert. Roep het resultaat aan `MediaEncrypterResult.getKeyInfo()` en giet het resultaat aan `V2KeyStatus`. Vervolgens haalt u de metagegevens van de inhoud op en slaat u deze op in een bestand.

Al deze taken kunnen worden uitgevoerd met de Java API.

Zie *Adobe Primetime DRM API Reference* voor meer informatie over de Java API.

Zie *De Adobe Primetime DRM Reference Implementations* gebruiken voor informatie over de implementatie van de Media Packager-referentie.
