---
seo-title: Adobe Access implementeren
title: Adobe Access implementeren
uuid: 9f9a9931-f607-4b1a-9209-0236a4c197ca
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# Adobe Access implementeren {#deploy-adobe-access}

Een belangrijk voordeel voor Adobe Access SDK is dat u deze kunt installeren op elke Java™-toepassingsserver of -servletcontainer, zoals Tomcat. U hebt ook JDK™ 1.5 of hoger nodig. Raadpleeg de vereisten voor het Adobe Access SDK-platform voor meer informatie over softwarevereisten: [: https://www.adobe.com/products/flashaccess/systemreqs/](https://www.adobe.com/products/flashaccess/systemreqs/).

De stappen op hoog niveau voor de implementatie van Adobe Access zijn:

1. Installeer en configureer de Adobe Access SDK.
1. Verkrijg digitale certificaten van Adobe.
1. Maak een licentieserver met de SDK of implementeer Adobe Access Server voor beveiligde streaming.
1. Maak pakketten van inhoud en beleidsbeheerprogramma&#39;s om inhoud te verpakken, gebruik de meegeleverde gereedschappen voor het voorbereiden van inhoud of maak een licentie voor een van de dynamische streaming pakketten van Adobe HTTP.
1. Bepaal gebruiksregels voor uw inhoud en creeer beleid ter ondersteuning van die regels.
1. Verpak uw inhoud met de tools voor verpakking en beleidsbeheer.
1. Ontwikkel videotoepassingen waarmee consumenten uw beveiligde inhoud kunnen bekijken met Flash Player of Adobe AIR, of gebruik een bestaande OVP (Online Video Platform) die Adobe Access ondersteunt.
1. Implementeer een SWF-bestand voor gebruik met Flash Player op uw website of post het installatieprogramma van Adobe AIR voor downloaden.

Deze stappen worden in de volgende secties uitgebreid, met verwijzingen naar andere documenten die extra informatie bevatten.

## Implementeren op een 64-bits besturingssysteem {#deploying-on-a-bit-operating-system}

Een 64-bits besturingssysteem, zoals de 64-bits versie van RedHat of Windows, biedt veel betere prestaties dan een 32-bits besturingssysteem.

## Adobe Access SDK installeren {#install-adobe-access-sdk}

De Adobe Access SDK wordt geleverd als een Java-archiefbestand (JAR). Zie Adobe Access SDK *gebruiken voor het beveiligen van inhoud* en de richtlijnen voor *veilige implementatie* voor meer informatie over het installeren van Adobe Access.

## Een licentieserver implementeren {#implement-a-license-server}

Als u Adobe Access SDK gebruikt, moet u een licentieserver maken. Als inhoud met Adobe Access is beveiligd, kan deze pas worden weergegeven als de licentieserver een licentie aan de consument heeft uitgegeven. Als licenties op basis van identiteit worden gebruikt, zorgt verificatie op basis van wachtwoord ervoor dat alleen geautoriseerde consumenten inhoud kunnen openen en bekijken.

Wanneer u een licentieserver implementeert, moet u de vereiste digitale certificaten verkrijgen van Adobe. Raadpleeg het Adobe Access-document voor certificaatinschrijving voor gedetailleerde instructies over het aanvragen van certificaten.

Zie* Adobe Access SDK gebruiken voor het beveiligen van inhoud voor meer informatie over het implementeren van een licentieserver en het verkrijgen van digitale certificaten.*

## Inhoud verpakken en beleidsbeheertools maken {#create-content-packaging-and-policy-management-tools}

Met de SDK van Adobe Access kunt u verpakken van inhoud en beleidsbeheergereedschappen maken. Met de API&#39;s voor beleidsbeheer kunnen beheerders beleidsregels maken, weergeven en bijwerken. De pakket-API&#39;s sluiten het beleid in het FLV- of F4V-bestand in en coderen het bestand met de coderingssleutel voor inhoud.

De SDK van Adobe Access bevat een referentie-implementatie ( [!DNL AdobePackager.jar]) die voorbeelden biedt van gereedschappen voor het verpakken van inhoud en beleidsbeheer ( [!DNL AdobePolicyManager.jar]).

Zie De SDK van Adobe Access *gebruiken voor het beveiligen van inhoud* voor meer informatie over het maken van pakketten voor inhoud en beleidsbeheergereedschappen.

## Beleid maken en inhoud verpakken {#create-policies-and-package-content}

Gebruikend de gebruiksregels die door SDK worden gesteund, moet u beleid ter ondersteuning van het bedrijfsmodel van uw organisatie bepalen en tot stand brengen, en dan uw inhoud verpakken gebruikend dat beleid. Zodra het beleid op inhoud tijdens verpakking wordt toegepast, kunt u controle van uw inhoud handhaven ongeacht hoe wijd het wordt verdeeld.

Het beleid in Adobe Access biedt ondersteuning voor een groot aantal verschillende gebruiksregels, waaronder:

* Het aantal dagen dat een licentie geldig is wanneer een consument de inhoud begint te bekijken.
* Licentie in cache plaatsen toegestaan.
* Clientruntimes en -versies opgeven die toegang kunnen krijgen tot inhoud (gebruikers moeten bijvoorbeeld over een bepaalde Adobe AIR-toepassing of een specifieke versie van Flash Player beschikken).
* Vereisen dat consumenten zichzelf verifiëren met een gebruikersnaam en wachtwoord voordat ze beveiligde inhoud bekijken of anonieme toegang toestaan.

Zie Inhoud *beveiligen* voor meer informatie over het verpakken van inhoud. Zie *Gebruiksregels* voor meer informatie over de gebruiksregels en de bedrijfsmodellen die ze ondersteunen.

## Toepassingen ontwikkelen voor het afspelen van video {#develop-applications-for-video-playback}

Als u consumenten toegang wilt geven tot inhoud en deze wilt weergeven, ontwikkelt u een videoafspeeltoepassing met Flash Player of Adobe AIR. Nadat u een videoafspeeltoepassing hebt ontwikkeld, moet u deze implementeren voor consumenten. Als u een toepassing ontwikkelt met Flash Player, host u deze op de website van uw organisatie. Als u een toepassing ontwikkelt met Adobe® AIR®, plaatst u het installatieprogramma van de AIR-toepassing zodat consumenten de toepassing kunnen downloaden en installeren op hun computer.

Zie het hoofdstuk &quot;Werken met video&quot; in de ActionScript 3.0-ontwikkelaarsgids [*, het Adobe Video Technology Center](https://help.adobe.com/en_US/as3/dev/WS9936fa0d5984e93b3f4f38ec1272a447844-8000.html)[](https://www.adobe.com/devnet/video/)en het Open Source Media Framework voor meer informatie over het ontwikkelen van aangepaste toepassingen voor het afspelen van video&#39;s voor gebruik met Adobe Access.