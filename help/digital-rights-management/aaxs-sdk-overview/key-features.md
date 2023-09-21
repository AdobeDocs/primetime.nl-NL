---
title: Belangrijkste kenmerken
description: Belangrijkste kenmerken
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1146'
ht-degree: 0%

---

# Belangrijkste kenmerken {#key-features}

De Toegang van de Adobe verstrekt deze zeer belangrijke eigenschappen:

* **Ondersteuning voor HLS-streaming (vereist Adobe Primetime):** Gebruik Adobe Access DRM met HLS-inhoud die kan worden gestreamd naar elk platform dat wordt ondersteund door Flash of Adobe Primetime (zoals Desktop, iOS en Android).
* **Systeemeigen iOS-toepassingsondersteuning (vereist Adobe Primetime):** Gebruik Adobe Access DRM om video in uw iOS-toepassingen te beveiligen.
* **Systeemeigen ondersteuning voor Android-toepassingen (vereist Adobe Primetime):** Gebruik Adobe Access DRM om video in uw Android-toepassingen te beveiligen.
* **Beveiligde streaming op Xbox (vereist Adobe Primetime)**.
* **IOS-sleutellevering op afstand (Adobe Primetime vereist):** Ondersteuning voor het leveren van externe iOS-sleutels via een sleutelserver met meerdere gebruikers, de zogenaamde Adobe Access Key Server.
* **Bescherming van permanente inhoud:** De inhoud blijft in de hele distributieketen beschermd. Als de inhoud eenmaal is verpakt, blijft deze altijd beveiligd en worden delen ervan alleen op het moment van afspelen en in overeenstemming met de gebruiksregels gedecodeerd.
* Omdat de inhoud is verpakt met gebruiksregels en licentiegegevens, reist de beveiliging altijd met de inhoud. Als consumenten zonder licentie de inhoud proberen af te spelen, leidt het beleid dat in de inhoud is ingesloten hen om, zodat zij een geldige licentie voor de inhoud kunnen verkrijgen.
* **Beveiligd afspelen van beveiligde inhoud: **Bewezen coderingsschema&#39;s worden gebruikt om inhoud te beschermen tegen onbevoegd afspelen.
* **Flexibele gebruiksregels:** Gebruiksregels bepalen hoe consumenten beveiligde inhoud kunnen gebruiken. De gebruiksregels die door de Toegang van de Adobe worden gesteund staan voor verscheidene verschillende bedrijfsmodellen, met inbegrip van loon-per-mening, filmhuur, abonnementen, of de gecofinancierde diensten toe. De gebruiksregels worden gespecificeerd door het beleid u in de inhoud tijdens verpakking inbedt, of kunnen door de Server van de Vergunning tijdens vergunningsverwerving worden gespecificeerd.
* **Uitvoerbeveiliging:** Uitvoerbeveiligingscontroles kunnen worden gebruikt om beschermingsregelingen aan te gaan zoals HDCP, CGMS-A of Rovi (voorheen Macrovision) ACS. Dit kan de uitvoer van inhoud via digitale (bijvoorbeeld HDMI, DVI en UDI) en analoge (bijvoorbeeld S-Video en Component Video) uitvoer helpen beschermen.

  U kunt uitvoerbeveiligingsopties opgeven in het beleid dat u voor uw inhoud maakt, zodat toegang tot inhoud wordt toegestaan of geweigerd op basis van de uitvoerbeveiligingsmogelijkheden van een apparaat. U kunt bijvoorbeeld opgeven dat uitvoerbeveiliging niet vereist is voor bepaalde inhoud, maar dat uitvoerbeveiliging vereist is voor hoogwaardige video-inhoud. Zo voorkomt u dat inhoud wordt uitgevoerd op besturingssystemen die deze mogelijkheid niet hebben.

  Hoewel deze regels op alle platforms consistent worden toegepast, is het momenteel alleen mogelijk om uitvoerbeveiliging op Windows-platforms veilig in te schakelen.

