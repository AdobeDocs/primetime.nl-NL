---
seo-title: Belangrijkste kenmerken
title: Belangrijkste kenmerken
uuid: b1bded0f-4e45-4ff8-a7ce-dac3d3ec0ab0
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Belangrijkste kenmerken {#key-features}

Adobe Access biedt de volgende belangrijke functies:

* **Ondersteuning voor HLS-streaming (Adobe Primetime vereist):** Gebruik Adobe Access DRM met HLS-inhoud die kan worden gestreamd naar elk platform dat door Flash of Adobe Primetime wordt ondersteund (zoals Desktop, iOS en Android).
* **Systeemeigen iOS-toepassingsondersteuning (vereist Adobe Primetime):** Gebruik Adobe Access DRM om video in uw iOS-toepassingen te beveiligen.
* **Systeemeigen ondersteuning voor Android-toepassingen (Adobe Primetime vereist):** Gebruik Adobe Access DRM om video in uw Android-toepassingen te beveiligen.
* **Beveiligde streaming op Xbox (vereist Adobe Primetime)**.
* **Externe levering van iOS-sleutels (vereist Adobe Primetime):** Ondersteuning voor het leveren van externe iOS-sleutels via een sleutelserver met meerdere gebruikers, de zogenaamde Adobe Access Key Server.
* **Beveiliging van permanente inhoud:** De inhoud blijft in de hele distributieketen beschermd. Als de inhoud eenmaal is verpakt, blijft deze altijd beveiligd en worden delen ervan alleen op het moment van afspelen en in overeenstemming met de gebruiksregels gedecodeerd.
* Omdat de inhoud is verpakt met gebruiksregels en licentiegegevens, reist de beveiliging altijd met de inhoud. Als consumenten zonder licentie de inhoud proberen af te spelen, leidt het beleid dat in de inhoud is ingesloten hen om, zodat zij een geldige licentie voor de inhoud kunnen verkrijgen.
* **Beveiligd afspelen van beveiligde inhoud: **Bewezen versleutelingsschema&#39;s worden gebruikt om inhoud te beschermen tegen ongeoorloofd afspelen.
* **Flexibele gebruiksregels:** Gebruiksregels bepalen hoe consumenten beveiligde inhoud kunnen gebruiken. De gebruiksregels die worden ondersteund door Adobe Access, staan verschillende bedrijfsmodellen toe, zoals pay-per-view, filmverhuur, abonnementen of services met ad-funding. De gebruiksregels worden gespecificeerd door het beleid u in de inhoud tijdens verpakking inbedt, of kunnen door de Server van de Vergunning tijdens vergunningsverwerving worden gespecificeerd.
* **Uitvoerbeveiliging:** Uitvoerbeveiligingscontroles kunnen worden gebruikt om beschermingsregelingen aan te gaan zoals HDCP, CGMS-A of Rovi (voorheen Macrovision) ACS. Dit kan de uitvoer van inhoud via digitale (bijvoorbeeld HDMI, DVI en UDI) en analoge (bijvoorbeeld S-Video en Component Video) uitvoer helpen beschermen.

   U kunt uitvoerbeveiligingsopties opgeven in het beleid dat u voor uw inhoud maakt, zodat toegang tot inhoud wordt toegestaan of geweigerd op basis van de uitvoerbeveiligingsmogelijkheden van een apparaat. U kunt bijvoorbeeld opgeven dat uitvoerbeveiliging niet vereist is voor bepaalde inhoud, maar dat uitvoerbeveiliging vereist is voor hoogwaardige video-inhoud. Zo voorkomt u dat inhoud wordt uitgevoerd op besturingssystemen die deze mogelijkheid niet hebben.

   Hoewel deze regels op alle platforms consistent worden toegepast, is het momenteel alleen mogelijk om uitvoerbeveiliging op Windows-platforms veilig in te schakelen.

* **Ondersteuning voor dynamische streaming: **Gebruik de functie voor dynamisch streamen van Flash Media Server of Adobe HTTP Dynamic Streaming om inhoud die is gecodeerd, te beschermen tegen meerdere bitsnelheden. Dynamische streaming maakt gebruik van een videostream die de bitsnelheid en de afspeelkwaliteit dynamisch aanpast op basis van de beschikbare bandbreedte, waardoor de gebruiker een betere beleving krijgt. Met Adobe Access kunt u dezelfde coderingssleutel en licentie voor inhoud gebruiken voor de verschillende coderingen van hetzelfde element.
* **Offlineweergave:** Met de Adobe AIR-runtime-client kunnen consumenten inhoud downloaden en opslaan voor weergave op een later tijdstip, ongeacht of de computer nog steeds met internet is verbonden.
* **Licenties op basis van identiteit:** Koppelt machtigingen aan gebruikersidentiteiten, waarbij de consument zichzelf moet verifiëren (met een gebruikersnaam en wachtwoord) om toegang te krijgen tot inhoud. Voor op identiteit gebaseerde licenties moet de partij die de clienttoepassing ontwikkelt gebruikersverificatie implementeren als onderdeel van de workflow voor het aanschaffen van licenties.
* **Licentieketting:** Hiermee kunnen consumenten de levensduur van al hun inhoud verlengen door een enkele basislicentie te vernieuwen. Een van de belangrijkste toepassingen van licentietekeningen is voor bedrijfsmodellen op basis van abonnementen, waarbij aan het einde van een abonnementsperiode licenties voor grote aantallen inhoudsbestanden kunnen worden vernieuwd door gewoon de hoofdlicentie te vernieuwen.

   Zowel basis- als bladlicenties zijn gebonden aan de computer van de consument. De bladlicentie bevat de CEK en een verwijzing naar de hoofdlicentie. De hoofdlicentie kan de rechten uitbreiden die in de bladlicentie zijn verleend. Een consument kan bijvoorbeeld bladlicenties hebben voor 50 stukken inhoud die aan het einde van een bepaalde abonnementsperiode verlopen. Als de consument een nieuwe wortelvergunning met een nieuwe vervaldatum downloadt, kunnen alle 50 stukken van inhoud worden gespeeld terug tot de bijgewerkte vergunning verloopt.

   Adobe Access 2.0 heeft een licentietekening geïntroduceerd waarin zowel de blad- als basislicenties zijn gebonden aan een specifieke computer. Adobe Access 3.0 introduceert een verbeterde vorm van licentietekeningen, waarbij een blad is gebonden aan een hoofdlicentie en alleen de hoofdlicentie is gebonden aan een specifieke computer of een specifiek domein. Lees *Enhanced License Chaining* in *Using the Adobe Access SDK for Protecting Content*.

* **Rotatie sleutel:** Tijdens het gebruikelijke verpakken wordt de inhoud versleuteld met de Content Encryption Key (CEK) en krijgt de client een licentie met de CEK om de inhoud te kunnen gebruiken. Wanneer sleutelrotatie is ingeschakeld, kan de sleutel die wordt gebruikt om de inhoud te coderen, worden gewijzigd, zodat de sleutel alleen wordt gebruikt om een deel van de inhoud te coderen. De *Sleutelrotatie* lezen in de SDK van Adobe Access *gebruiken voor het beschermen van inhoud*.

* **Out-of-band licenties:** Met Adobe Access is het mogelijk een workflow te implementeren waarin clients vooraf gegenereerde licenties offline verkrijgen, zodat een licentieserver niet hoeft te worden geïmplementeerd.
* **Domeinondersteuning:** Als alternatief voor het binden van een licentie aan een specifiek apparaat, ondersteunt Adobe Access het binden van licenties aan een domein. De veelvoudige apparaten kunnen zich bij een domein aansluiten en een domeinteken ontvangen dat vergunningen toestaat om tussen apparaten in het domein worden bewogen. Lees *Domeinregistratie* in de SDK van Adobe Access *gebruiken voor het beveiligen van inhoud*.

* **Gedeeltelijke codering:** Hiermee geeft u op of alle frames, of alleen een subset frames, moeten worden gecodeerd. Er zijn drie niveaus van encryptie: laag, gemiddeld en hoog. Het verminderen van het encryptieniveau kan cpu overheadkosten op lagere eindmachines verminderen.
* **Verpakken van losgekoppelde inhoud:** Voor het verpakken van inhoud is geen netwerkverbinding met de licentieserver vereist. Dit maakt veilige back-endbewerkingen mogelijk door de blootstelling van gecomprimeerde inhoud die nog niet is beschermd, te beperken.
* **Besturing over terugdraaien klok: **Adobe Access biedt een veilige en nauwkeurige berekening van de tijd die nodig is om de terugdraaitijd van de klok op de clientcomputer te detecteren. Dit handhaaft rechten met betrekking tot de toegang tot van inhoud voor een specifieke hoeveelheid tijd, en verhindert consumenten toegangsrechten te onderdrukken door de tijd op hun computer te veranderen.
* **Individualisatie**: Hiermee wordt het binden van inhoud aan een bepaalde computer toegestaan.
* **whitelist van toepassing:** Hiermee kan de clientruntime ervoor zorgen dat beveiligde inhoud alleen wordt afgespeeld binnen een geautoriseerde SWF- of AIR-toepassing.
* **Intrekking van gecompromitteerde cliënten: **Gecomprimeerde clientsoftware kan worden ingetrokken. Als wordt vastgesteld dat de Flash Player- of Adobe AIR-runtime in gevaar is gebracht, kan de service aan deze clients worden geweigerd totdat ze een upgrade uitvoeren naar een nieuwere en veiligere versie van de clientsoftware.
* **Meerdere beleidsregels voor hetzelfde videobestand: **Voor één stuk video-inhoud kunnen meerdere beleidsregels zijn ingesloten tijdens het verpakken. Bij het uitgeven van een vergunning, kan de Server van de Vergunning beslissen welke van het beleid te gebruiken, toelatend een inhoudsverdeler om het zelfde beschermde dossier voor verschillende bedrijfsmodellen (zoals huur en elektronische doorverkoop) te gebruiken.

