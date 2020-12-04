---
seo-title: Adobe Primetime DRM implementeren
title: Adobe Primetime DRM implementeren
uuid: c14c2792-d207-4f39-b856-610520bdaa28
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 0%

---


# Adobe Primetime DRM {#configure-adobe-primetime-drm} implementeren

Een belangrijk voordeel voor Adobe Primetime DRM SDK is dat u deze kunt installeren op elke Java™-toepassingsserver of -servletcontainer, zoals Tomcat. U hebt ook JDK™ 1.5 of hoger nodig. Raadpleeg de vereisten voor het Primetime DRM SDK-platform voor meer informatie over softwarevereisten: [https://www.adobe.com/products/flashaccess/systemreqs/](https://www.adobe.com/products/flashaccess/systemreqs/).

De stappen op hoog niveau om Primetime DRM te implementeren zijn:

1. Installeer en configureer Primetime DRM SDK.
1. Digitale certificaten verkrijgen van Adobe.
1. Maak een licentieserver met de SDK of implementeer Primetime DRM Server voor beveiligde streaming.
1. Maak inhoud verpakken en beleidsbeheertools om inhoud te verpakken, gebruik de meegeleverde gereedschappen voor het voorbereiden van inhoud of geef een licentie voor een van de Adobe HTTP Dynamic Streaming-pakketten.
1. Bepaal gebruiksregels voor uw inhoud en creeer beleid ter ondersteuning van die regels.
1. Verpak uw inhoud met de tools voor verpakking en beleidsbeheer.
1. Ontwikkel videotoepassingen waarmee consumenten uw beschermde inhoud kunnen bekijken gebruikend Flash Player of Adobe AIR, of gebruik een gevestigde OVP (Online Video Platform) die Primetime DRM steunt.
1. Implementeer een SWF-bestand voor gebruik met Flash Player op uw website of post het Adobe AIR-installatieprogramma voor downloaden.

Deze stappen worden in de volgende secties uitgebreid, met verwijzingen naar andere documenten die extra informatie bevatten.

## Implementeren op een 64-bits besturingssysteem{#deploying-on-a-bit-operating-system}

Een 64-bits besturingssysteem, zoals de 64-bits versie van RedHat of Windows, biedt veel betere prestaties dan een 32-bits besturingssysteem.

## Adobe Primetime DRM SDK {#install-adobe-primetime-drm-sdk} installeren

Primetime DRM SDK wordt geleverd als een JAR-bestand (Java archive). Zie Adobe Primetime DRM SDK gebruiken voor het beschermen van inhoud en het beveiligen van implementatierichtlijnen voor meer informatie over het installeren van Primetime DRM.

## Een licentieserver {#implement-a-license-server} implementeren

Met Adobe Primetime DRM SDK moet u een licentieserver maken. Wanneer inhoud wordt beveiligd met Primetime DRM, kan deze pas worden weergegeven als de licentieserver een licentie heeft afgegeven aan de consument. Als licenties op basis van identiteit worden gebruikt, zorgt verificatie op basis van wachtwoord ervoor dat alleen geautoriseerde consumenten inhoud kunnen openen en bekijken.

Wanneer u een licentieserver implementeert, moet u de benodigde digitale certificaten verkrijgen van Adobe. Raadpleeg het document voor primetime DRM-certificaatinschrijving voor gedetailleerde instructies over het aanvragen van certificaten.

Zie **Adobe Primetime DRM SDK gebruiken voor het beschermen van inhoud voor meer informatie over het implementeren van een licentieserver en het verkrijgen van digitale certificaten.**

## Inhoud verpakken en beleidsbeheertools maken{#create-content-packaging-and-policy-management-tools}

Met de Adobe Primetime DRM SDK kunt u verpakken van inhoud en beleidsbeheertools maken. Met de API&#39;s voor beleidsbeheer kunnen beheerders beleidsregels maken, weergeven en bijwerken. De pakket-API&#39;s sluiten het beleid in het videobestand in en coderen het bestand met de coderingssleutel voor inhoud.

De Primetime DRM SDK bevat een referentie-implementatie ( [!DNL AdobePackager.jar]) die voorbeelden biedt van gereedschappen voor het verpakken van inhoud en beleidsbeheer ( [!DNL AdobePolicyManager.jar]).

Zie **De Adobe Primetime DRM SDK gebruiken voor het beschermen van inhoud voor meer informatie over het maken van inhoudspakketten en beleidsbeheertools.**

## Beleid maken en inhoud verpakken {#create-policies-and-package-content}

Gebruikend de gebruiksregels die door SDK worden gesteund, moet u beleid ter ondersteuning van het bedrijfsmodel van uw organisatie bepalen en tot stand brengen, en dan uw inhoud verpakken gebruikend dat beleid. Zodra het beleid op inhoud tijdens verpakking wordt toegepast, kunt u controle van uw inhoud handhaven ongeacht hoe wijd het wordt verdeeld.

Het beleid in Adobe Primetime DRM ondersteunt een groot aantal verschillende gebruiksregels, waaronder:

* Het aantal dagen dat een licentie geldig is wanneer een consument de inhoud begint te bekijken.
* Licentie in cache plaatsen toegestaan.
* Clientruntimes en -versies opgeven die toegang kunnen krijgen tot inhoud (gebruikers moeten bijvoorbeeld een bepaalde Adobe AIR-toepassing of een specifieke versie van Flash Player hebben).
* Vereisen dat consumenten zichzelf verifiëren met een gebruikersnaam en wachtwoord voordat ze beveiligde inhoud bekijken of anonieme toegang toestaan.

Zie *Inhoud beveiligen* voor meer informatie over het verpakken van inhoud. Voor meer informatie over de gebruiksregels en de bedrijfsmodellen die zij steunen, zie *Gebruiksregels*.

## Toepassingen ontwikkelen voor het afspelen van video {#develop-applications-for-video-playback}

Als u consumenten toegang wilt geven tot inhoud en deze wilt bekijken, ontwikkelt u een videoafspeeltoepassing met Flash Player of Adobe AIR. Nadat u een videoafspeeltoepassing hebt ontwikkeld, moet u deze implementeren voor consumenten. Als u een toepassing ontwikkelt met behulp van Flash Player, host u deze op de website van uw organisatie. Als u een toepassing ontwikkelt met Adobe® AIR®, plaatst u het installatieprogramma van de AIR-toepassing, zodat consumenten de toepassing kunnen downloaden en installeren op hun computer.

Zie het hoofdstuk &quot;Werken met video&quot; in [ActionScript Adobe Primetime 3.0-ontwikkelaarsgids](https://help.adobe.com/en_US/as3/dev/WS9936fa0d5984e93b3f4f38ec1272a447844-8000.html), het [Adobe Video Technology Center](https://www.adobe.com/devnet/video/) en het Open Source Media Framework voor meer informatie over het ontwikkelen van aangepaste videoafspeeltoepassingen voor gebruik met DRM.