* **Ondersteuning voor dynamische streaming: **Gebruik de functie voor dynamische streaming van Flash Media Server of Adobe HTTP Dynamic Streaming om inhoud die met meerdere bitsnelheden is gecodeerd, te beschermen. Dynamische streaming maakt gebruik van een videostream die de bitsnelheid en de afspeelkwaliteit dynamisch aanpast op basis van de beschikbare bandbreedte, waardoor de gebruiker een betere beleving krijgt. Met Toegang tot Adobe kunt u dezelfde coderingssleutel en licentie voor inhoud gebruiken voor de verschillende coderingen van hetzelfde element.
* **Offlineweergave:** Met de Adobe AIR-runtimeclient kunnen consumenten inhoud downloaden en opslaan om deze later weer te geven, ongeacht of de computer nog steeds verbonden is met internet.
* **Licenties op basis van identiteit:** Koppelt machtigingen aan gebruikersidentiteiten, waarbij de consument zichzelf moet verifiëren (met een gebruikersnaam en wachtwoord) om toegang te krijgen tot inhoud. Voor op identiteit gebaseerde licenties moet de partij die de clienttoepassing ontwikkelt gebruikersverificatie implementeren als onderdeel van de workflow voor het aanschaffen van licenties.
* **Licentieketting:** Hiermee kunnen consumenten de levensduur van al hun inhoud verlengen door een enkele basislicentie te vernieuwen. Een van de belangrijkste toepassingen van licentietekeningen is voor bedrijfsmodellen op basis van abonnementen, waarbij aan het einde van een abonnementsperiode licenties voor grote aantallen inhoudsbestanden kunnen worden vernieuwd door gewoon de hoofdlicentie te vernieuwen.

  Zowel basis- als bladlicenties zijn gebonden aan de computer van de consument. De bladlicentie bevat de CEK en een verwijzing naar de hoofdlicentie. De hoofdlicentie kan de rechten uitbreiden die in de bladlicentie zijn verleend. Een consument kan bijvoorbeeld bladlicenties hebben voor 50 stukken inhoud die aan het einde van een bepaalde abonnementsperiode verlopen. Als de consument een nieuwe wortelvergunning met een nieuwe vervaldatum downloadt, kunnen alle 50 stukken van inhoud worden gespeeld terug tot de bijgewerkte vergunning verloopt.

  Adobe Access 2.0 introduceerde een licentieketting waarin zowel de blad- als basislicenties aan een specifieke machine zijn gebonden. Toegang 3.0 van de Adobe introduceert een verbeterde vorm van vergunningsketting, waarin een blad aan een wortelvergunning wordt gebonden, en slechts is de wortelvergunning gebonden aan een specifiek machine of domein. Lezen *Enhanced License Chaining* in *De Adobe Access SDK gebruiken voor het beveiligen van inhoud*.

* **Rotatie sleutel:** Tijdens het gebruikelijke verpakken wordt de inhoud versleuteld met de Content Encryption Key (CEK) en krijgt de client een licentie met de CEK om de inhoud te kunnen gebruiken. Wanneer sleutelrotatie is ingeschakeld, kan de sleutel die wordt gebruikt om de inhoud te coderen, worden gewijzigd, zodat de sleutel alleen wordt gebruikt om een deel van de inhoud te coderen. Lezen *Toetsrotatie* in *De Adobe Access SDK gebruiken voor het beveiligen van inhoud*.

* **Out-of-band licenties:** Met de Toegang van de Adobe, is het mogelijk om een werkschema uit te voeren waarin de cliënten pre-geproduceerde vergunningen out-of-band verkrijgen, die de behoefte elimineren om een Server van de Vergunning op te stellen.
* **Domeinondersteuning:** Als alternatief voor het binden van een vergunning aan een specifiek apparaat, steunt de Toegang van de Adobe bindende vergunningen aan een domein. De veelvoudige apparaten kunnen zich bij een domein aansluiten en een domeinteken ontvangen dat vergunningen toestaat om tussen apparaten in het domein worden bewogen. Lezen *Domeinregistratie* in *De Adobe Access SDK gebruiken voor het beveiligen van inhoud*.

* **Gedeeltelijke codering:** Hiermee geeft u op of alle frames, of alleen een subset frames, moeten worden gecodeerd. Er zijn drie versleutelingsniveaus: laag, gemiddeld en hoog. Het verminderen van het encryptieniveau kan cpu overheadkosten op lagere eindmachines verminderen.
* **Verpakken van losgekoppelde inhoud:** Voor het verpakken van inhoud is geen netwerkverbinding met de licentieserver vereist. Dit maakt veilige back-endbewerkingen mogelijk door de blootstelling van gecomprimeerde inhoud die nog niet is beschermd, te beperken.
* **Controle over klokterugdraaiing: **De Toegang van de Adobe voorziet de veilige en nauwkeurige berekening van tijd om klokterugdraaiing op de cliëntcomputer te ontdekken. Dit handhaaft rechten met betrekking tot de toegang tot van inhoud voor een specifieke hoeveelheid tijd, en verhindert consumenten toegangsrechten te onderdrukken door de tijd op hun computer te veranderen.
* **Individualisatie**: Hiermee wordt het binden van inhoud aan een bepaalde computer toegestaan.
* **Lijst van gewenste personen toepassing:** Hiermee kan de clientruntime ervoor zorgen dat beveiligde inhoud alleen wordt afgespeeld binnen een geautoriseerde SWF- of AIR-toepassing.
* **Intrekking van gecompromitteerde cliënten: **De beloofde cliëntsoftware kan worden ingetrokken. Als wordt vastgesteld dat de Flash Player- of Adobe AIR-runtime in gevaar is gebracht, kan de service aan deze clients worden geweigerd totdat ze een upgrade uitvoeren naar een nieuwere en veiligere versie van de clientsoftware.
* **Meerdere beleidsregels voor hetzelfde videobestand: **Voor één stuk video-inhoud kunnen meerdere beleidsregels zijn ingesloten tijdens het maken van een pakket. Bij het uitgeven van een vergunning, kan de Server van de Vergunning beslissen welke van het beleid te gebruiken, toelatend een inhoudsverdeler om het zelfde beschermde dossier voor verschillende bedrijfsmodellen (zoals huur en elektronische doorverkoop) te gebruiken.
