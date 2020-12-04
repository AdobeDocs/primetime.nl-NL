---
seo-title: Toegang tot Adobe implementeren
title: Toegang tot Adobe implementeren
uuid: 9f9a9931-f607-4b1a-9209-0236a4c197ca
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 0%

---


# Adobe-toegang {#deploy-adobe-access} implementeren

Een belangrijk voordeel voor Adobe Access SDK is dat u deze kunt installeren op elke Java™-toepassingsserver of -servletcontainer, zoals Tomcat. U hebt ook JDK™ 1.5 of hoger nodig. Voor meer informatie over softwarevereisten, zie Adobe Access SDK platformvereisten: [: https://www.adobe.com/products/flashaccess/systemreqs/](https://www.adobe.com/products/flashaccess/systemreqs/).

De stappen op hoog niveau om de Toegang van Adobe op te stellen zijn:

1. Installeer en vorm Adobe Access SDK.
1. Digitale certificaten verkrijgen van Adobe.
1. Maak een licentieserver met de SDK of implementeer Adobe Access Server voor beveiligde streaming.
1. Maak inhoud verpakken en beleidsbeheertools om inhoud te verpakken, gebruik de meegeleverde gereedschappen voor het voorbereiden van inhoud of geef een licentie voor een van de Adobe HTTP Dynamic Streaming-pakketten.
1. Bepaal gebruiksregels voor uw inhoud en creeer beleid ter ondersteuning van die regels.
1. Verpak uw inhoud met de tools voor verpakking en beleidsbeheer.
1. Ontwikkel videotoepassingen waarmee consumenten uw beschermde inhoud kunnen bekijken gebruikend Flash Player of Adobe AIR, of gebruik een gevestigde OVP (Online Video Platform) die Adobe toegang steunt.
1. Implementeer een SWF-bestand voor gebruik met Flash Player op uw website of post het Adobe AIR-installatieprogramma voor downloaden.

Deze stappen worden in de volgende secties uitgebreid, met verwijzingen naar andere documenten die extra informatie bevatten.

## Implementeren op een 64-bits besturingssysteem {#deploying-on-a-bit-operating-system}

Een 64-bits besturingssysteem, zoals de 64-bits versie van RedHat of Windows, biedt veel betere prestaties dan een 32-bits besturingssysteem.

## SDK voor Adobe Access installeren {#install-adobe-access-sdk}

Adobe Access SDK wordt geleverd als een Java-archiefbestand (JAR). Voor meer informatie over het installeren van Adobe Access, zie *Gebruikend Adobe Access SDK voor het Beschermen van Inhoud* en *Veilige Richtlijnen van de Plaatsing*.

## Een licentieserver {#implement-a-license-server} implementeren

Gebruikend Adobe Access SDK, moet u een Server van de Vergunning tot stand brengen. Wanneer inhoud wordt beschermd met behulp van Adobe Access, kan deze pas worden weergegeven als de licentieserver een licentie heeft afgegeven aan de consument. Als licenties op basis van identiteit worden gebruikt, zorgt verificatie op basis van wachtwoord ervoor dat alleen geautoriseerde consumenten inhoud kunnen openen en bekijken.

Wanneer u een licentieserver implementeert, moet u de benodigde digitale certificaten verkrijgen van Adobe. Raadpleeg het document Adobe Access Certificate Enrollment voor gedetailleerde instructies over het aanvragen van-certificaten.

Meer over het uitvoeren van een Server van de Vergunning, en het verkrijgen van digitale certificaten, zie* Gebruikend Adobe Toegang SDK voor het Beschermen van Inhoud.*

## Inhoud verpakken en beleidsbeheertools maken {#create-content-packaging-and-policy-management-tools}

Met de SDK van Adobe Access kunt u verpakken van inhoud en beleidsbeheertools maken. Met de API&#39;s voor beleidsbeheer kunnen beheerders beleidsregels maken, weergeven en bijwerken. De pakket-API&#39;s sluiten het beleid in het FLV- of F4V-bestand in en coderen het bestand met de coderingssleutel voor inhoud.

De Adobe Access SDK bevat een referentie-implementatie ( [!DNL AdobePackager.jar]) met voorbeelden van inhoudopmaak en beleidsbeheertools ( [!DNL AdobePolicyManager.jar]).

Voor meer over het creëren van inhoud verpakken en beleidsbeheersinstrumenten, zie *Gebruikend de SDK van de Toegang van de Adobe voor het Beschermen van Inhoud*.

## Beleid maken en inhoud verpakken {#create-policies-and-package-content}

Gebruikend de gebruiksregels die door SDK worden gesteund, moet u beleid ter ondersteuning van het bedrijfsmodel van uw organisatie bepalen en tot stand brengen, en dan uw inhoud verpakken gebruikend dat beleid. Zodra het beleid op inhoud tijdens verpakking wordt toegepast, kunt u controle van uw inhoud handhaven ongeacht hoe wijd het wordt verdeeld.

Het beleid in de Toegang van Adobe steunt een brede waaier van verschillende gebruiksregels, die omvatten:

* Het aantal dagen dat een licentie geldig is wanneer een consument de inhoud begint te bekijken.
* Licentie in cache plaatsen toegestaan.
* Clientruntimes en -versies opgeven die toegang kunnen krijgen tot inhoud (gebruikers moeten bijvoorbeeld een bepaalde Adobe AIR-toepassing of een specifieke versie van Flash Player hebben).
* Vereisen dat consumenten zichzelf verifiëren met een gebruikersnaam en wachtwoord voordat ze beveiligde inhoud bekijken of anonieme toegang toestaan.

Zie *Inhoud beveiligen* voor meer informatie over het verpakken van inhoud. Voor meer informatie over de gebruiksregels en de bedrijfsmodellen die zij steunen, zie *Gebruiksregels*.

## Toepassingen ontwikkelen voor het afspelen van video {#develop-applications-for-video-playback}

Als u consumenten toegang wilt geven tot inhoud en deze wilt bekijken, ontwikkelt u een videoafspeeltoepassing met Flash Player of Adobe AIR. Nadat u een videoafspeeltoepassing hebt ontwikkeld, moet u deze implementeren voor consumenten. Als u een toepassing ontwikkelt met behulp van Flash Player, host u deze op de website van uw organisatie. Als u een toepassing ontwikkelt met Adobe® AIR®, plaatst u het installatieprogramma van de AIR-toepassing, zodat consumenten de toepassing kunnen downloaden en installeren op hun computer.

Meer over het ontwikkelen van de toepassingen van de douanevideo playback voor gebruik met Adobe Access, zie het &quot;Werken met Video&quot;hoofdstuk in [ActionScript 3.0 de Gids van de Ontwikkelaar](https://help.adobe.com/en_US/as3/dev/WS9936fa0d5984e93b3f4f38ec1272a447844-8000.html)*, *het [Adobe VideoCentrum](https://www.adobe.com/devnet/video/), en het Open Source Media Framework.