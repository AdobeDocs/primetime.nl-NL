---
title: Belangrijkste kenmerken
description: Belangrijkste kenmerken
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '1147'
ht-degree: 0%

---


# Belangrijkste kenmerken{#key-features}

Adobe Primetime DRM biedt de volgende belangrijke functies:

* **Ondersteuning voor HLS-streaming (Adobe Primetime vereist):** gebruik Primetime DRM met HLS-inhoud die kan worden gestreamd naar elk platform dat door Flash of Adobe Primetime wordt ondersteund (zoals Desktop, iOS en Android).
* **Native iOS-toepassingsondersteuning (vereist Adobe Primetime):** gebruik Primetime DRM om video in uw iOS-toepassingen te beschermen.
* **Systeemeigen ondersteuning voor Android-toepassingen (Adobe Primetime vereist):** gebruik Primetime DRM om video te beschermen in uw Android-toepassingen.
* **Beveiligde streaming op Xbox (vereist Adobe Primetime)**.
* **Externe levering van iOS-sleutels (vereist Adobe Primetime):** Ondersteuning voor het leveren van externe iOS-sleutels via een sleutelserver met meerdere gebruikers, de Primetime DRM-sleutelserver genaamd.
* **Blijvende inhoudsbeveiliging:** inhoud blijft beveiligd in de hele distributieketen. Als de inhoud eenmaal is verpakt, blijft deze altijd beveiligd en worden delen ervan alleen op het moment van afspelen en in overeenstemming met de gebruiksregels gedecodeerd.
* Omdat de inhoud is verpakt met gebruiksregels en licentiegegevens, reist de beveiliging altijd met de inhoud. Als consumenten zonder licentie de inhoud proberen af te spelen, leidt het beleid dat in de inhoud is ingesloten hen om, zodat zij een geldige licentie voor de inhoud kunnen verkrijgen.
* **Beveiligd afspelen van beveiligde inhoud:** bewezen coderingsschema&#39;s worden gebruikt om inhoud te beschermen tegen ongeoorloofd afspelen.
* **Flexibele gebruiksregels:** gebruiksregels bepalen hoe consumenten beveiligde inhoud kunnen gebruiken. De gebruiksregels die door Primetime DRM worden ondersteund, staan verschillende bedrijfsmodellen toe, waaronder pay-per-view, filmverhuur, abonnementen of gecofinancierde services. De gebruiksregels worden gespecificeerd door het beleid u in de inhoud tijdens verpakking inbedt, of kunnen door de Server van de Vergunning tijdens vergunningsverwerving worden gespecificeerd.
* **Uitvoerbescherming:** Uitvoerbeveiligingselementen kunnen worden gebruikt voor beschermingssystemen zoals HDCP, CGMS-A of Rovi (voorheen Macrovision) ACS. Dit kan de uitvoer van inhoud via digitale (bijvoorbeeld HDMI, DVI en UDI) en analoge (bijvoorbeeld S-Video en Component Video) uitvoer helpen beschermen.

   U kunt uitvoerbeveiligingsopties opgeven in het beleid dat u voor uw inhoud maakt, zodat toegang tot inhoud wordt toegestaan of geweigerd op basis van de uitvoerbeveiligingsmogelijkheden van een apparaat. U kunt bijvoorbeeld opgeven dat uitvoerbeveiliging niet vereist is voor bepaalde inhoud, maar dat uitvoerbeveiliging vereist is voor hoogwaardige video-inhoud. Zo voorkomt u dat inhoud wordt uitgevoerd op besturingssystemen die deze mogelijkheid niet hebben.

   Hoewel deze regels op alle platforms consistent worden toegepast, is het momenteel alleen mogelijk om uitvoerbeveiliging op Windows-platforms veilig in te schakelen.

* **Ondersteuning voor dynamische streaming:** gebruik de functie voor dynamische streaming van Flash Media Server of Adobe HTTP Dynamic Streaming om inhoud die is gecodeerd, te beschermen tegen meerdere bitsnelheden. Dynamische streaming maakt gebruik van een videostream die de bitsnelheid en de afspeelkwaliteit dynamisch aanpast op basis van de beschikbare bandbreedte, waardoor de gebruiker een betere beleving krijgt. Met primetime DRM kunt u dezelfde inhoudscoderingssleutel en -licentie gebruiken voor de verschillende coderingen van hetzelfde element.
* **Offlineweergave:** de Adobe AIR-runtime client stelt consumenten in staat inhoud te downloaden en op te slaan voor weergave op een later tijdstip, ongeacht of de computer nog steeds verbonden is met internet.
* **Op identiteit gebaseerde licenties:** Koppelingen maken naar gebruikersidentiteiten, zodat consumenten zichzelf hoeven te verifiëren (met een gebruikersnaam en wachtwoord) om toegang te krijgen tot inhoud. Voor op identiteit gebaseerde licenties moet de partij die de clienttoepassing ontwikkelt gebruikersverificatie implementeren als onderdeel van de workflow voor het aanschaffen van licenties.
* **Licentieteketting:** Hiermee kunnen consumenten de levensduur van alle inhoud verlengen door één hoofdlicentie te vernieuwen. Een van de belangrijkste toepassingen van licentietekeningen is voor bedrijfsmodellen op basis van abonnementen, waarbij aan het einde van een abonnementsperiode licenties voor grote aantallen inhoudsbestanden kunnen worden vernieuwd door gewoon de hoofdlicentie te vernieuwen.

   Zowel basis- als bladlicenties zijn gebonden aan de computer van de consument. De bladlicentie bevat de CEK en een verwijzing naar de hoofdlicentie. De hoofdlicentie kan de rechten uitbreiden die in de bladlicentie zijn verleend. Een consument kan bijvoorbeeld bladlicenties hebben voor 50 stukken inhoud die aan het einde van een bepaalde abonnementsperiode verlopen. Als de consument een nieuwe wortelvergunning met een nieuwe vervaldatum downloadt, kunnen alle 50 stukken van inhoud worden gespeeld terug tot de bijgewerkte vergunning verloopt.

   Primetime DRM 2.0 introduceerde vergunningsketting waarin zowel de blad als wortelvergunningen aan een specifieke machine worden gebonden. Primetime DRM 3.0 introduceert een verbeterde vorm van vergunning die, waarin een blad aan een wortelvergunning wordt gebonden, wordt geketend en slechts de wortelvergunning is gebonden aan een specifieke machine of een domein. Lees *Enhanced License Chaining* in *De Adobe Primetime DRM SDK gebruiken voor het beschermen van inhoud*.

* **Sleutelrotatie:** Tijdens het typische verpakken wordt de inhoud versleuteld met de Content Encryption Key (CEK) en krijgt de client een licentie met de CEK om de inhoud te kunnen gebruiken. Wanneer sleutelrotatie is ingeschakeld, kan de sleutel die wordt gebruikt om de inhoud te coderen, worden gewijzigd, zodat de sleutel alleen wordt gebruikt om een deel van de inhoud te coderen. Lees *Key Rotation* in *De Adobe Primetime DRM SDK gebruiken voor het beschermen van inhoud*.

* **out-of-band licenties:** met Primetime DRM is het mogelijk om een workflow te implementeren waarin clients vooraf gegenereerde licenties offline verkrijgen, zodat een licentieserver niet hoeft te worden geïmplementeerd.
* **Domeinondersteuning:** Als alternatief voor het binden van een licentie aan een specifiek apparaat, ondersteunt Primetime DRM het binden van licenties aan een domein. De veelvoudige apparaten kunnen zich bij een domein aansluiten en een domeinteken ontvangen dat vergunningen toestaat om tussen apparaten in het domein worden bewogen. Lees *Domeinregistratie* in *De Adobe Primetime DRM SDK gebruiken voor het beschermen van inhoud*.

* **Gedeeltelijke codering:** geeft op of alle frames, of alleen een subset van frames, moeten worden gecodeerd. Er zijn drie niveaus van encryptie: laag, gemiddeld en hoog. Het verminderen van het encryptieniveau kan cpu overheadkosten op lagere eindmachines verminderen.
* **Inhoud loskoppelen:** Inhoud verpakken vereist geen netwerkverbinding met de licentieserver. Dit maakt veilige back-endbewerkingen mogelijk door de blootstelling van gecomprimeerde inhoud die nog niet is beschermd, te beperken.
* **Besturing over terugdraaien klok: **Primetime DRM verstrekt voor de veilige en nauwkeurige berekening van tijd om klokterugdraaiing op de cliëntcomputer te ontdekken. Dit handhaaft rechten met betrekking tot de toegang tot van inhoud voor een specifieke hoeveelheid tijd, en verhindert consumenten toegangsrechten te onderdrukken door de tijd op hun computer te veranderen.
* **Individualisatie**: Hiermee wordt het binden van inhoud aan een bepaalde computer toegestaan.
* **Application lijst van gewenste personen:** Hiermee kan de clientruntime ervoor zorgen dat beveiligde inhoud alleen wordt afgespeeld binnen een geautoriseerde SWF- of AIR-toepassing.
* **Intrekking van gecompromitteerde cliënten:De** Gecombineerde cliëntsoftware kan worden ingetrokken. Als wordt vastgesteld dat de Flash Player- of Adobe AIR-runtime gecompromitteerd is, kan de service aan deze clients worden geweigerd totdat ze een upgrade uitvoeren naar een nieuwere en veiligere versie van de clientsoftware.
* **Meerdere beleidsregels voor hetzelfde videobestand:** voor één stuk video-inhoud kunnen meerdere beleidsregels zijn ingesloten tijdens het verpakken. Bij het uitgeven van een vergunning, kan de Server van de Vergunning beslissen welke van het beleid te gebruiken, toelatend een inhoudsverdeler om het zelfde beschermde dossier voor verschillende bedrijfsmodellen (zoals huur en elektronische doorverkoop) te gebruiken.